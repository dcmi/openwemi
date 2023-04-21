# openwemi

The concepts first introduced in the FRBR document and known as “WEMI” (Work, Expression, Manifestation, Item) have been employed in situations quite different from the library bibliographic catalog. (More in this [article](https://journal.code4lib.org/articles/16491) and see the [bibliography](bibliography.md)). This is evidence that a definition of similar classes that are more general than those developed for library usage would benefit metadata developers broadly. This DCMI work product proposes a minimally constrained set of classes and relationships that could form the basis for a useful model of created works that defines WEMI as RDF classes with few constraints. These classes can be used together or separately in metadata to characterize aspects of creations. 

openWEMI classes are purposely defined very broadly. Experience shows that metadata models are likely to use openWEMI classes as superclasses to the more specific materials being described. 

## The proposal

This is work to create a non-constrained version of FRBR's Work, Expression, Manifestation, Item. In particular it removes any disjoint rules between the WEMI entities. It is based on the [FRBR Core](http://purl.org/vocab/frbr/core) created by Ian Davis and Richard Newman, with contributions by Bruce D'Arcus. 

The minimal WEMI set has these classes and subclasses:
* Endeavor
  * Work
  * Expression
  * Manifestation
  * Item
* ResponsibleEntity

It has these properties which define the primary relationships between WEMI:
  * expresses (range: Work or Expression)
  * manifests (range: Work or Expression or Manifestation)
  * instantiates (range: Work or Expression or Manifestation or Item)
Which is expressed in this diagram:
![openRels2](https://user-images.githubusercontent.com/1564129/231845216-bc842bb0-de35-4778-8066-32947af26781.jpg)


This proposal does not include the FRBR Group2 or Group3 entities (responsible bodies and subjects). It does include the superclass Endeavor, which is not part of the FRBR group of entities but was added by the authors of FRBR core. 

