http://dbpedia.org/resource/List_of_American_Grammy_Award_winners_and_nominees

List_of_American_Grammy_Award_winners_and_nominees


### compter
PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>
SELECT (COUNT(*) as ?eff)
WHERE { 
dbr:List_of_American_Grammy_Award_winners_and_nominees ?p ?o1.
?o1 a dbo:Person.
  }
   
   réponse : 816



### GND (base de recherche allemande)
PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>

SELECT ?person ?object
WHERE { 
dbr:List_of_American_Grammy_Award_winners_and_nominees
 ?p ?person.
?person a dbo:Person;
        dbo:birthDate ?birthDate ;
    owl:sameAs ?object.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( ?birthYear > 1770 && CONTAINS(STR(?object), 'gnd'))
}
LIMIT 10



## WIKIDATA

### liste d'uris depuis dbpedia
PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>
SELECT ?person ?object
WHERE { 
dbr:List_of_American_Grammy_Award_winners_and_nominees ?p ?person.
?person a dbo:Person;
        dbo:birthDate ?birthDate ;
    <http://www.w3.org/2002/07/owl#sameAs> ?object.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( ?birthYear > 1770 && CONTAINS(STR(?object), 'wikidata'))
}
LIMIT 10