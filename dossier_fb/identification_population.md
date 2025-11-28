

## Les listes associées à la liste des listes


    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?list
    WHERE {
    dbr:Lists_of_singers dbo:wikiPageWikiLink  ?list.

    FILTER(CONTAINS(STR(?list), 'http://dbpedia.org/resource/List_of'))
        }
    LIMIT 100

### Exemples de personnes associées aux listes

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?person (STR(?psLabel) as ?persLabel) ?listId ?list 
    WHERE {
    dbr:Lists_of_singers dbo:wikiPageWikiLink  ?list.
    ?list ?p ?person.
    ?person a dbo:Person;
        rdfs:label ?psLabel.
    BIND(SUBSTR(STR(?list), STRLEN('http://dbpedia.org/resource/')+1) AS ?listId)
    FILTER(CONTAINS(STR(?list), 'http://dbpedia.org/resource/List_of'))
    FILTER(LANG(?psLabel) = 'en')
        }
    LIMIT 100




### Effectif des personnes par liste

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT  ?listId  (COUNT(*) AS ?number)
    WHERE {
    dbr:Lists_of_singers dbo:wikiPageWikiLink  ?list.
    ?list ?p ?person.
    ?person a dbo:Person
    BIND(SUBSTR(STR(?list), STRLEN('http://dbpedia.org/resource/')+1) AS ?listId)
    FILTER(CONTAINS(STR(?list), 'http://dbpedia.org/resource/List_of'))
        }
    GROUP BY ?listId 
    ORDER BY DESC(?number)

