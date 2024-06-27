# Queries



### R1: Political discourse has different metrics (views, listeners, attendees, likes, etc.)

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?metrics where { 
    ?s a podio:Discourse;
       schema:interactionStatistic ?stats.
    ?stats a schema:InteractionCounter;
        schema:interactionType ?metrics.
}
```

### R2: A speech is published by an agent who may not be the creator of the speech itself.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?s ?publisher ?creator where { 
    ?s a podio:Discourse;
         terms:publisher ?publisher;
         terms:creator ?creator.
    FILTER(?publisher != ?creator)
}
```

### R3: A speech has an audience. That is, the group of people who have received the message.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?audience where { 
    ?s a podio:Discourse;
         terms:audience ?audience.
}
```

### R4: A speech has a target. That is, the group of people to whom the message is intended. This group does not necessarily have to coincide with the audience.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?audience ?target where { 
    ?s a podio:Discourse;
         terms:audience ?audience;
         podio:hasTarget ?target.
    FILTER(?target != ?audience)
}
```

### R5: Both speeches and party manifestos are written in one or more languages.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?language where { 
    ?s a podio:Discourse;
         terms:language ?language.
}
```

### R6: Both speeches and party manifestos have a publication date.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select ?date where { 
    ?s a podio:Discourse;
         terms:created ?date.
} Limit 10
```

### R7: Both speeches and party manifestos can have a description.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select ?desc where { 
    VALUES ?clases {
        podio:Discourse
        podio:PartyManifesto
    }
    ?s a ?clases;
        terms:description ?desc.
} Limit 10
```

### R8: Both speeches and party manifestos have an ideology.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?ideology ?ideologyLabel where { 
    VALUES ?clases {
        podio:Discourse
        podio:PartyManifesto
    }
    ?s a ?clases;
        podio:ideology ?ideology.
    
    # Query Wikidata using federation
    SERVICE <https://query.wikidata.org/sparql> {
        ?ideology rdfs:label ?ideologyLabel.
        FILTER(LANGMATCHES(LANG(?ideologyLabel), "en")).
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
    }
    
} Limit 3
```

### R9: Both speeches and party manifestos should reference the source of information in the official channel.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?sources where { 
    VALUES ?clases {
        podio:Discourse
        podio:PartyManifesto
    }
    ?s a ?clases;
        terms:source ?sources.
    
    
} Limit 3
```

### R10: A party manifesto has a textual content extracted from a document.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?content ?sources where { 
    ?s a podio:PartyManifesto;
        podio:content ?content;
        terms:source ?sources.

} Limit 3
```

### R11: A party manifesto proposes a candidate for political position.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?candidate ?candidateLabel ?sources where { 
    ?s a podio:PartyManifesto;
        podio:proposesCandidate ?candidate;
        terms:source ?sources.
    
    # Query Wikidata using federation
    SERVICE <https://query.wikidata.org/sparql> {
        ?candidate rdfs:label ?candidateLabel.
        FILTER(LANGMATCHES(LANG(?candidateLabel), "en")).
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
    }
    
} Limit 3
```

### R12: A party manifesto is published by the political party that drafts it.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?publisher ?publisherLabel ?sources where { 
    ?s a podio:PartyManifesto;
        terms:publisher ?publisher.
    
    # Query Wikidata using federation
    SERVICE <https://query.wikidata.org/sparql> {
        ?publisher rdfs:label ?publisherLabel.
        FILTER(LANGMATCHES(LANG(?publisherLabel), "en")).
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
    }
    
} Limit 3
```

### R13: A party manifesto has several policy proposals.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?pmanifest ?proposal ?proposalContent where { 
    ?pmanifest a podio:PartyManifesto.
    
    ?proposal terms:isPartOf ?pmanifest;
              podio:content ?proposalContent.
    
    
} Limit 3
```

### R14: Political speech can have content in any format, both text and multimedia.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?content where { 
    ?speech a podio:Discourse;
              podio:content ?content.
    
} Limit 3
```

### R15: There are speeches that are shared in digital communities and allow direct interaction with the audience.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?content where { 
    ?speech a podio:Conversational;
              podio:content ?content.
    
} Limit 3
```

### R16: There are speeches that may be shared on channels that do not allow interaction with the audience.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?content where { 
    ?speech a podio:Expository;
              podio:content ?content.
    
} Limit 3
```

