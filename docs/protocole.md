---
title: Protocole
...
# Géolocalisation

Protocole de géolocalisation pour le projet du Faubourg à m’lasse

---

Ce protocole décrit les étapes permettant de géolocaliser les bâtiments des quartiers disparus de Montréal et de consigner les données dans une structure de transition.

## Préalables

### Git

Dépôt Git adéquatement configuré :

```bash
$ git clone git@github.com:qdmtl/faubourg-demo.git
```

### Avant de commencer

Liste des éléments nécessaires aux activités de géolocalisation.

- Éléments obligatoires :
      - **Voie** (voir la liste des voies dans la section [ressources](#ressources)).
      - **Séquence de numéros civiques** (valider en croisant les informations des plans et des rôles d’évaluation foncière).
      - **Numéro d’inventaire**.
- Élément facultatif :
      - Nom du bâtiment.

## Fichiers locaux

*Préparation des fichiers locaux*.

1. Démarrer VS Code.
1. Dans VS Code, ouvrir le dossier de l’application.
1. S’assurer de se trouver dans la branche de développement. Pour vérifier, `$ git status`. Si nécessaire, `$ git checkout dev`.
1. Synchroniser avec la branche distante.

Le système local est prêt.

## `geojson.io`

*Préparation de l’interface `geojson.io` et chargement des données*.

**Utiliser Chrome.**

1. Démarrer l'application `geojson.io` en suivant le lien suivant : [http://geojson.io/#data=data:text/x-url,https%3A%2F%2Fntnlv.ca%2Ffaubourg%2Fmap%2Fbuildings.json&map=16/45.518314/-73.550455](http://geojson.io/#data=data:text/x-url,https%3A%2F%2Fntnlv.ca%2Ffaubourg%2Fmap%2Fbuildings.json&map=16/45.518314/-73.550455).
1. Dans le menu de l'application `geojson.io` (coin supérieur gauche), aller à `Meta > Add raster tile layer`.
1. Dans la boite de dialogue, copier-coller l'URL suivante et appuyer sur `OK` : `https://ntnlv.ca/faubourg/tiles/{z}/{x}/{y}.png`
1. Dans la boite de dialogue qui s'ouvre ensuite, entrer le nom de la couche de tuiles souhaité et appuyer sur `OK` (peut être n'importe quelle chaîne de caractères).

### Extraction des coordonnées

Pour chaque bâtiment, effectuer les étapes suivantes :

1. Sélectionner l’outil « Draw Point ».
1. Placer le point à l’emplacement voulu sur la carte (**note** : le dernier point ajouté se retrouve systématiquement au bas de la liste dans la sérialisation GeoJSON.
1. Dans l’éditeur à droite, sélectionner l’onglet « Table » et saisir les données dans les champs appropriés du tableau.

## Sauvegarde

1. Par mesure de précaution, synchroniser la branche `dev` avec la branche distante.
1. Dans `geojson.io`, `Save > GeoJSON`, puis écraser l’actuel fichier `building.json` (**note** : s’assurer d’utiliser la bonne extension, `.json`).
1. Dans VS Code, ouvrir l’onglet `Source Control`, à gauche.
1. Cliquer sur le bouton `Stage Changes` (icône +) pour le fichier `buildings.json`. 
1. Décrire les chagement de la champ `Message`.
1. Cliquer sur le bouton `Commit`.
1. Synchroniser avec la branche distante.

## Ressources

- https://geojson.org/geojson-ld/
- [Liste des voies](http://qdmtl.ca/sparql/#query=PREFIX%20rdfs%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0APREFIX%20qdmtl%3A%20%3Chttp%3A%2F%2Fonto.qdmtl.ca%2F%3E%0ASELECT%20%3FURI%20%3Flabel%20%3FseeAlso%20WHERE%20%7B%0A%09%3FURI%20a%20qdmtl%3AE24_Thoroughfare%20%3B%0A%09%09rdfs%3Alabel%20%3Flabel%20.%0A%20%20OPTIONAL%20%7B%0A%09%3FURI%20rdfs%3AseeAlso%20%3FseeAlso%20.%0A%20%20%7D%09%0A%7D&endpoint=endpoint.php&requestMethod=POST&tabTitle=Requ%C3%AAte%201&headers=%7B%7D&contentTypeConstruct=application%2Fn-triples%2C*%2F*%3Bq%3D0.9&contentTypeSelect=application%2Fsparql-results%2Bjson%2C*%2F*%3Bq%3D0.9&outputFormat=table)
