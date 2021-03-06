# Introduction

This repository contains a list of SPARQL queries illustrating how to use the ChEMBL enpoint. If you are new to the
semantic web, you can first [follow a tutorial](http://www.cambridgesemantics.com/semantic-university/introduction-to-the-semantic-web). If you have some knowledge about SQL and relational database already, the transition to SPARQL should be easy, first read the introduction below and you can directly get started!

### RDF

RDF stands for [Resource Description Framework](http://en.wikipedia.org/wiki/Resource_Description_Framework). Briefly, it is a conceptual way of representing data as a graph, as opposite to relational databases, focusing on tables and their relations. Within RDF, the information is encoded as triples. The nodes and edges of the RDF graph are identified using Universal Resource Identifiers (URI or web addresses). Representing data as a graph is interesting because it simplifies the integration of information from different sources. URIs guarantees the uniqueness of resources and allow you to simply explore them with your web browser.

### SPARQL

SPARQL is a language used to query RDF data. It is fairly similar to SQL, yet better standardised and more flexible to query multiple data sources or *services* in the same time. A *SPARQL endpoint* is a web address you use to access the RDF data and run SPARQL queries. The ChEMBL SPARQL enpoint is located at http://www.ebi.ac.uk/rdf/services/chembl/sparql

### What should I consider using the SPARQL endpoint?

Semantic web technologies provide two main advantages. First, they remove the need to maintain, update, download, parse and handle flat files or databases. You can query the ChEMBL data directly from the web, in a fully automated way. RDF helps you to focus entirely on the query, where the real scientific value is.

Secondly, it becomes easier to integrate the data from another provider. For instance, when you analyse ChEMBL data, you may realise that it would be interesting to combine your current results with gene expression or pathway information. SPARQL allows you to do this easily, as illustrated in the example queries below.

### How do I run the queries?

Simply click on the link to open and run directly the queries from your web browser. You can also copy and paste the queries from the files in the web form on the [SPARQL endpoint](http://www.ebi.ac.uk/rdf/services/chembl/sparql) form. Queries contain a comment in the first lines (lines starting with `#`), summarising what they do. Do not paste the commented lines on the web form, the endpoint does not support them yet.

It is also possible to run the queries from R or with command lines. More examples will come to demonstrate this feature. Finally, you can also [check the ChEMBL endpoint documentation](http://www.ebi.ac.uk/rdf/documentation/chembl) or [contact us](http://www.ebi.ac.uk/rdf/chembl-contact) if you are facing any problems.

# SPARQL queries over the ChEMBL endpoint

Queries are listed by degree of difficulty. More complex queries require a better understanding of the RDF graph's underlying structure. You can find a summary map of the structure [here](http://www.ebi.ac.uk/rdf/documentation/chembl).

### A. Simple SPARQL queries

1. Retrieve ChEMBL molecule from the trade name ("sildenafil"). [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/moleculeSourceForTradeName.rq) or [see it live](http://www.ebi.ac.uk/rdf/services/chembl/sparql?query=PREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+owl%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2002%2F07%2Fowl%23%3E%0D%0APREFIX+xsd%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dc%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Felements%2F1.1%2F%3E%0D%0APREFIX+dcterms%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+dbpedia2%3A+%3Chttp%3A%2F%2Fdbpedia.org%2Fproperty%2F%3E%0D%0APREFIX+dbpedia%3A+%3Chttp%3A%2F%2Fdbpedia.org%2F%3E%0D%0APREFIX+foaf%3A+%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+cco%3A+%3Chttp%3A%2F%2Frdf.ebi.ac.uk%2Fterms%2Fchembl%23%3E%0D%0A%0D%0A%0D%0ASELECT+%3Fmolecule%0D%0AWHERE+{%0D%0A++%3Fmolecule+skos%3AaltLabel+%3Fname.%0D%0A++FILTER+regex%28%3Fname+%2C%22sildenafil%22%2C+%27i%27%29%0D%0A}&render=HTML&limit=100&offset=0#lodestart-sparql-results)
2. Retrieve the molecular formula of ChEMBL molecule having ChEMBL-id "CHEMBL192". [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/molFormulaof192Molecule.rq) or [see it live](http://tinyurl.com/pljpjwn)
3. Retrieve rotational bond of ChEMBL molecule having ChEMBL-id  "CHEMBL192". [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/rotbonOf192Molecule.rq) or [see it live](http://tinyurl.com/p8rmghh)
4. Retrieve trade name of CHEMBL192 molecule. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/tradeNameOf192Molecule.rq) or [see it live](http://tinyurl.com/o3uzcol)
5. Retrieve the ChEMBL molecules URI having molecular formula is combination of “C22H30N6O4S”. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/sourceForMolecularFormula.rq) or [see it live](http://tinyurl.com/qzmlsnq)

### B. Moderate difficulty

1. Retrieve substance types having target type "cell-line". [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/substanceTypeToCell-line.rq) or [see it live](http://tinyurl.com/qh7shqb)
- Retrieve target types available in ChEMBL rdf triple store. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/targetType.rq)or [see it live](http://tinyurl.com/p5ranmk)
- Retrieve compound activity details for all target. [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundActDetails.rq)or [see it live](http://tinyurl.com/ovrz72n)
- Retrieve all the bioactive ChEMBL molecules for bacterial target. [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/bacterialTargetData.rq)or [see it live](http://tinyurl.com/q2rrzma)
- Retrieve ChEMBL molecules targeting “Firefly Luciferase”. [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundToFirLuciferase.rq)or [see it live](http://tinyurl.com/pbvfjyu)
- Retrieve target details, uniprot_reference and sequences for proteins target. [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundDetailsForProteinTar.rq)or [see it live](http://tinyurl.com/nv9lqyl)
- Retrieve ChEMBL molecules activity details for all targets containing a protein of interest, and protein of interest is human M2 muscarinic receptor (P08172). [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/P08172CompActAssTarDet.rq)or [see it live](http://tinyurl.com/qzbepv7)
- Retrieve ChEMBL molecules activity details for a target, and target is Human PDE5 (CHEMBL1827). [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/detailsForTarget.rq)or [see it live](http://tinyurl.com/o53fb73)
- Retrieve ChEMBL molecules activity details for all target. [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundActDetails.rq)or [see it live](http://www.ebi.ac.uk/rdf/services/chembl/sparql?query=PREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+owl%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2002%2F07%2Fowl%23%3E%0D%0APREFIX+xsd%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dc%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Felements%2F1.1%2F%3E%0D%0APREFIX+dcterms%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+dbpedia2%3A+%3Chttp%3A%2F%2Fdbpedia.org%2Fproperty%2F%3E%0D%0APREFIX+dbpedia%3A+%3Chttp%3A%2F%2Fdbpedia.org%2F%3E%0D%0APREFIX+foaf%3A+%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+cco%3A+%3Chttp%3A%2F%2Frdf.ebi.ac.uk%2Fterms%2Fchembl%23%3E%0D%0A%0D%0A%0D%0ASELECT+%3FChEMBL_id+%3Fstd_value+%3Fstd_unit+%3Fstd_type+%3Fstd_rel+%3Fass_disc%0D%0AWHERE+{%0D%0A++%3Fmolecule+cco%3AhasActivity+%3Fact.%0D%0A++%3Fmolecule+rdfs%3AsubClassOf+cco%3ASubstance.%0D%0A++%3Fmolecule+rdfs%3Alabel+%3FChEMBL_id+.%0D%0A++%3Fact+cco%3AhasAssay+%3Fass.%0D%0A++%3Fact+cco%3AstandardValue+%3Fstd_value+.%0D%0A++%3Fact+cco%3AstandardUnits+%3Fstd_unit+.%0D%0A++%3Fact+cco%3AstandardType+%3Fstd_type+.%0D%0A++%3Fact+cco%3AstandardRelation+%3Fstd_rel.%0D%0A++%3Fass+dcterms%3Adescription+%3Fass_disc.%0D%0A++%3Fass+cco%3AhasTarget+%3Ftar.%0D%0A++%3Ftar+rdfs%3Alabel+%3Ftar_id+.%0D%0A}&render=HTML&limit=25&offset=0#lodestart-sparql-results)

In some of the queries, I have used the filter function even is not needed but just to make extra column which give satisfaction for correct output. I helps If you are new for triple store.
For example, I am interested in ChEMBL-id of molecules having activity standard type "IC50" then we can put "IC50" value at standard type but to make a extra column to show that I have selected the correct standard type, can use filter. We can add standard type as a
new column having constant text "IC50" without filter. These differences make change in running time of query. To analyse this kind of changes, I have made query for about same problem in different way like last 5 ChEMBL queries.  

Note: Try to avoid the use of filter function in SPARQL query, because it takes more time for running.

1. Retrieve ChEMBL molecules ChEMBL-ID, activity standard type, activity standard unit having activity standard type "IC50" and standard unit "nM" using filter. [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds.rq) or [see it live](http://tinyurl.com/pdx3wtu)
- Retrieve ChEMBL molecules ChEMBL-ID having activity standard type "IC50" and activity standard unit "nM". [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds_1.rq) or [see it live](http://tinyurl.com/ofgcxxy)
- Retrieve ChEMBL molecules ChEMBL-ID having activity standard type "IC50" and activity standard unit "nM" having extra columns with variable name that contain constant text about standard type and standard unit. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds_2.rq) or [see it live](http://tinyurl.com/nhjm8wb)
- Retrieve ChEMBL molecules ChEMBL-ID having activity standard type "IC50" and activity standard unit "nM" having extra columns that contains constant text about standard type and standard unit. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds_3.rq) or [see it live](http://tinyurl.com/qx2g35g)
- Retrieve ChEMBL molecules ChEMBL-ID, activity standard type, activity standard unit having activity standard type "IC50" and standard unit "nM" using filter but two conditions in a single filter. [file]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds_4.rq) or [see it live](http://tinyurl.com/p5utb9n)


# SPARQL queries for metadata

 If you are new in querying RDF triple store then you can try these queries, because these work on any SPARQL endpoint. It will help to get familiar with contains of triple store.  
 
1. [Retrieve all available triples from triple store]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/metadataQuery1.rq)
- [Retrieve all types defined in triple store]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/metadataQuery2.rq)
- [Retrieve triples which is Subclassof of class]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/metadataQuery3.rq)
- [Retrieve triples those subject are label]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/metadataQuery4.rq)
- [Retrive all declared classes]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/allclassesMetadata.rq)
- [Retrieve properties have been associated for a given class]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/classPropertiesMetadata.rq)
- [Retrieve subclasses descendants of a given class]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/descendatsClassesMetadata.rq)
- [Retrieve the relation with source (URI)]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/describeMetadata.rq)
- [Retrieve the properties]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/propertiesMetadata.rq)
- [Retrieve values has been associated with given property]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/propertyValuesMetadata.rq)
- [Retrieve the service description of the endpoint]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/metadataQueries/serviceDescriptionMetadata.rq )


# Fedarated SPARQL queries or other than ChEMBL endpoint queries

1. Retrieve known diseases from uniprot. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/knownDisUp.rq) or [see it live](http://tinyurl.com/pudqtkl)
2. Retrieve the proteins and their sequence involved in Alzheimer disease (Runs on ChEMBL SPARQL endpoint). [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/proteinRelatedToAlzheimerChEMBL_up.rq)or [see it live](http://tinyurl.com/q6bvutv)
3. Retrieve the proteins and their sequence involved in Alzheimer disease (Runs on UniProt SPARQL endpoint). [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/proteinsRelatedToAlzheimerUp.rq)or [see it live](http://tinyurl.com/nfnw6yx)
4. Retrieve total number of known diseases in uniprot. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/totKnownDisUp.rq)or [see it live](http://tinyurl.com/pnhmoto)