### R17: Speeches shared in digital communities should implement the basic mechanics of interaction (reply, mention, thread, hashtags, post, repost, follow, and share content).

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?p where { 
    ?speech a podio:Conversational;
              ?p ?o.
    
} 
```

### R18: The laws approved by political parties and their electoral proposals are speeches that do not allow for direct interaction with the audience.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select DISTINCT ?speech where { 
    VALUES ?clases {
        podio:PolicyProposal
        podio:ApprovedPolicy
    }
    ?speech a ?clases;
              a podio:Expository.
    
} 
```

### R19: It should be possible to explore the existing laws in the Lynx knowledge graph.

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT (?juris as ?jurisdiction) ?year ?s_text
WHERE {
    
        SERVICE <http://sparql.lynx-project.eu/> {
            ?s a lkg:Legislation ;
                nif:isString ?s_text ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?date ;
                eli:id_local ?id ;
                terms:source ?source .
        }
    
    BIND(year(?date) as ?year)
    
} LIMIT 10
```

### CQ1: What are the names of all political parties (in Spanish and English), when were they created and what is their ideology?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>


select (SAMPLE(?nameEN) as ?PoliticalPartyEN) (SAMPLE(?nameES) as ?PoliticalPartyES) (SAMPLE(?creation) as ?creationDate) (SAMPLE(?ideologyLabel) as ?ideologyLabel)
where {

    ?s a foaf:Agent.

    # Query Wikidata using federation
    SERVICE <https://query.wikidata.org/sparql> {
      ?s  rdfs:label ?nameEN;
          rdfs:label ?nameES;
          wdt:P31/wdt:P279* wd:Q7278; # instance of Political Party
          wdt:P571 ?creation;         # date of creation
          wdt:P1387 ?ideology.        # ideological alignment
      FILTER(LANGMATCHES(LANG(?nameEN), "en")). # Name in english
      FILTER(LANGMATCHES(LANG(?nameES), "es")). # Name in spanish

      ?ideology rdfs:label ?ideologyLabel.
      FILTER(LANGMATCHES(LANG(?ideologyLabel), "en")). # Ideology in english
    }
} group by ?s
order by asc(UCASE(str(?PoliticalPartyEN)))
```

### CQ2: Which social media accounts does the PP have?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select ?socialMediaUserName ?socialMedia where {
    wd:Q185088 foaf:holdsAccount ?accounts .
    ?accounts foaf:accountServiceHomepage ?socialMedia;
              foaf:accountName ?socialMediaUserName.
}
```

### CQ3: How many posts have political parties published on each of their social media accounts?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>


select (SAMPLE(?name) AS ?PoliticalParty) ?socialMedia (?accname AS ?accountName) (COUNT(DISTINCT(?discourse)) AS ?numberOfpost)
where {
    ?discourse a podio:Discourse;
                    sioc:has_creator ?account.
    ?s a foaf:Agent;
        foaf:holdsAccount ?account .
    ?account foaf:accountServiceHomepage ?socialMedia;
                foaf:accountName ?accname.

    # Query Wikidata using federation
    SERVICE <https://query.wikidata.org/sparql> {
        ?s rdfs:label ?name;
                    wdt:P31/wdt:P279* wd:Q7278.
        FILTER(LANGMATCHES(LANG(?name), "en")).
    }
}  group by ?socialMedia ?accname
order by asc(UCASE(str(?name)))
```

### CQ4: Which account and on which social media network is the most mentioned by each politician and political party?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>


SELECT (SAMPLE(?name) as ?agentName) (SAMPLE(?socialMedia) as ?socialMedia) (SAMPLE(?mentioned_account) as ?maxMentionedAccount) (MAX(?count_mentions) as ?numberOfTimesMentioned) WHERE{
    
    SELECT DISTINCT ?pparty ?name ?socialMedia ?mentioned_account (COUNT (?tweet) as ?count_mentions)
    WHERE {
     ?tweet a podio:Discourse ;
           sioc:mentions ?mentioned_account ;
           podio:content ?tweet_text ;
           sioc:has_creator ?account .
        ?pparty foaf:holdsAccount ?account.
        ?account foaf:accountServiceHomepage ?socialMedia.


        # Query Wikidata using federation
        SERVICE <https://query.wikidata.org/sparql> {
          ?pparty rdfs:label ?name.
          FILTER(LANGMATCHES(LANG(?name), "en")).
          SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
        }
    } GROUP BY ?pparty ?mentioned_account ?name ?socialMedia
    
} group by ?pparty 
ORDER BY DESC(?mentions)
```

### CQ5: What were the ten most used hashtags in political speech during 2020?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>



Select ?hashtagName (MAX(?count) as ?usedTimes) where{
    select ?hashtagName (count(distinct ?s) as ?count) where {
        ?s a podio:Discourse;
             podio:content ?text;
             terms:creator ?authAcc;
             sioc:has_container ?container;
             terms:created ?date .
        ?container a podio:Hashtag;
                terms:identifier ?hashtagName.

        
    FILTER(year(?date) = 2020)
    } GROUP BY ?hashtagName 

} group by ?authAcc ?hashtagName
Order BY desc (?usedTimes) LIMIT 10
```

