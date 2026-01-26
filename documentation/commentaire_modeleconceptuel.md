
Ce document contient le commentaire, avec exemples, du modèle conceptuel

## Person

Tout être humain. 

### Propriétés
Nom standard, notice, le genre, éventuellement la date de mort.
Il s'agit d'une classe objet (persistent item)


## Occupation

Un métier ou tout autre type d'occupation
Il s'agit d'une classe objet (persistent item)

### Propriétés
Nom standard, notice

### Relations
Une relation réfléxive de spécialisation, termes plus génériques associés à des termes plus précis.


## Pursuit

Le fait d'avoir telle occupation ou activité durant telle période 
Il s'agit d'une classe temporalité (temporal entity)


### Relations

Une _Pursuit_ peut comprend une et une seule personne, une et une seule occupation (ces deux relations sont nécessaires) et éventuellement on peut associer une (et une seule) organisation auprès de laquelle l'activité est exercée.

Si plusieurs organisation sont concernées par une activité, plusieurs individus de la classe _Pursuit_ seront créées.



## Tag

Un mot clé qui introduit un classement de recherche, généralement lié au questionnement.


## Song
Un track appartenant à un album et chanté par un artiste.

## Album
Un album comporte plusieurs chansons.

## Prize
Un artiste gagne un prix pour une chanson ou un album spécifique.
