# openWEMI Questions and Answers

## Isn't openWEMI too broad and vague to be useful?

It is true that the four classes of openWEMI are extremely broad and are semantically "loose". That is by design. Like the OWL class "owl:Thing" openWEMI classes will rarely be useful on their own. The intention is that they will be super-classes to more specific metadata classes. Rather than thinking of openWEMI as classes that you might assign to your metadata, think of it as a high-level organizing principle. Here's an example using FaBiO:
* openWEMI:Work (defined as: the intellectual or artistic content of a distinct creation)
    * fabio:Work (defined as: restricted to academic works that are published)

and one using the music ontology:
* openWEMI:Manifestation (defined as: The physical embodiment of a creation)
    * musicalManifestation (This entity is related to the edition/production/publication of a musical expression)

openWEMI should provide to metadata developers ideas for possible organization of their data.

## How is this different from FRBR/LRM WEMI?

FRBR/LRM WEMI is a model for the creation of library catalog data. It defines the entities as they are to be implemented in library catalog data; it constrains the data that can be associated with each of the WEMI entities; and it constrains the relationship between the entities. In this sense, FRBR/LRM WEMI could be seen as an application profile based on openWEMI. 

## Why not use the FRBR/LRM WEMI?

The FRBR/LRM WEMI is suitable for a specific application: library catalog data. Library catalogs contain metadata for certain types of recorded and fixed creations. There are many types of creations that libraries either do not gather or do not include in standard catalog entries. These include commercial processes, un-recorded events, constructions and buildings, among others. The FRBR/LRM models impose constraints on WEMI that are appropriate for library data but that can be hindrances to the use of WEMI by others.

Even if your metadata could be analogous to the metadata modelled in FRBR/LRM, IFLA, the organization supporting the FRBR and Library Reference Model efforts, has not provided a machine-actionable instance of its models, which it describes as "conceptual models." An RDF version of the FRBR model was developed as a vocabulary in [vocab.org](https://vocab.org/frbr/core), but that model was created by a third party and has no official status. That vocabulary, which was intended to be used for library data, includes the same constraints from the FRBR model that openWEMI avoids.

## Will openWEMI promote interoperability?

Only in a small way. Since it is expected that metadata designers will create their own subclasses and sub-subclasses of openWEMI for their own needs, true interoperability would require knowledge of those subclasses. However, there are some advantages in approaching metadata that is subclassed to openWEMI. For example, in searching a data store using such subclasses, even if those subclasses are not known, the superclasses of openWEMI can be used in the search, which can retrieve all subclasses. 

openWEMI does little to constrain ones data in a way that would support interoperability. That latter would be the function of a metadata model or an application profile that is specific to a community or use case.
