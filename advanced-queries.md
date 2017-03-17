# Advanced queries

The `q` parameter used for [free text search](/free-text-search.md) can also be used to execute more complex queries.

For example:

```
GET https://search.uitdatabank.be/offers/?q=(labels:uitpas* OR labels:paspartoe) AND typicalAgeRange:[* TO 12]
```

The syntax is based on the Lucene query syntax. More info can be found in the ElasticSearch documentation:  
[https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html\#query-string-syntax](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax)

## Supported fields

| Field | Type | Comments |
| :--- | :--- | :--- |
| id | String | Complete matches only\* |
| name.nl | String |  |
| name.fr | String |  |
| name.de | String |  |
| name.en | String |  |
| labels | String | Complete matches only\* |
| typicalAgeRange | Integer range |  |
| addressLocality | String |  |
| postalCode | String | Currently only supports numerical codes \(eg. 3000\) |
| streetAddress | String |  |
| location.id | String | Complete matches only\* |
| location.name.nl | String |  |
| location.name.fr | String |  |
| location.name.de | String |  |
| location.name.en | String |  |
| organizer.id | String | Complete matches only\* |
| organizer.name.nl | String |  |
| organizer.name.fr | String |  |
| organizer.name.de | String |  |
| organizer.name.fr | String |  |

\* Wildcards allowed

