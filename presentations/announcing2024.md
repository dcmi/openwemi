# Announcing OpenWEMI
***A minimally constrained vocabulary***

In 1998 a working group of the International Federation of Library Associations published a new and innovative model for library catalog data.[1] Based on an analysis of the bibliographic relationships uncovered in bibliographic metadata, the model represented a view of created resources from the conceptual to the physical. The main elements of this model are:

 *   Work - the conceptual level
 *   Expression - the mode of communication
 *   Manifestation - the realization, physical or digital
 *  Item - an instance

These are incorporated into the Library Reference Model (LRM) where they are defined along with other model elements that support library cataloging.[2] The LRM model is specific to library catalog applications and is described with definitions and constraints that support those applications.

The general concepts of Work, Expression, Manifestation, and Item (WEMI) have been found useful by metadata creators unrelated to the library catalog use case. Some developers have borrowed the WEMI concepts and integrated them into their own applications.[3] These uses usually do not follow the definitions and constraints of the LRM model, nor are there formal vocabulary relations between these uses and the library vocabulary.

To facilitate the use of the metadata concepts in WEMI outside of the LRM vocabulary, a more general vocabulary that encodes WEMI with minimal constraints and very general definitions is needed. OpenWEMI [4] has been developed to fill this need. This is a project supported by the Dublin Core Metadata Initiative (DCMI).[5]

The RDF vocabulary of OpenWEMI consists of classes for `Work`, `Expression`, `Manifestation` and `Item`, as well as a super-class, `Endeavor`, that groups these. Relationships between the classes are defined as properties that maintain the direction of general-to-specific of WEMI but that allow various combinations of classes to be employed. The vocabulary also includes four properties that can be used to express that any two resources are related through one or more WEMI  classes, e.g. `commonWork`.

The OpenWEMI vocabulary can be used directly but the practical assumption is that it will be used as a general model for the definition of context-specific metadata vocabularies. For example, a subclass of the OpenWEMI Work could be a "MusicWork", an "ArtWork", or an "ArchitectureWork". All of the OpenWEMI classes and properties can be used in this way. Anyone wishing to make use of the concepts of WEMI can now do so, utilizing the OpenWEMI vocabulary as a meta-model for their data. 

Please see the documentation for OpenWEMI [4]. The RDF vocabulary file is available in turtle format. [6] Examples and other documents, including github issues, are publicly available. [7]

[1] IFLA Study Group on the Functional Requirements for Bibliographic Records. (2009) Functional Requirements for Bibliographic Records. Den Haag. http://archive.ifla.org/VII/s13/frbr/frbr_2008.pdf  
[2] Riva, P., Le Boeuf, P., Žumer, M. (2017) IFLA Library Reference Model: A Conceptual Model for Bibliographic Information. Den Haag, IFLA. https://repository.ifla.org/handle/123456789/40  
[3] Coyle, Karen. Works, Expressions, Manifestations, Items: An Ontology. Code4lib Journal, Issue 53, 2022-05-09. https://journal.code4lib.org/articles/16491  
[4] https://dcmi.github.io/openwemi/  
[5] https://dublincore.org/  
[6] https://dcmi.github.io/openwemi/ns/openWEMI.ttl  
[7] https://github.com/dcmi/openwemi/tree/main  
