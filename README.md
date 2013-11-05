# Introduction

This repository contains a list of queries illustrating how to use the ChEMBL SPARQL enpoint. If you are new to the
semantic web, you can [follow a tutorial](http://www.cambridgesemantics.com/semantic-university/introduction-to-the-semantic-web). If you have some knowledge about SQL and relational database already, the transition to SPARQL should be easy, first read the introduction below and you can directly get started!

### RDF

RDF stands for Resource Description Framework. Briefly, it is a conceptual way of representing data as a graph, as opposite to relational databases, focusing on relations. Within RDF, the information is encoded as triples, and identifiers are Universal Resource Identifiers (URI or web addresses). Representing data as a graph is interesting because it simplifies the integration of information from different sources. URIs guarantees the uniqueness of resources and allow you to simply explore them with your web browser.

### SPARQL

SPARQL is a language used to query RDF data. It is fairly similar to SQL, yet better standardised and more flexible to query multiple data sources or *services* in the same time. A *SPARQL endpoint* is a web address you use to access the RDF data and run SPARQL queries. The ChEMBL SPARQL enpoint is located at http://www.ebi.ac.uk/rdf/services/chembl/sparql

### What should I consider using the SPARQL endpoint?

Semantic web technologies provide two main advantages. First, they remove the need to maintain, update, download, parse and handle flat files or databases. You can query the ChEMBL data directly from the web, in a fully automated way. RDF helps you to focus entirely on the query, where the real scientific value is.

Secondly, it becomes easier to integrate the data from another provider. For instance, when you analyse ChEMBL data, you may realise that it would be interesting to combine your current results with gene expression or pathway information. SPARQL allows you to do this very easily, as illustrated in the example queries.

### How do I run the queries?

You can directly copy and paste the queries from the files in the web form on the [SPARQL endpoint](http://www.ebi.ac.uk/rdf/services/chembl/sparql). Do not include the commented lines, starting with the symbol `#` in very first line of query, the endpoint does not support them yet. You can put it from 2nd line.

It is also possible to run the queries from R or with command lines. More examples will come to demonstrate this feature. Finally, you can also [check the ChEMBL endpoint documentation](http://www.ebi.ac.uk/rdf/services/chembl/sparql) or [contact us](http://www.ebi.ac.uk/rdf/documentation/chembl) if you are facing problems.

# SPARQL queries over the ChEMBL endpoint

I have kept the ChEMBL triple store queries in a folder /Documents/git/ChEMBL-RDF-queries. We can directly run the query, using terminal but for running on sparql-endpoint of ChEMBL triple store, remove the comment from the query.


### A. Simple SPARQL queries

1. Retrieve ChEMBL molecule from the trade name ("sildenafil"). [File](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/moleculeSourceForTradeName.rq) or [see it live](http://www.ebi.ac.uk/rdf/services/chembl/sparql?query=PREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+owl%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2002%2F07%2Fowl%23%3E%0D%0APREFIX+xsd%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dc%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Felements%2F1.1%2F%3E%0D%0APREFIX+dcterms%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+dbpedia2%3A+%3Chttp%3A%2F%2Fdbpedia.org%2Fproperty%2F%3E%0D%0APREFIX+dbpedia%3A+%3Chttp%3A%2F%2Fdbpedia.org%2F%3E%0D%0APREFIX+foaf%3A+%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+cco%3A+%3Chttp%3A%2F%2Frdf.ebi.ac.uk%2Fterms%2Fchembl%23%3E%0D%0A%0D%0A%0D%0ASELECT+%3Fmolecule%0D%0AWHERE+{%0D%0A++%3Fmolecule+skos%3AaltLabel+%3Fname.%0D%0A++FILTER+regex%28%3Fname+%2C%22sildenafil%22%2C+%27i%27%29%0D%0A}&render=HTML&limit=100&offset=0#lodestart-sparql-results)
2. Retrieve the molecular formula of ChEMBL molecule having ChEMBL-id "CHEMBL192". [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/molFormulaof192Molecule.rq) or [see it live](http://tinyurl.com/pljpjwn)
3. Retrieve rotational bond of ChEMBL molecule having ChEMBL-id  "CHEMBL192". [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/rotbonOf192Molecule.rq) or [see it live](http://tinyurl.com/p8rmghh)
4. Retrieve trade name of CHEMBL192 molecule. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/tradeNameOf192Molecule.rq) or [see it live](http://tinyurl.com/o3uzcol)
5. Retrieve the ChEMBL molecules URI having molecular formula is combination of “C22H30N6O4S”. [file](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/sourceForMolecularFormula.rq) or [see it live](http://tinyurl.com/qzmlsnq)

### B. Moderate (Need to know more about schema to reach the specific location)

1. [Retrieve substance types having target type "cell-line"](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/substanceTypeToCell-line.rq)
- [Retrieve target types available in ChEMBL rdf triple store](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/targetType.rq)
- [Retrieve compound activity details for all target]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundActDetails.rq)
- [Retrieve all the bioactive ChEMBL molecules for bacterial target]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/bacterialTargetData.rq)
- [Retrieve ChEMBL molecules targeting “Firefly Luciferase”]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundToFirLuciferase.rq)
- [Retrieve target details, uniprot_reference and sequences for proteins target]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundDetailsForProteinTar.rq)
- [Retrieve ChEMBL molecules activity details for all targets containing a protein of interest, and protein of interest is human M2 muscarinic receptor (P08172)]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/P08172CompActAssTarDet.rq)
- [Retrieve ChEMBL molecules activity details for a target, and target is Human PDE5 (CHEMBL1827)]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/detailsForTarget.rq)
- [Retrieve ChEMBL molecules activity details for all target]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/compoundActDetails.rq)