### CQ6: Which political party has generated the most speeches?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select (?name as ?PoliticalParty) ?numberOfDiscourses where { 

    select ?s
        (SAMPLE(?name) AS ?name)
        (COUNT(DISTINCT(?discourse)) AS ?numberOfDiscourses) 
    where { 
        ?discourse a podio:Discourse;
                terms:creator ?s.
        ?s a foaf:Agent;
                terms:identifier ?ids.
        
        BIND(IRI(CONCAT("http://www.wikidata.org/entity/", str(?ids))) AS ?wikidataIri) .

        # Query Wikidata using federation
        SERVICE <https://query.wikidata.org/sparql> {
          ?wikidataIri rdfs:label ?name;
                       wdt:P31/wdt:P279* wd:Q7278.
          FILTER(LANGMATCHES(LANG(?name), "en")).
          SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
        }
    }  group by ?s
}ORDER BY DESC(?numberOfDiscourses)
LIMIT 1
```

### CQ7: How many references to the LGTBI community have been made in each year's political speeches by the different political agents?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select (SAMPLE(?name) as ?name) ?timeslice (count(distinct ?s) as ?count) where {
    ?s a podio:Discourse;
         podio:content ?text;
         terms:creator ?auth;
         terms:created ?date .
    BIND(year(?date) as ?timeslice) .
    filter contains(lcase(str(?text)),"lgtbi")
    
    ?auth terms:identifier ?ids.
    BIND(IRI(CONCAT("http://www.wikidata.org/entity/", str(?ids))) AS ?wikidataIri) .

    SERVICE <https://query.wikidata.org/sparql> {
                ?wikidataIri rdfs:label ?name.
                FILTER(LANGMATCHES(LANG(?name), "en")).
                SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
            }
    
    } GROUP BY ?timeslice ?auth
ORDER BY DESC (?count)
```

### CQ8: What were the five most shared speeches?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

select ?text (?int as ?numberOfTimeShared) where { 
    ?s a podio:Discourse;
        schema:interactionStatistic ?stats;
        terms:creator ?auth;
        podio:content ?text.
    
    ?stats schema:interactionType schema:ShareAction;
           schema:userInteractionCount ?number.

    BIND( abs(xsd:float(?number)) as ?int)


} 
ORDER BY DESC (?int)
LIMIT 5
```

### CQ9: What are the ten authorities that have approved the most legislations?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>


SELECT ?jurisdiction (?auth as ?authority) (MAX(?numberOfLegislations) AS ?numberOfLegislations)
WHERE {
    SELECT (?juris as ?jurisdiction) ?auth (COUNT(DISTINCT(?id)) AS ?numberOfLegislations)
    WHERE {
        {
            ?s a podio:ApprovedPolicy ;
                podio:content ?s_text ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?date ;
                eli:id_local ?id ;
                lkg:hasAuthority ?auth ;
                terms:source ?source .
                
        }
        UNION{
            SERVICE <http://sparql.lynx-project.eu/> {
                ?s a lkg:Legislation ;
                    nif:isString ?s_text ;
                    lkg:metadata ?metadata .
                ?metadata eli:jurisdiction ?juris ;
                    eli:version_date ?date ;
                    eli:id_local ?id ;
                    lkg:hasAuthority ?auth ;
                    terms:source ?source .
            }
        }
        BIND(year(?date) as ?year)
    } group by ?juris ?auth
    
} group by ?jurisdiction ?auth
ORDER BY DESC(?numberOfLegislations) Limit 10
```

