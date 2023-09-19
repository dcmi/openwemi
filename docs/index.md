# openWEMI Primer
**A minimally constrained vocabulary for Work, Expression, Manifestation, and Item**

## About this specification
This document and the related resources are the work of the Dublin Core Metadata Initiative's openWEMI Community Group. The group uses github for its work, and welcomes comments on the work. All resources are open for viewing and github issues can be created by anyone with a github account. The email list is self-subscribe. 

* The [openWEMI mailing list](https://lists.dublincore.org/mailman/listinfo/openwemi)
* [openWEMI on github](https://github.com/dcmi/openwemi)

## Introduction

openWEMI is an RDF vocabulary based on the concepts of Work, Expression, Manifestation, and Item that were first introduced in the Functional Requirements for Bibliographic Records (FRBR) document that was produced by a working group of the International Federation of Library Associations (IFLA). 

For the purposes of this draft, the vocabulary is using the namespace https://dcmi.github.io/openwemi/ns#. It is anticipated that a true namespace will be assigned after review by the DCMI Usage Board.

* Human-friendly documentation: [https://dcmi.github.io/openwemi/ns/openWEMI.html](https://dcmi.github.io/openwemi/ns/openWEMI.html)
* Vocabulary in turtle: [https://dcmi.github.io/openwemi/ns/openWEMI.ttl](https://dcmi.github.io/openwemi/ns/openWEMI.ttl)

The concepts introduced in FRBR document have been employed in metadata for resources quite different from those in the library bibliographic catalog, and often ignoring some of the restrictions built in to the original definition. (More in this [article](https://journal.code4lib.org/articles/16491) and see the [bibliography](bibliography.md)). This is evidence that a definition of similar classes that are more general than those developed for library usage would benefit metadata developers broadly. 

This DCMI work product proposes a minimally constrained set of classes and relationships that could form the basis for a useful model of created works that defines WEMI as RDF classes with few constraints. These classes can be used together or separately in metadata to characterize aspects of creations. 

openWEMI classes are purposely defined very broadly. Experience shows that metadata models are likely to use openWEMI classes as superclasses to the more specific materials being described. The proposal includes the superclass Endeavor, which is not part of the FRBR group of entities but was added by the authors of FRBR core and is deemed to be needed to create a coherent grouping of the entities. It also would be useful should any new high-order entities be added in the future. 

## What is WEMI?

openWEMI defines a non-constrained version of FRBR's Work, Expression, Manifestation, Item. In particular it removes any disjoint rules between the WEMI entities and removes any reference to bibliographic entities from their definitions. It is loosely based on the [FRBR Core](http://purl.org/vocab/frbr/core) created by Ian Davis and Richard Newman, with contributions by Bruce D'Arcus, and which is used in several non-library RDF implementations. 

The original analysis by the FRBR Working Group produced of a 4-layer model of metadata that could be applied to every library catalog entry. openWEMI retains these concepts, expanded beyond the bibliographic application.

*Work* is the most abstract layer that represented the conceptual aspect of a creation. Expression is a perceptible version using some form of communication like text, sound, or a visual display. *Manifestation* is the realization, which can be a manufactured product in multiple copies or a single object. *Item* is an individual instance of the creation, often having a location in the world, including electronic locations

This proposal includes one other class which is a super-class over each of the WEMI classes and serves to provide them. *Endeavor* is a creation that may be described by any of the WEMI classes, as appropriate to the nature of the creation and the use cases addressed by the metadata

## The proposal
### Classes
The minimal WEMI set has these classes and subclasses:
* Endeavor
  * Work
  * Expression
  * Manifestation
  * Item
* ResponsibleEntity

![Screenshot 2023-09-07 at 8 55 42 AM](https://github.com/dcmi/openwemi/assets/1564129/fa993378-921f-42b4-8585-c149fae574a1)

These are defined in the vocabulary as:
* Endeavor: "A creation"
* Work: "An abstract notion of an artistic or intellectual creation."
* Expression: "A perceivable form of the creation"
* Manifestation: "The physical embodiment of a creation"
* Item: "An exemplar of a creation."
* ResponsibleEntity: "An agent with some responsibility related to a creation."

### Relationship properties
These properties define the primary relationships between WEMI:
  * expresses (range: Work)
  * expressedBy (range: Expression)
  * manifests (range: Work or Expression)
  * manifestedBy (range Manifestation)
  * instantiates (range: Work or Expression or Manifestation)
  * instantiatedBy (range: Item)
Which is expressed in this diagram:
![relationships](https://github.com/dcmi/openwemi/assets/1564129/74b70a1f-ccd1-4294-827c-1c6703fc495e)

The primary relationship properties are as open as possible while still maintaining the logical progression between the most general concept of the Work to the Item. Unlike these relationships in FRBR and in the Library Reference Model which are strictly linear, from Work to Expression to Manifestation to Item, openWEMI allows all relationships that maintain the overall semantics of the classes.

The model also provides properties expressing relationships between entities of the same type
* relatedWork (range: Work)
* relatedExpression (range: Expression)
* relatedManifestation (range: Manifestation)
* relatedItem (range: Item)

What counts as "related" depends entirely on the area of the metadata description and the needs of the constituents. For example, famous works of art are often copied in different and even quite varied forms, like this:
![‎thewave](https://github.com/dcmi/openwemi/assets/1564129/53322a03-4611-46eb-ad01-a48c32f4c00d)


Depending on ones' need, these could be considered related works. Some artworks are created in multiple copies that are considered distinct. These might be viewed as related manifestations, or even as related copies.
![Screenshot 2023-09-10 at 9 21 33 AM](https://github.com/dcmi/openwemi/assets/1564129/2aaff76f-da7b-42aa-a231-8de0fea7697e)

In the fashion industry, designs are re-purposed by different brands, creating what could be seen as related works.
![glasses](https://github.com/dcmi/openwemi/assets/1564129/2e8ec556-e43e-422f-aace-435a7052ab73)

In addition to these relationships there are properties that can be used to indicate that two resources represent or contain the same openWEMI entity:
* commonEndeavor
* commonWork
* commonExpression
* commonManifestation
* commonItem
  
There are no ranges or domains for these properties so that they could be used without making a class inference about either resource. They can be used to describe relationships between resources or resource representations that do not otherwise make use of the WEMI concepts.

## Using openWEMI in RDF
### Vocabulary method
It is not expected that most uses of openWEMI will use the classes and properties directly although that is not in any way prohibited. The openWEMI elements are defined very broadly with the intention of encouraging reuse in a wide variety of circumstances, by defining sub-elements in the metadata vocabulary that are specific to the resources being described. Metadata describing recorded music might define subclasses such as:

| openWEMI class| recorded music subclass |
|-|-|
| openWEMI:Work | rm:Work  |
| openWEMI:Expression | rm:Session  |
| openWEMI:Manifestation | rm:Product  |

![musicSubclasses drawio](https://github.com/dcmi/openwemi/assets/1564129/1d54cc54-8c54-4e65-a83b-596c16aa77f5)

It is not required that sub-elements be one-to-one with openWEMI. openWEMI is a starting point on which one can define additional concepts for the metadata in question. As an example, recorded music may have specific expressions that are derived from other expressions, and therefore could define

| openWEMI class| recorded music subclass |
|-|-|
| openWEMI:Work | rm:Work  |
| openWEMI:Expression | rm:Session  |
| openWEMI:Expression | rm: Mix |
| openWEMI:Manifestation | rm:Product  |


![musicSubclasses2 drawio](https://github.com/dcmi/openwemi/assets/1564129/0693938c-4446-4a99-bb8a-81f12d5fbeac)


Properties can also be sub-defined to the openWEMI properties, and may be renamed to be specific to the resources being described. 

| openWEMI property| recorded music subproperty |
|-|-|
| openWEMI:expresses | rm:records  |
| openWEMI:expresses | rm:mixes |

This could look like:

![Concept map creation worksheet - Color](https://github.com/dcmi/openwemi/assets/1564129/77ee7e5c-f945-4bc7-9f25-3503542003da)


Alternately, because there is no prohibition against adding new classes or properties to the basic model, one could create other classes and properties that do not have an equivalent in openWEMI.

| openWEMI class| recorded music  class|
|-|-|
| openWEMI:Work | rm:Work  |
| openWEMI:Expression | rm:Session  |
|  | rm: Mix |
| openWEMI:Manifestation | rm:Product  |

| openWEMI property| recorded music  property|
|--|--|
| openWEMI:expresses | rm:records  |
|  | rm:mixes |

Whether one subdefines all elements to an openWEMI element or adds elements beyond those of the openWEMI model depends on the use cases one is addressing. If it is desirable to search on the broad openWEMI elements then defining elements with subordinate relationships to openWEMI in the vocabulary is useful.

For those with existing vocabularies who for their own reasons do not want to make direct connections between the vocabulary and openWEMI, openWEMI elements can be used directly in metadata.


