# Queries

### QR1 - An speech is attributed to an author

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?speech ?creator  
WHERE {
    ?speech a speech:Speech ;
       dc:creator ?creator .
}
```

### QR2 - An speech has a date associated

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?speech ?date  
WHERE {
    ?speech a speech:Speech ;
       dc:created ?date .
}
```

### QR3 - An speech has a subject associated

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?speech ?subject  
WHERE {
    ?speech a speech:Speech ;
       dc:subject ?subject .
}
```

### QR4 - A political party has an ideology associated

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty ?ideology  
WHERE {
    ?pparty a speech:PoliticalParty ;
       speech:hasIdeology ?ideology .
}
```

### QR5 - Political parties have accounts in social networks

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty ?account  
WHERE {
    ?pparty a speech:PoliticalParty ;
       foaf:holdsAccount ?account .
}
```

### QR6 - A political party may have political manifestos

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty ?manifesto
WHERE {
    ?manifesto a speech:PoliticalPartyManifesto ;
       dc:creator ?pparty .
}
```

### QR7 - A political party may have political proposals

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty ?proposal
WHERE {
    ?manifesto a speech:PoliticalPartyManifesto ;
       dc:creator ?pparty ;
       dc:hasPart ?proposal .
}
```

### QR8 - A political party may have a hashtag associated to a speech

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?speech ?pparty ?hashtag
WHERE {
    ?pparty foaf:holdsAccount ?account .
    ?account sioc:creator_of ?speech .
    ?speech sioc:has_container ?hashtag .
}  
```

### QR9 - An speech may have interaction metrics

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?interactions
WHERE {
    ?speech schema:interactionStatistic ?interactions .
}   
```

### QR10 - Which are the posts of a political party related to the transport domain?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?speech_text
WHERE {
    ?pparty a speech:PoliticalParty ;
           foaf:name ?pparty_name ;
           foaf:holdsAccount ?account .
    ?account sioc:creator_of ?speech .
    ?speech schema:text ?speech_text .
    FILTER regex(lcase(str(?speech_text)), "transporte")
}     
```

### QR11 - A political party can be a subsidiary of another political party

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?sub_pparty_name ?pparty_name
WHERE {
    ?sub_pparty a speech:PoliticalParty ;
           foaf:name ?sub_pparty_name ;
           org:subOrganizationOf ?pparty .
   ?pparty a speech:PoliticalParty ;
           foaf:name ?pparty_name .
}     
```

### QR12 - Which political party wrote the longest thread in the 2021 campaign?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?thread (COUNT (?tweet) as ?count_tweet)
WHERE {
 ?thread a sioc:Thread ;
        sioc:container_of ?tweet .
 ?tweet a speech:Tweet ;
       dc:created ?date .
 FILTER(year(?date) = 2021)
}
GROUP BY ?thread ?date
ORDER BY DESC (?count_tweet)     
```

### QR13 - Which is the last tweet of the elections of Madrid in 2015?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?tweet_text ?date
WHERE {
 ?tweet a speech:Tweet ;
       dc:created ?date ;
       schema:text ?tweet_text .
 FILTER(?date < "2015-05-23"^^xsd:date)
}
ORDER BY DESC (?date)    
```

### QR14 - Which is the user most mentioned by a political party?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?mentioned_account (COUNT (?tweet) as ?count_mentions)
WHERE {
 ?tweet a speech:Tweet ;
       sioc:mentions ?mentioned_account ;
       schema:text ?tweet_text ;
       sioc:has_creator ?account .
 ?pparty foaf:holdsAccount ?account ;
     foaf:name ?pparty_name .
} GROUP BY ?pparty ?mentioned_account
```

### QR15 - Which is the user most quoted by a political party?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?quoted_account (COUNT (?tweet) as ?count_quotes)
WHERE {
 ?quoted_tweet a speech:Tweet ;
       siocq:quote_of ?tweet ;
       schema:text ?quoted_tweet_text ;
       sioc:has_creator ?quoted_account .
 ?tweet a speech:Tweet ;
       schema:text ?tweet_text ;
       sioc:has_creator ?account .
 ?pparty a speech:PoliticalParty ;
     foaf:holdsAccount ?account ;
     foaf:name ?pparty_name .
} GROUP BY ?pparty_name ?quoted_account
ORDER BY DESC (?count_quotes)
```
