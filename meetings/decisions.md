# Running list of things decided
3-29
AGREED definitions:
* Work: "An abstract notion of an artistic or intellectual creation."
* Expression: "A perceivable form of the creation"
* Manifestation: "The physical embodiment of a creation"
* Item: "An exemplar of a creation."

AGREED: Endeavor is useful; keep it

4-2

4-26
* AGREED: Endeavor will be defined as "A creation"
* AGREED: Use verb forms of predicates ("expresses")

5-10
* Drop `ResponsibleEntity` class, but add `responsibleEntity` property

5-17
* Decided: May 17. Use "responsibleEntity" property, but define broadly enough that "responsible" fits a wide variety of relationships.
* Decided: will need inverse relationships
* Relationship of Endeavor and Work: The group agrees that the appropriate relationship is "subclass" and that Endeavor is a kind of organizing "bucket".

6-14
* Decided: properties will have domains and ranges; documentation will explain the potential use of strings as objects.

6-21
* Yes, define properties as RDFs, not OWL:ObjectProperty
* Yes to inverse relationships, and define them as OWL:inverse

6-28
* replace owl:Class with rdfs:Class
* No range on `responsibleEntity`
* Keep owl:unionOf
* Keep owl:Ontology
* Add fuller descriptions to that vocabulary is self-documenting

8-13
* make properties sub-property to dct:relation
* add commonX - as owl:equivalentProperty to vocab.org
