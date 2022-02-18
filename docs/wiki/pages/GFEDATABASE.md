## GFE Database


The GFE database has a new schema that more clearly centralizes the GFE node and makes the IMGT_HLA curation and IMGT_HLA database versioning as optional annotation of GFEs.

![schema](https://github.com/nmdp-bioinformatics/GFE/blob/0fb719a84db802e93ad347906a76223a44d1ea3e/images/45D8F9B2-DC6C-4EAD-BCAE-5DD1B20F8079.jpeg)

### Nodes 
**GFE** - Each node represents a distinct GFE object.  For example, a GFE with gfe_name="HLA-Aw2-1-1-1-1-4-1-1-1-2-1-1-1-1-1-1-4" corresponds to a  full sequence and also 17 features (FIVE_PRIME_UTR, EXON (1-8), INTRON (1-7), THREE_PRIME_UTR)

**GenomicAlignment** - Genomic alignment of the genomic sequence corresponding to the GFE (deprecated)

**NucleotideAlignment** - Nucleoside alignment of the CDS nucleotide sequence corresponding to the GFE (deprecated)

**ProteinAlignment** - Protein alignment of the amino acid sequences (deprecated)

**IMGT_HLA** - The name in the IPD/IMGT-HLA database

**CDS** - CoDing sequence (deprecated)

**Sequence** - The nucleotide sequence corresponding to the GFE

**Feature** - A feature is a tuple of: locus, term, rank and sequence.  locus is "anything in [HUGO](https://www.genenames.org/)", term is "anything in [http://www.sequenceontology.org/](sequence ontology)" 

**G** - Big G group

**lg** - Little g group with "g" character

**lgx** - Little g group without "g" (clinical use)


***

### Edges

**HAS_FEATURE** - links a GFE to a FEATURE

**HAS_CDS** - links a sequence to its CoDing sequence (CDS) 

**HAS_SEQUENCE** - links a GFE to the full sequence 

**HAS_ALIGNMENT** - deprecated

**G**

**HAS_GFE**

**lg**

**lgx**


***

## Breaking down a GFE

The representation of a single GFE, for example corresponding to the allele `HLA-A*01:03:01:01` can be understood from the graph 

![GFE query](https://github.com/nmdp-bioinformatics/GFE/blob/225e9c4be40f0bd3f16044502efa8a00841cb2c9/images/Neo4j%20Browser.png)

The IMGT_HLA node points to a GFE as one of possibly many annotations.
With this schema it is possible to analyze GFEs that do not have an IMGT_HLA referring to it.

To see the how a GFE expands to its constituent components, this query 
```MATCH (i:IMGT_HLA {name:'HLA-A*01:03:01:01'})-[]-(:GFE)-[]-(f:Feature) return f.term, f.rank order by f.term, f.rank``` 
 returns the corresponding features associated with the GFE referred to by the IMGT_HLA allele `HLA-A*01:03:01:01`.

![query result](https://github.com/nmdp-bioinformatics/GFE/blob/67386c0c060a85a6d275bcaa036d9132cc61d671/images/0E9C47FE-AD95-4B23-8A7A-EC8DFF271127.jpeg)

These features each have an accession number that is unique in the context of the (locus, term and rank) combination and is a **permanent reversible 1-to-1 mapping** between the sequence and the accession number in that context.

This is important because the mapping between IMGT_HLA names and sequences is not permanent/reversible/1-to-1.  Nor is the mapping between IMGT_HLA names and IMGT accession numbers permanent/reversible/1-to-1.  Nor is the mapping between IMGT accession numbers and sequence permanent/reversible/1-to-1.

Here is a simple example of a relationship between and IMGT_HLA allele (`HLA-DRB1*11:17`) and the corresponding GFE.

![GFE example](https://github.com/nmdp-bioinformatics/GFE/blob/225e9c4be40f0bd3f16044502efa8a00841cb2c9/images/157B500B-9399-4B46-9E48-628F72C869C0.jpeg)

In this example, the GFE associated with this allele changed between 3.42.0 and 3.43.0 

