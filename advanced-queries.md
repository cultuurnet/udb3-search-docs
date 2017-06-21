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

Because of this, it is important to encapsulate field values that contain spaces, like this:

```
GET https://search.uitdatabank.be/offers/?q=zwembad labels:"uitpas leuven"
```

If we don't encapsulate `uitpas leuven` with quotes in the example above, `leuven` would become part of the free text search query instead of the label query.

Make sure to escape any quotes in the field values themselves if you encapsulate them!

For example, a valid label in UiTdatabank could be `"dag van de fiets"` \(with quotes!\).

To search for this label in an advanced query, it should be escaped and encapsulated like this:

```
GET https://search.uitdatabank.be/offers/?q=labels:"\"dag van de fiets\""
```

## Supported fields

| Field | Type | Comments |
| :--- | :--- | :--- |
| id | String | Looks for complete matches |
| calendarType | String | Looks for complete matches |
| dateRange | Date range | See [Date & time](/date.md) |
| availableRange | Date range | See [Availability](/availability.md) |
| workflowStatus | Enum \(String\) | See [Workflow status](/workflow-status.md) |
| name.{[lang](/languages.md)} | String |  |
| description.{[lang](/languages.md)} | String |  |
| languages | String | See [Languages](/languages.md) |
| terms.id | String | Looks for complete matches |
| terms.label | String | Looks for complete matches |
| labels | String | See [Labels](/labels.md). Looks for complete matches |
| price | Integer | See [Price](/price.md) |
| typicalAgeRange | Integer range | See [Age](/age.md) |
| audienceType | String | See [Audience type](/audience-type.md) |
| mediaObjectsCount | Integer | See [Media objects](/media-objects.md) |
| labels | String | Looks for complete matches |
| typicalAgeRange | Integer range |  |
| address.{[lang](/languages.md)}.addressCountry | Enum | See [Address](/address.md) |
| address.{[lang](/languages.md)}.addressLocality | String | See [Address](/address.md) |
| address.{[lang](/languages.md)}.postalCode | String | See [Address](/address.md) |
| address.{[lang](/languages.md)}.streetAddress | String | See [Address](/address.md) |
| regions | Enum | See [Region](/region.md) |
| location.id | String | Looks for complete matches |
| location.name.{[lang](/languages.md)} | String |  |
| location.terms.id | String | Looks for complete matches |
| location.terms.label | String | Looks for complete matches |
| location.labels | String | Looks for complete matches |
| organizer.id | String | Looks for complete matches |
| organizer.name.{[lang](/languages.md)} | String |  |
| organizer.labels | String | Looks for complete matches |
| creator | String | See [Creator](/creator.md) |
| createdRange | DateRange | See [Created and Modified](/created-and-modified.md) |
| modifiedRange | DateRange | See [Created and Modified](/created-and-modified.md) |

### Notes
* Wildcards (`*` or `?`) allowed to search for partial matches. (See [ElasticSearch documentation on syntax](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html\#query-string-syntax))
* `{lang}` should always be replaced by either a specific language (`nl`, `fr`, ...) or an **escaped** wildcard (`\*`)

## Examples

Searching by label `fietsen`

```
GET https://search.uitdatabank.be/offers/?q=labels:fietsen
```

Searching by all labels that start with `fiets`
```
GET https://search.uitdatabank.be/offers/?q=labels:fiets*
```

Searching by `postalCode` in the `nl` address:
```
GET https://search.uitdatabank.be/offers/?q=address.nl.postalCode:3000
```

Searching by `postalCode` in any address translation:
```
GET https://search.uitdatabank.be/offers/?q=address.\*.postalCode:3000
```

