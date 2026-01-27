http://dbpedia.org/resource/List_of_Portuguese_singers

### ressources liées 

PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>
SELECT ?person ?object
WHERE { 
dbr:List_of_Portuguese_singers ?p ?person.
?person a dbo:Person;
        dbo:birthDate ?birthDate ;
    <http://www.w3.org/2002/07/owl#sameAs> ?object.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( ?birthYear > 1770)
}
LIMIT 100


### compter
PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
SELECT ?addr (COUNT(*) AS ?number)
WHERE { 
dbr:List_of_Portuguese_singers ?p ?person.
?person a dbo:Person;
        dbo:birthDate ?birthDate ;
    owl:sameAs ?object.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( ?birthYear > 1770)
BIND(SUBSTR(STR(?object), 1, 20) as ?addr)
}
GROUP BY ?addr
ORDER BY DESC(?number)


### GND (base de recherche allemande)
PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>

SELECT ?person ?object
WHERE { 
dbr:List_of_Portuguese_singers ?p ?person.
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
dbr:List_of_Portuguese_singers ?p ?person.
?person a dbo:Person;
        dbo:birthDate ?birthDate ;
    <http://www.w3.org/2002/07/owl#sameAs> ?object.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( ?birthYear > 1770 && CONTAINS(STR(?object), 'wikidata'))
}
LIMIT 10