### CQ10: How much legislations are available for each jurisdiction and year?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT (?juris as ?jurisdiction) ?year (COUNT(DISTINCT(?id)) AS ?numberOfLegislations)
WHERE {
    {
        ?s a lkg:Legislation ;
            nif:isString ?s_text ;
            lkg:metadata ?metadata .
        ?metadata eli:jurisdiction ?juris ;
            eli:version_date ?date ;
            eli:id_local ?id ;
            terms:source ?source .
    }
    UNION{
        SERVICE <http://sparql.lynx-project.eu/> {
            ?s a lkg:Legislation ;
                nif:isString ?s_text ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?date ;
                eli:id_local ?id ;
                terms:source ?source .
        }
    }
    BIND(year(?date) as ?year)
    
} group by ?juris ?year
```

### CQ11: What is the year in which more legislations were approved by each jurisdiction?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT ?jurisdiction (SAMPLE(?year) as ?year) (MAX(?numberOfLegislations) AS ?numberOfLegislations)
WHERE {
    SELECT (?juris as ?jurisdiction) ?year (COUNT(DISTINCT(?id)) AS ?numberOfLegislations)
    WHERE {
        {
            ?s a lkg:Legislation ;
                nif:isString ?s_text ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?date ;
                eli:id_local ?id ;
                terms:source ?source .
        }
        UNION{
            SERVICE <http://sparql.lynx-project.eu/> {
                ?s a lkg:Legislation ;
                    nif:isString ?s_text ;
                    lkg:metadata ?metadata .
                ?metadata eli:jurisdiction ?juris ;
                    eli:version_date ?date ;
                    eli:id_local ?id ;
                    terms:source ?source .
            }
        }
        BIND(year(?date) as ?year)

    } group by ?juris ?year
} group by ?jurisdiction
```

### CQ12: What has been the latest legislation approved by each jurisdiction?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>



SELECT (?juris as ?jurisdiction) (MAX(?date) AS ?date) (SAMPLE(?id) AS ?id) (SAMPLE(?source) AS ?source) (SAMPLE(?s_text) AS ?content) 
WHERE {
    {
        ?s a lkg:Legislation ;
            nif:isString ?s_text ;
            lkg:metadata ?metadata .
        ?metadata eli:jurisdiction ?juris ;
            eli:version_date ?date ;
            eli:id_local ?id ;
            terms:source ?source .
    }
    UNION{
        SERVICE <http://sparql.lynx-project.eu/> {
            ?s a lkg:Legislation ;
                nif:isString ?s_text ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?date ;
                eli:id_local ?id ;
                terms:source ?source .
        }
    }    
} group by ?juris
```

### CQ13: What was the last legislation approved by the government of the Community of Madrid?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>



SELECT ?auth (SAMPLE(?juris) as ?jurisdiction) (MAX(?date) AS ?date) (SAMPLE(?id) AS ?id) (SAMPLE(?source) AS ?source) (SAMPLE(?s_text) AS ?content) 
WHERE {
    {
        ?s a lkg:Legislation ;
            nif:isString ?s_text ;
            lkg:metadata ?metadata .
        ?metadata eli:jurisdiction ?juris ;
            eli:version_date ?date ;
            eli:id_local ?id ;
            lkg:hasAuthority ?auth;
            terms:source ?source .
    }
    UNION{
        SERVICE <http://sparql.lynx-project.eu/> {
            ?s a lkg:Legislation ;
                nif:isString ?s_text ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?date ;
                eli:id_local ?id ;
                lkg:hasAuthority ?auth;
                terms:source ?source .
        }
    } FILTER(?auth=<https://www.wikidata.org/wiki/Q578788>)
}GROUP BY ?auth
```

### CQ14: What is the longest legislation?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>



