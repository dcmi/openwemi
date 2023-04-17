I'm trying to find or make up examples of metadata that uses some or all of the openWEMI classes but does not necessarily use WEMI as a structure. I see (at least) two ways to use classes in RDF:
1. to assign a class to a subject node - using rdfType: This is a structural view, and seems to be quite common. The Node then is the hub for a number of arcs
2. to define a vocabulary element with a domain in the vocabulary definition. The vocabulary term can be used anywhere, but wherever it is used the inference is that in its arc the subject is a member of the domain assigned to the term.

