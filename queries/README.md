# Queries

### QR1 - An speech is attributed to an author

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?creator_name ?speech ?speech_text
WHERE {
    ?speech a speech:Speech ;
       schema:text ?speech_text ;
       ?p_creator ?creator .
    ?creator ?p_name ?creator_name .
   VALUES ?p_creator {dc:creator sioc:has_creator}
   VALUES ?p_name {foaf:name sioc:name}
}
```

### QR2 - An speech has a date associated

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?date  ?speech ?speech_text
WHERE {
    ?speech a speech:Speech ;
       schema:text ?speech_text ;
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

SELECT DISTINCT ?subject  ?speech ?speech_text
WHERE {
    ?speech a speech:Speech ;
        dc:hasPart ?proposal .
    ?proposal dc:subject ?subject ;
       schema:text ?speech_text .
}
```

### QR4 - A political party has an ideology associated

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?ideology  
WHERE {
    ?pparty a speech:PoliticalParty ;
       foaf:name ?pparty_name ;
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

SELECT DISTINCT ?pparty_name ?account  
WHERE {
    ?pparty a speech:PoliticalParty ;
       foaf:name ?pparty_name ;
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

SELECT DISTINCT ?pparty_name ?manifesto
WHERE {
    ?manifesto a speech:PoliticalPartyManifesto ;
       dc:creator ?pparty .
    ?pparty a speech:PoliticalParty ;
       foaf:name ?pparty_name .
}
```

### QR7 - A political party may have political proposals

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?proposal ?proposal_text
WHERE {
    ?manifesto a speech:PoliticalPartyManifesto ;
       dc:creator ?pparty ;
       dc:hasPart ?proposal .
    ?proposal schema:text ?proposal_text .
    ?pparty a speech:PoliticalParty ;
       foaf:name ?pparty_name .
}
```

### QR8 - A political party may have a hashtag associated to a speech

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?hashtag_label ?speech_text
WHERE {
    ?pparty foaf:holdsAccount ?account ;
       foaf:name ?pparty_name .
    ?account sioc:creator_of ?speech .
    ?speech sioc:has_container ?hashtag ;
       schema:text ?speech_text .
    ?hashtag rdfs:label ?hashtag_label.
}   
```

### QR9 - An speech may have interaction metrics

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?speech ?interaction_type ?interaction_count ?speech_text
WHERE {
    ?speech schema:interactionStatistic ?interactions ;
       schema:text ?speech_text .
    ?interactions schema:interactionType ?interaction_type;
       schema:userInteractionCount ?interaction_count .
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
PREFIX org: <http://www.w3.org/ns/org#>

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
} GROUP BY ?pparty_name ?mentioned_account
```

### QR15 - Which is the user most quoted by a political party?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX siocq: <http://rdfs.org/sioc/quotes#>
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

### QR16 - Which is the tweet with more quotes of a political party?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX siocq: <http://rdfs.org/sioc/quotes#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?quoted_tweet_text (COUNT (?tweet) as ?count_quotes)
WHERE {
 ?quoted_tweet a speech:Tweet ;
       siocq:quote_of ?tweet ;
       schema:text ?quoted_tweet_text ;
       sioc:has_creator ?quoted_account .
 ?tweet a speech:Tweet .
 ?pparty a speech:PoliticalParty ;
     foaf:holdsAccount ?quoted_account ;
     foaf:name ?pparty_name .
} GROUP BY ?pparty_name ?quoted_tweet_text
ORDER BY DESC (?count_quotes)
```

### QR17 - Which are the tweets and users quoted by at least two political parties?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX siocq: <http://rdfs.org/sioc/quotes#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?quoted_tweet_text ?quoted_account
WHERE {
 ?quoted_tweet a speech:Tweet ;
       siocq:quote_of ?tweet ;
       schema:text ?quoted_tweet_text ;
       sioc:has_creator ?quoted_account .
 ?tweet a speech:Tweet ;
       sioc:has_creator ?account .
 ?pparty a speech:PoliticalParty ;
      foaf:holdsAccount ?account .
} GROUP BY ?quoted_tweet_text ?quoted_account
HAVING (COUNT (DISTINCT ?pparty) > 1)
```

### QR18 - Which are the tweets and users retweeted by at least two political parties?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?tweet_text ?ret_account
WHERE {
 ?tweet a speech:Tweet ;
       schema:text ?tweet_text ;
       sioc:has_creator ?ret_account .
 ?pparty a speech:PoliticalParty ;
      foaf:holdsAccount ?account .
 ?account speech:retweets ?tweet .
} GROUP BY ?tweet_text ?ret_account
HAVING (COUNT (DISTINCT ?pparty) > 1)
```

### QR19 - Which are the tweets of a political party retweeted by another political party?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?ret_pparty_name ?pparty_name ?tweet_text
WHERE {
 ?tweet a speech:Tweet ;
       schema:text ?tweet_text ;
       sioc:has_creator ?ret_account .
 ?pparty a speech:PoliticalParty ;
      foaf:name ?pparty_name ;
      foaf:holdsAccount ?account .
 ?ret_pparty a speech:PoliticalParty ;
      foaf:name ?ret_pparty_name ;
     foaf:holdsAccount ?ret_account .
 ?account speech:retweets ?tweet .
}
```

### QR20 - Which is the hashtag most tweeted by a political party in the 2019 Madrid elections?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?hashtag_label (COUNT (?tweet) as ?count_hashtag)
WHERE {
    ?pparty a speech:PoliticalParty ;
      foaf:name ?pparty_name ;
      foaf:holdsAccount ?account .
    ?tweet a speech:Tweet ;
       sioc:has_container ?hashtag ;
       sioc:has_creator ?account ;
       dc:created ?date .
    ?hashtag a speech:Hashtag ;
       rdfs:label ?hashtag_label .
    FILTER(year(?date) = 2019)
} GROUP BY ?pparty_name ?hashtag_label
ORDER BY DESC (?count_hashtag)
```

### QR21 - Which is the hashtag most retweeted by a political party in the 2019 Madrid elections?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name ?hashtag_label (COUNT (?tweet) as ?count_hashtag)
WHERE {
    ?pparty a speech:PoliticalParty ;
      foaf:name ?pparty_name ;
      foaf:holdsAccount ?account .
    ?account speech:retweets ?tweet .
    ?tweet a speech:Tweet ;
       sioc:has_container ?hashtag ;
       dc:created ?date .
    ?hashtag a speech:Hashtag ;
       rdfs:label ?hashtag_label .
    FILTER(year(?date) = 2019)
} GROUP BY ?pparty_name ?hashtag_label
ORDER BY DESC (?count_hashtag)
```

### QR22 - Which is the political party that has tweeted the most in 2021?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name (COUNT (?tweet) as ?count_tweets)
WHERE {
    ?pparty a speech:PoliticalParty ;
      foaf:name ?pparty_name ;
      foaf:holdsAccount ?account .
    ?tweet a speech:Tweet ;
       dc:created ?date ;
       sioc:has_creator ?account.
    FILTER(year(?date) = 2021)
} GROUP BY ?pparty_name
ORDER BY DESC (?count_tweets)
```

### QR23 - Which is the political party that has been retweeted the most in 2021?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?pparty_name (COUNT (?tweet) as ?count_retweets)
WHERE {
    ?pparty a speech:PoliticalParty ;
      foaf:name ?pparty_name ;
      foaf:holdsAccount ?ret_account .
    ?account speech:retweets ?tweet .
    ?tweet a speech:Tweet ;
       dc:created ?date ;
       sioc:has_creator ?ret_account.
    FILTER(year(?date) = 2021)
} GROUP BY ?pparty_name
ORDER BY DESC (?count_retweets)
```

### QR24 - How have ODS changed in the proposals of a manifesto of a political party?

```
PREFIX speech: <http://w3id.org/speech#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX sioc: <http://rdfs.org/sioc/ns#>
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX schema: <http://schema.org/>

SELECT DISTINCT ?manifesto_id ?sdg (COUNT (?proposal) as ?count_proposal)
WHERE {
    ?manifesto a speech:PoliticalPartyManifesto ;
            dc:identifier ?manifesto_id ;
            dc:hasPart ?proposal .
    ?proposal dc:subject ?sdg .
} GROUP BY ?manifesto_id ?sdg
ORDER BY DESC (?sdg)
```
