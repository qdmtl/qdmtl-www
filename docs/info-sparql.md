---
title: SPARQL
...
# SPARQL

Informations sur le point d’accès SPARQL du projet QDMTL

---

Le projet QDMTL met à disposition un point d’accès SPARQL permettant d’explorer le jeu de données dans l’état actuel du développement.

<a class="btn btn-primary btn-lg btn-block" href="http://qdmtl.ca/sparql" role="button" target="_blank">Point d’accès SPARQL <span style="font-family:'DejaVu Sans'">&#8599;</span></a>

## Spécification

### SPARQL 1.0

Ce point d’accès implémente la spécification [SPARQL 1.0](https://www.w3.org/TR/rdf-sparql-query) à laquelle s’ajoutent les principales fonctions d’agrégation.

Pour en savoir plus sur cette implémentation, consultez le document disponible à l’adresse suivante :

- [https://github.com/semsol/arc2/blob/master/doc/SPARQL-support.md](https://github.com/semsol/arc2/blob/master/doc/SPARQL-support.md)

### SPARQL 1.1

Date prévue du déploiement de l’entrepôt RDF avec implémentation de la spécification SPARQL 1.1 :

- à déterminer


## Exemple de requêtes

### Bâtiments avec coordonnées géographiques

La liste des bâtiments avec :

- l’URI contenant la version française du nom de la classe
- l’étiquette associée au bâtiment
- le nom du bâtiment lorsqu’une appellation existe
- les coordonnées géographiques lorsqu’elles sont disponibles

<a target="_blank" href="http://qdmtl.ca/sparql/#query=PREFIX%20rdfs%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0APREFIX%20qdmtl%3A%20%3Chttp%3A%2F%2Fonto.qdmtl.ca%2F%3E%0APREFIX%20owl%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2002%2F07%2Fowl%23%3E%0APREFIX%20geo%3A%20%3Chttp%3A%2F%2Fwww.opengis.net%2Font%2Fgeosparql%23%3E%0APREFIX%20ecrm%3A%20%3Chttp%3A%2F%2Ferlangen-crm.org%2Fcurrent%2F%3E%0A%0ASELECT%20DISTINCT%20%3FuriFr%20%3Flabel%20%3Fappellation%20%3Fpoint%0A%20%20WHERE%20%7B%0A%20%20%20%20%3Fs%20a%20qdmtl%3AE24_Building%20%3B%0A%20%20%20%20%20%20owl%3AsameAs%20%3FuriFr%20%3B%0A%20%20%20%20%20%20ecrm%3AP1_is_identified_by%20%3Fidentifier%20%3B%0A%20%20%20%20%20%20rdfs%3Alabel%20%3Flabel%20.%0A%20%20%20%20OPTIONAL%20%7B%0A%20%20%20%20%20%20%3Fs%20ecrm%3AP53_has_former_or_current_location%20%3Fplace%20.%0A%20%20%20%20%20%20%3Fplace%20ecrm%3AP168_place_is_defined_by%20%3FgeoFeature%20.%0A%20%20%20%20%20%20%3FgeoFeature%20geo%3AasGeoJSON%20%3Fpoint%20.%20%7D%0A%20%20%09OPTIONAL%20%7B%0A%20%20%20%20%20%20%3Fidentifier%20a%20ecrm%3AE41_Appellation%20%3B%0A%20%20%20%20%20%20%20%20rdfs%3Alabel%20%3Fappellation%20.%20%7D%0A%20%20%7D&endpoint=endpoint.php&requestMethod=POST&tabTitle=Query&headers=%7B%7D&contentTypeConstruct=application%2Fn-triples%2C*%2F*%3Bq%3D0.9&contentTypeSelect=application%2Fsparql-results%2Bjson%2C*%2F*%3Bq%3D0.9&outputFormat=table&outputSettings=%7B%22pageSize%22%3A100%7D">Lien vers la requête &nearr;</a>

```plain
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX qdmtl: <http://onto.qdmtl.ca/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX geo: <http://www.opengis.net/ont/geosparql#>
PREFIX ecrm: <http://erlangen-crm.org/current/>

SELECT DISTINCT ?uriFr ?label ?appellation ?point
  WHERE {
    ?s a qdmtl:E24_Building ;
      owl:sameAs ?uriFr ;
      ecrm:P1_is_identified_by ?identifier ;
      rdfs:label ?label .
    OPTIONAL {
      ?s ecrm:P53_has_former_or_current_location ?place .
      ?place ecrm:P168_place_is_defined_by ?geoFeature .
      ?geoFeature geo:asGeoJSON ?point . }
  	OPTIONAL {
      ?identifier a ecrm:E41_Appellation ;
        rdfs:label ?appellation . }
  }
```

### Photographies avec lien vers le fichier numérique

La liste des photographies portant le numéro d’inventaire `116` :

- l’URI de la pièce d’archive dans la structure de QDMTL
- le numéro d’inventaire apparaissant sur la photographie
- le format du fichier
- l’URL de la photo dans les Archives de Montréal

<a target="_blank" href="http://qdmtl.ca/sparql/#query=PREFIX%20dcterms%3A%20%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0APREFIX%20rico%3A%20%3Chttps%3A%2F%2Fwww.ica.org%2Fstandards%2FRiC%2Fontology%23%3E%0APREFIX%20schema%3A%20%3Chttps%3A%2F%2Fschema.org%2F%3E%0APREFIX%20skos%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0APREFIX%20vocab%3A%20%3Chttp%3A%2F%2Fvocab.qdmtl.ca%2F%3E%0A%0ASELECT%20%3Frecord%20%3FnoInv%20%3Fformat%20%3Ffile%0A%20%20WHERE%20%7B%0A%20%20%20%20%3Frecord%20a%20rico%3ARecord%20%3B%0A%20%20%20%20%20%20rico%3AhasOrHadIdentifier%20%3Fid%20%3B%0A%20%20%20%20%20%20rico%3AhasInstantiation%20%3Finstantiation%20.%0A%20%20%20%20%3Fid%20rico%3AhasIdentifierType%20vocab%3AinventoryNumber%20%3B%0A%20%20%20%20%20%20rico%3AtextualValue%20%3FnoInv%20.%0A%20%20%20%20FILTER%20(%3FnoInv%20%3D%20116)%20.%0A%0A%20%20%20%20%3Finstantiation%20rico%3AhasCarrierType%20vocab%3AdigitalFile%20%3B%0A%20%20%20%20%20%20dcterms%3Aformat%20%3FmimeType%20%3B%0A%20%20%20%20%20%20schema%3Aimage%20%3Ffile%20.%0A%20%20%20%20%3FmimeType%20skos%3AprefLabel%20%3Fformat%20.%0A%20%20%7D&endpoint=endpoint.php&requestMethod=POST&tabTitle=Query&headers=%7B%7D&contentTypeConstruct=application%2Fn-triples%2C*%2F*%3Bq%3D0.9&contentTypeSelect=application%2Fsparql-results%2Bjson%2C*%2F*%3Bq%3D0.9&outputFormat=table">Lien vers la requête &nearr;</a>

```plain
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX rico: <https://www.ica.org/standards/RiC/ontology#>
PREFIX schema: <https://schema.org/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX vocab: <http://vocab.qdmtl.ca/>

SELECT ?record ?noInv ?format ?file
  WHERE {
    ?record a rico:Record ;
      rico:hasOrHadIdentifier ?id ;
      rico:hasInstantiation ?instantiation .
    ?id rico:hasIdentifierType vocab:inventoryNumber ;
      rico:textualValue ?noInv .
    FILTER (?noInv = 116) .

    ?instantiation rico:hasCarrierType vocab:digitalFile ;
      dcterms:format ?mimeType ;
      schema:image ?file .
    ?mimeType skos:prefLabel ?format .
  }
```

### Les objets représentés par une photographie

La liste des photographies avec les bâtiments représentés.

<a href="http://qdmtl.ca/sparql/#query=PREFIX%20rico%3A%20%3Chttps%3A%2F%2Fwww.ica.org%2Fstandards%2FRiC%2Fontology%23%3E%0APREFIX%20qdmtl%3A%20%3Chttp%3A%2F%2Fonto.qdmtl.ca%2F%3E%0APREFIX%20owl%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2002%2F07%2Fowl%23%3E%0APREFIX%20ecrm%3A%20%3Chttp%3A%2F%2Ferlangen-crm.org%2Fcurrent%2F%3E%0APREFIX%20geo%3A%20%3Chttp%3A%2F%2Fwww.opengis.net%2Font%2Fgeosparql%23%3E%0A%0ASELECT%20%3Frecord%20%3Fbatiment%20%3Fpoint%0A%20%20WHERE%20%7B%0A%20%20%20%20%3Frecord%20a%20rico%3ARecord%20%3B%0A%20%20%20%20%20%20rico%3AhasOrHadMainSubject%20%3Fs%20.%0A%20%20%20%20%3Fs%20a%20qdmtl%3AE24_Building%20%3B%0A%20%20%20%20%20%20owl%3AsameAs%20%3Fbatiment%20.%0A%20%20%20%20OPTIONAL%20%7B%0A%20%20%20%20%20%20%3Fs%20ecrm%3AP53_has_former_or_current_location%20%3Fplace%20.%0A%20%20%20%20%20%20%3Fplace%20ecrm%3AP168_place_is_defined_by%20%3FgeoFeature%20.%0A%20%20%20%20%20%20%3FgeoFeature%20geo%3AasGeoJSON%20%3Fpoint%20.%0A%20%20%20%20%7D%0A%20%20%7D%0A&endpoint=endpoint.php&requestMethod=POST&tabTitle=Query&headers=%7B%7D&contentTypeConstruct=application%2Fn-triples%2C*%2F*%3Bq%3D0.9&contentTypeSelect=application%2Fsparql-results%2Bjson%2C*%2F*%3Bq%3D0.9&outputFormat=table&outputSettings=%7B%22pageSize%22%3A50%7D" target="_blank" >Lien vers la requête &nearr;</a>

```plain
PREFIX rico: <https://www.ica.org/standards/RiC/ontology#>
PREFIX qdmtl: <http://onto.qdmtl.ca/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX ecrm: <http://erlangen-crm.org/current/>
PREFIX geo: <http://www.opengis.net/ont/geosparql#>

SELECT ?record ?batiment ?point
  WHERE {
    ?record a rico:Record ;
      rico:hasOrHadMainSubject ?s .
    ?s a qdmtl:E24_Building ;
      owl:sameAs ?batiment .
    OPTIONAL {
      ?s ecrm:P53_has_former_or_current_location ?place .
      ?place ecrm:P168_place_is_defined_by ?geoFeature .
      ?geoFeature geo:asGeoJSON ?point .
    }
  }
```