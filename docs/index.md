---
title: Accueil
...
# QDMTL

Données ouvertes et liées pour les quartiers disparus de Montréal<br/>
`#qdmtl` `#lod` `#semweb`

---

Le projet `#qdmtl` propose un modèle de description sémantique sur lequel repose une démonstration de faisabilité pour la publication et la manipulation de données structurées sur les quartiers disparus de Montréal.

Le modèle s’appuie sur deux axes descriptifs alimentés par des sources archivistiques&nbsp;:

1. une description des objets du patrimoine disparu : des infrastructures résidentielles, commerciales, industrielles et institutionnelles rasées pour faire place aux chantiers qui ont façonné la ville telle qu’on la connaît aujourd’hui
2. une description des documents d’archives qui témoignent du patrimoine en question : des photographies, des plans et des documents administratifs

La première phase du projet permettra de présenter les éléments de consultation suivants :

- un jeu de données
- un point d’accès SPARQL
- un prototype d’application cartographique en ligne

## Accès aux données

!!! note "Phase de prépublication"
    **2023-06-01** — Les données sont actuellement exposées en tant que prépublication. À court terme, la structure et le contenu du jeu de données pourraient être substantiellement modifiés.

QDMTL dispose d’un **point d’accès SPARQL** disponible à l’adresse suivante :

- [http://qdmtl.ca/sparql](http://qdmtl.ca/sparql).

Pour en savoir plus, cliquez sur le bouton ci-dessous :

<a class="btn btn-primary btn-lg btn-block" href="info-sparql/" role="button">Informations sur le point d’accès SPARQL</a>

## Échéancier

| Type d’accès | Échéance | Statut |
| --- | --- | --- |
| Point d’accès SPARQL | Semaine du 2 mai 2022 | Opérationnel |
| Sérialisations | Semaine du 2 mai 2022 | RDF/XML au moyen des clauses `CONSTRUCT` et `DESCRIBE` (SPARQL).<br/>RDF/XML avec le graphe `http://data.qdmtl.ca`
| URI déréférençables | Semaine du 9 mai 2022 | Entités de [http://data.qdmtl.ca/](http://data.qdmtl.ca/) (exemple : [http://data.qdmtl.ca/Batiment/1065-1105-Maisonneuve](http://data.qdmtl.ca/Batiment/1065-1105-Maisonneuve), RDF/XML) |
| Plan interactif du Faubourg à m’lasse (prototype d’application cartographique) | Juillet 2023 | v0.1 - avril 2023 : [https://qdmtl.ca/pifm/app/](https://qdmtl.ca/pifm/app/) |

## Méthodologie

Le développement du modèle s’appuie sur la méthodologie SAMOD&nbsp;: *Simplified Agile Methodology for Ontology Development* ([Peroni 2017](https://link.springer.com/chapter/10.1007/978-3-319-54627-8_5)). Il s’agit d’un protocole de développement basé sur de courts cycles itératifs qui placent les données au centre du processus d’élaboration de l’ontologie. Cette méthodologie permet la production du jeu de données parallèlement au développement de l’ontologie. Pour chaque itération, le protocole prévoit les éléments qui suivent :

1. un scénario énonçant les termes de la réalité à décrire
1. une formalisation du modèle correspondant au scénario (format OWL)
1. un échantillon de données permettant de répondre aux questions du scénario
1. des requêtes permettant de formaliser les questions et procéder aux tests d’utilisation

Le modèle développé utilise des ontologies et des vocabulaires décrivant des champs de connaissances pertinents :

- Records in Contexts Ontology, Conseil International des Archives (ICA&#160;RiC&#8209;O)
- Erlangen CRM/OWL, une implémentation du modèle conceptuel de référence du CIDOC
- Art and Architecture Thesaurus, Getty Museum

## Échantillon de données

L’échantillon de données produit dans le cadre de ce projet est principalement lié au secteur du Faubourg à m’lasse, dont une large superficie fut détruite en 1963 pour faire place à la construction de la maison de Radio-Canada.

Dans une moindre mesure, certaines informations concernant d’autres secteurs seront rendues disponibles afin d’esquisser le contexte plus large des quartiers disparus à Montréal.

## Publication

- Valentine, David et Dominic Forest. 2023. « Le projet QDMTL : modéliser les quartiers disparus de Montréal avec des données ouvertes et liées », *Humanités numériques* [en ligne], mis en ligne le 9 juin 2023, consulté le 16 juin 2023. URL : [http://journals.openedition.org/revuehn/3336](http://journals.openedition.org/revuehn/3336)

## Communications

- Valentine, David. 2023. « Défragmenter la mémoire montréalaise. La reconstitution sémantique des liaisons documentaires du Faubourg à m’lasse ». Premier Colloque étudiant du CRIHN. Centre de recherche interuniversitaire sur les humanités numériques. Montréal (communication orale).
- Valentine, David et Dominic Forest. 2022. « Décrire les quartiers disparus de Montréal : modélisation et implémentation d’un réseau de données ouvertes ». Colloque Humanistica 2022. Association francophone des humanités numériques. Montréal (communication par affiche).
<!--
---

## Ressources

- Sources de l’ontologie
- Cas de test
- Sources de la documentation
- Bibliographie
-->

## Contact

- [david.valentine@umontreal.ca](mailto:david.valentine@umontreal.ca)