## gfe-service
gfe-service is the public REST interface to the GFE system

![gfe-graphic](../img/9EDD2D37-C36E-4619-A4F2-9D0F1413BE7E.jpeg)

The [py-gfe](https://github.com/nmdp-bioinformatics/py-gfe) module performs all of the underlying actions either directly against the [gfe-db](https://github.com/nmdp-bioinformatics/gfe-db) (Neo4j) or via the [seq-ann](https://github.com/nmdp-bioinformatics/seq-ann) module.  The seq-ann module uses feature-service for cloud storage of individual features and BioSQL for sequence analysis.


# REST endpoint

Live at [http://gfe.b12x.org/ui](http://gfe.b12x.org/ui)

## Swagger interface as of 2021-04-01

![swagger](../img/swagger.png)
