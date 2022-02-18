## gfe-service
gfe-service is the public REST interface to the GFE system

![](https://github.com/nmdp-bioinformatics/GFE/blob/495a3688f2e7f7dba2d44ffb27411b454740bed6/images/9EDD2D37-C36E-4619-A4F2-9D0F1413BE7E.jpeg)

The [py-gfe](https://github.com/nmdp-bioinformatics/py-gfe) module performs all of the underlying actions either directly against the [gfe-db](https://github.com/nmdp-bioinformatics/gfe-db) (Neo4j) or via the [seq-ann](https://github.com/nmdp-bioinformatics/seq-ann) module.  The seq-ann module uses feature-service for cloud storage of individual features and BioSQL for sequence analysis.


# REST endpoint

Live at [http://gfe.b12x.org/ui](http://gfe.b12x.org/ui)

## Swagger interface as of 2021-04-01

![swagger](https://github.com/nmdp-bioinformatics/GFE/blob/ce1376a063bcde48dac102e50f0b19c0ee0eb224/images/Screen%20Shot%202021-04-01%20at%2010.04.28.png)
