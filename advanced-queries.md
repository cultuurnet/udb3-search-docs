# Advanced queries

The `q` parameter used for [free text search](/free-text-search.md) can also be used to execute more complex queries.

For example:

```
GET https://search.uitdatabank.be/offers/?q=(labels:uitpas* OR labels:paspartoe) AND typicalAgeRange:[* TO 12]
```

The syntax is based on the Lucene query syntax. More info can be found in the ElasticSearch documentation:  
[https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html\#query-string-syntax](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax)

## Mixing free text search and advanced queries

As per the ElasticSearch documentation, it is possible to mix free text search and advanced queries.

For example:

```
GET https://search.uitdatabank.be/offers/?q=zwembad labels:uitpas*
```

This will execute a free text search for the term `zwembad`, combined with a label search for `uitpas*`.

Because of this, it is important to encapsulate field values that contain spaces, like so:

```
GET https://search.uitdatabank.be/offers/?q=zwembad labels:"uitpas leuven"
```

If we don't encapsulate `uitpas leuven` with quotes in the example above, `leuven` would become part of the free text search query instead of the label query.

Make sure to escape any quotes in the field values themselves if you encapsulate them!

For example, a valid label in UiTDatabank could be `"dag van de fiets"` \(with quotes!\).

To search for this label in an advanced query, it should be escaped and encapsulated like this:

```
GET https://search.uitdatabank.be/offers/?q=labels:"\"dag van de fiets\""
```

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