SELECT (SAMPLE(?juris) as ?jurisdiction) (SAMPLE(?date) AS ?date) (SAMPLE(?id) AS ?id) 
(SAMPLE(?source) AS ?source) (MAX(STRLEN(?s_text)) AS ?len_s_text) (SAMPLE(?s_text) as ?content)
WHERE {
    {
        ?s a lkg:Legislation ;
            nif:isString ?s_text ;
            lkg:metadata ?metadata .
        ?metadata eli:jurisdiction ?juris ;
            eli:version_date ?date ;
            eli:id_local ?id ;
            terms:source ?source .
    }
    UNION{
        SERVICE <http://sparql.lynx-project.eu/> {
            ?s a lkg:Legislation ;
                nif:isString ?s_text ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?date ;
                eli:id_local ?id ;
                terms:source ?source .
        }
    } 
}
```

### CQ15: How much legislative and propaganda activity have the spanish leftist parties had during their governments in each legislature?

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcam: <http://purl.org/dc/dcam/>
PREFIX eli: <http://data.europa.eu/eli/ontology#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX lkg: <http://lkg.lynx-project.eu/def/>
PREFIX nif-core: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX podio: <http://w3id.org/podio#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX schema: <http://schema.org/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX terms: <http://purl.org/dc/terms/>
PREFIX vann: <http://purl.org/vocab/vann/>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX nif: <http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX ps: <http://www.wikidata.org/prop/statement/>
PREFIX p: <http://www.wikidata.org/prop/>
PREFIX pq: <http://www.wikidata.org/prop/qualifier/>

SELECT ?ppartyLabel (?startTime as ?inGovernmentSince) (?endTime AS ?inGovernmentUntil) ?legislatureLabel ?legislatureStartTime ?legislatureEndTime (COUNT(DISTINCT ?message) AS ?discourses) (COUNT(DISTINCT ?legis) AS ?legislations)
WHERE {
    BIND(wd:Q138198 AS ?pparty). #PSOE
    {
        SELECT (NOW() AS ?currentTime) WHERE {}
    }
    {
        SERVICE <https://query.wikidata.org/sparql> {
            ?pparty rdfs:label ?ppartyLabel.
            FILTER(LANGMATCHES(LANG(?ppartyLabel), "es")).
            wd:Q29 p:P6 ?statement.                                                  # España (Q29) con una declaración de jefe de gobierno (P6)
            ?statement ps:P6 ?primeMinister.                                         # Primer ministro (P6)
            ?statement pq:P580 ?startTime.                                           # Fecha de inicio del puesto
            OPTIONAL { ?statement pq:P582 ?possibleEndTime. }                        # Fecha de fin del puesto (opcional)
            ?primeMinister wdt:P102 ?pparty.                                         # Partido político del primer ministro es PSOE (Q138198)
            BIND(IF(BOUND(?possibleEndTime), ?possibleEndTime, ?currentTime) AS ?endTime)   # Asigna NOW() si ?possibleEndTime no está definido


          ?legislature p:P31 ?legislatureStatement.  # Declaración que la identifica como legislatura
          ?legislatureStatement ps:P31 wd:Q15238777; # Instancia de 'legislatura'
                                pq:P642 wd:Q219692.  # Qualificador: Cortes Generales

          ?legislature wdt:P17 wd:Q29;                 # País: España
                       wdt:P580 ?legislatureStartTime; # Fecha de inicio
                       rdfs:label ?legislatureLabel.
          FILTER(LANGMATCHES(LANG(?legislatureLabel), "es")).

          OPTIONAL { ?legislature wdt:P582 ?possibleLegislatureEndTime. }  # Posible fecha de fin
          BIND(IF(BOUND(?possibleLegislatureEndTime), ?possibleLegislatureEndTime, ?currentTime) AS ?legislatureEndTime)   # Asigna NOW() si ?possibleEndTime no está definido

          FILTER (
              (?legislatureStartTime >= ?startTime && ?legislatureStartTime <= ?endTime) ||
              (?legislatureEndTime >= ?startTime && ?legislatureEndTime <= ?endTime) ||
              (?startTime >= ?legislatureStartTime && ?endTime <= ?legislatureEndTime)
            )
        }
    }

    optional{
        ?message a podio:Discourse;
                terms:creator ?pparty;
                dc:date ?created.

        FILTER NOT EXISTS { ?message rdf:type podio:ApprovedPolicy }


        FILTER (
            (?created >= ?startTime && ?created <= ?endTime) &&
            (?created >= ?legislatureStartTime && ?created <= ?legislatureEndTime)
        )
    }

    optional{
        {
            ?legis a lkg:Legislation ;
                lkg:metadata ?metadata .
            ?metadata eli:jurisdiction ?juris ;
                eli:version_date ?legisDate .
        }
        UNION{
            SERVICE <http://sparql.lynx-project.eu/> {
                ?legis a lkg:Legislation ;
                    lkg:metadata ?metadata .
                ?metadata eli:jurisdiction ?juris ;
                    eli:version_date ?legisDate.
            }
        }
        FILTER (
            (?juris = "ES") &&
            (?legisDate >= ?startTime && ?legisDate <= ?endTime) &&
            (?legisDate >= ?legislatureStartTime && ?legisDate <= ?legislatureEndTime)
        )
    }

}group by ?pparty ?ppartyLabel ?startTime ?endTime ?legislatureLabel ?legislatureStartTime ?legislatureEndTime
ORDER BY desc(?legislatureStartTime)
Limit 5
```
