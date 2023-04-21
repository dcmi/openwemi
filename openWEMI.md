# openwemi

The concepts first introduced in the FRBR document and known as “WEMI” (Work, Expression, Manifestation, Item) have been employed in situations quite different from the library bibliographic catalog. (More in this [article](https://journal.code4lib.org/articles/16491) and see the [bibliography](bibliography.md)). This is evidence that a definition of similar classes that are more general than those developed for library usage would benefit metadata developers broadly. This DCMI work product proposes a minimally constrained set of classes and relationships that could form the basis for a useful model of created works that defines WEMI as RDF classes with few constraints. These classes can be used together or separately in metadata to characterize aspects of creations. 

openWEMI classes are purposely defined very broadly. Experience shows that metadata models are likely to use openWEMI classes as superclasses to the more specific materials being described. The proposal includes the superclass Endeavor, which is not part of the FRBR group of entities but was added by the authors of FRBR core and is deemed to be needed to create a coherent grouping of the entities. It also would be useful should any new high-order entities be added in the future. 

## The proposal

This is work to create a non-constrained version of FRBR's Work, Expression, Manifestation, Item. In particular it removes any disjoint rules between the WEMI entities and removes any reference to bibliographic entities from their definitions. It is loosely based on the [FRBR Core](http://purl.org/vocab/frbr/core) created by Ian Davis and Richard Newman, with contributions by Bruce D'Arcus. 
### Classes
The minimal WEMI set has these classes and subclasses:
* Endeavor
  * Work
  * Expression
  * Manifestation
  * Item
* ResponsibleEntity
These are defined as:
* Endeavor: "A creation"
* Work: "An abstract notion of an artistic or intellectual creation."
* Expression: "A perceivable form of the creation"
* Manifestation: "The physical embodiment of a creation"
* Item: "An exemplar of a creation."
* ResponsibleEntity: "An agent with some responsibility related to a creation."
### Relationship properties
It has these properties which define the primary relationships between WEMI:
  * expresses (range: Work or Expression)
  * manifests (range: Work or Expression or Manifestation)
  * instantiates (range: Work or Expression or Manifestation or Item)
Which is expressed in this diagram:
![openRels1](https://user-images.githubusercontent.com/1564129/233729616-fa92d8c1-322a-4b6d-9ec9-ad532a209f6d.jpg)

The relationship properties are as open as possible while still maintaining the logical progression between the most general concept of the work to the item. Where these relationships in FRBR and in the Library Reference Model are strictly linear, from work to expression to manifestation to item, openWEMI allows 

The model assumes that other relationships can exist, in particular relationships between entities of the same type: Work/Work, Expression/Expression, Manifestation/Manifestation, and Item/Item. Those relationships, however, are not included in the core model.
![openRels2](https://user-images.githubusercontent.com/1564129/231845216-bc842bb0-de35-4778-8066-32947af26781.jpg)