In some of the queries, I have used the filter function even is not needed but just to make extra column which give satisfaction for correct output. I helps If you are new for triple store.
For example, I am interested in ChEMBL-id of molecules having activity standard type "IC50" then we can put "IC50" value at standard type but to make a extra column to show that I have selected the correct standard type, can use filter. We can add standard type as a
new column having constant text "IC50" without filter. These differences make change in running time of query. To analyse this kind of changes, I have made query for about same problem in different way like last 5 ChEMBL queries.  

Note: Try to avoid the use of filter function in SPARQL query, because it takes more time for running.

1. [Retrieve ChEMBL molecules ChEMBL-ID, activity standard type, activity standard unit having activity standard type "IC50" and standard unit "nM" using filter]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds.rq)
- [Retrieve ChEMBL molecules ChEMBL-ID having activity standard type "IC50" and activity standard unit "nM"](https://github.com/Ashwini607/ChEMBL-RDF Queries/tree/master/queries/IC50Compounds_1.rq)
- [Retrieve ChEMBL molecules ChEMBL-ID having activity standard type "IC50" and activity standard unit "nM" having extra columns with variable name that contain constant text about standard type and standard unit](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds_2.rq)
- [Retrieve ChEMBL molecules ChEMBL-ID having activity standard type "IC50" and activity standard unit "nM" having extra columns that contains constant text about standard type and standard unit](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds_3.rq)
- [Retrieve ChEMBL molecules ChEMBL-ID, activity standard type, activity standard unit having activity standard type "IC50" and standard unit "nM" using filter but two conditions in a single filter]( https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/queries/IC50Compounds_4.rq)


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

1. [Retrieve known diseases from uniprot](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/knownDisUp.rq)
2. [Retrieve the proteins and their sequence involved in Alzheimer disease (Runs on ChEMBL SPARQL endpoint)](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/proteinRelatedToAlzheimerChEMBL_up.rq)
3. [Retrieve the proteins and their sequence involved in Alzheimer disease (Runs on UniProt SPARQL endpoint)](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/proteinsRelatedToAlzheimerUp.rq)
4. [Retrieve total number of known diseases in uniprot](https://github.com/Ashwini607/ChEMBL-RDF-Queries/tree/master/federatedAndOthersEndpointQueries/totKnownDisUp.rq)
