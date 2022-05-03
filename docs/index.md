# QDMTL

Données ouvertes et liées pour les quartiers disparus de Montréal<br/>
`#qdmtl`

---

Le projet `#qdmtl` propose une modélisation sémantique sur laquelle repose une démonstration de faisabilité pour la publication et la manipulation de données structurées sur les quartiers disparus de Montréal.

À partir de sources archivistiques, il s’agit de décrire ce patrimoine : des infrastructures résidentielles, commerciales, industrielles et institutionnelles rasées pour faire place aux chantiers qui ont façonné la ville telle qu’on la connaît aujourd’hui.

---

## Accès aux données

!!! note "Prépublication"
    Les données sont actuellement exposées sous la forme d’une prépublication. La structure et le contenu du jeu de données pourraient être substantiellement modifiés dans les prochaines semaines.

| Type d'accès | Échéance |
|---|---|
| Point d’accès SPARQL | Semaine du 2 mai 2022 |
| Sérialisations | Semaine du 2 mai 2022 |
| URI déréférençables<br/>Fiches d’informations | Semaine du 9 mai 2022 |

---

## Méthodologie

Le développement de l’ontologie s’appuie sur la méthodologie SAMOD : *Simplified Agile Methodology for Ontology Development* (Peroni 2016). Il s’agit d’un protocole de développement basé sur de courts cycles itératifs qui placent les données au centre du processus d’élaboration de l’ontologie. Cette méthodologie permet la production du jeu de données parallèlement au développement de l’ontologie. Pour chaque itération, le protocole prévoit une portion de modélisation s’appuyant sur quatre éléments :

1. un scénario énonçant les termes de la réalité à décrire;
1. une formalisation du modèle correspondant au scénario (dans le format OWL 2);
1. un échantillon de données permettant de répondre aux questions du scénario;
1. des requêtes permettant de formaliser les questions.

Le modèle développé utilise des ontologies et des vocabulaires décrivant des champs de connaissances pertinents :

- Records in Contexts Ontology, développée par le Conseil International des Archives (ICA RiC-O)
- Erlangen CRM / OWL, une implémentation du modèle conceptuel de référence du CIDOC
- Art and Architecture Thesaurus du Getty Museum

<!--

Principes d’implémentation appliqués\ :

- Classes et propriétés sont tirées de ces ontologies.
- Chaque fois que possible, on utilise des vocabulaires contrôlés pour décrire les instances.
- Ensuite on ajoute

En plus de ces modèles de références, elle puise dans plusieurs vocabulaires contrôlés.

Si nécessaire, elle propose ses classes et vocabulaires.

Aspects fondamentaux

- Enregistrements d’archive
- Objets urbains (rues, immeubles)
- Objets territoriaux (lieux et territoires)
- Agents

-->

---

## Communication

Valentine, David et Dominic Forest. 2022. « Décrire les quartiers disparus de Montréal : modélisation et implémentation d’un réseau de données ouvertes ». Colloque Humanistica 2022. Association francophone des humanités numériques. Montréal (communication par affiche).
<!--
---

## Ressources

- Sources de l’ontologie
- Cas de test
- Sources de la documentation
- Bibliographie
-->
---

## Contact

- [david.valentine@umontreal.ca](mailto:david.valentine@umontreal.ca)

<!--

## Autres

SPA Specifications

The future database of the SAPA Foundation will be published as linked data and build on the conceptual models CIDOC-CRM, FBBRoo and RiC. As RiC is still in development, its classes and properties may be substituted with equivalents from ORE, PREMIS, PROV and RDA for the time being.

The implementation of these models is guided by the following ideas:

    Classes and properties come from the three reference ontologies.
    They are further specified by a domain-specific vocabulary.
    There is a distinction between core entities (such as persons or works) that should be publicly addressable and entities (such as appellations) that serve primarily auxiliary functions. The latter are represented by special URIs and are shown here as blank nodes.
    Make individual decisions in which case complexity is actually needed. If this is the case, think about providing a reduced version of the same information in a simple way. (Names are a good example here. They can be pretty complicated but sometimes one just needs a simple label.)

Basic Concepts

The documentation is structured along the following basic concepts:

    Actors/Agents (individual persons, groups, institutions)
    Records
    Objects (incl. venues, archival objects including videos)
    Works (performing arts works and their originals such as written plays or musical compositions)
    Seasons
    Places

General Concepts

Some concepts apply to more or less to all entities:

    Identities (types, identifiers, appellations)
    Time

RDF sample code is in turtle syntax and covers only the aspects that are relevant in the respective context.

-->