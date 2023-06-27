*The files listed here are strawpersons for discussion.*

# openWEMI

This is work to create a non-constrained version of FRBR's Work, Expression, Manifestation, Item. In particular it removes any disjoint rules between the WEMI entities. It is based on the [FRBR Core](http://purl.org/vocab/frbr/core) created by Ian Davis and Richard Newman, with contributions by Bruce D'Arcus. 

The minimal WEMI set has these classes and subclasses:
* Endeavor
  * Work
  * Expression
  * Manifestation
  * Item
* ResponsibleEntity

Properties which define the primary relationships between WEMI entities are presented in two "directions": from most concrete (Item) to most abstract (Work), and the inverse from the abstract to the concrete. 

  * expresses (domain: Expression, range: Work)
  * expressedBy (domain: Work, range: Expression)
  * manifests (domain: Manifestation, range: Work or Expression)
  * manifestedBy (domain: Expression or Work, range: Manifestation)
  * instantiates (domain: Item, range: Work or Expression or Manifestation)
  * instantiatedBy (domain: Work or Expression or Manifestation, range:Item)

It also provides properties that describe relationships between entities of the same type:
  * relatedEndeavor (domain:Endeavor, range:Endeavor)
  * relatedWork (domain:Work, range:Work)
  * relatedExpression (domain:Expression, range:Expression)
  * relatedManifestation (domain:Manifestation, range:Manifestation)
  * relatedItem (domain:Item, range:Item)

Classes and properties are intended as a foundation for more specific vocabularies that would be related to openWEMI through sub-classes and sub-properties.

## Files

* openWEMI.ttl  - this defines the WEMI classes as being sub-classes of "/Endeavor/". Endeavor encompasses the entire creation. Endeavor was introduced in [frbrCore](https://vocab.org/frbr/core). It also includes property "relatedEndeavor" from that vocabulary which is a general relationship between endeavors and "ResponsibleEntity", a general class to define the agent responsible for the creation. 

