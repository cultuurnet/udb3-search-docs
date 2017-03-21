# Languages

All documents created in UiTdatabank are available in Dutch \(NL\). Besides Dutch, content editors can translate their documents in French \(FR\), German \(DE\) and English \(EN\).

To limit your results to documents that have translations for a specific language, you can use the `languages` URL parameter, or the `languages` field in [advanced queries](/advanced-queries.md).

Allowed values for both are:

* nl \(or NL\)
* fr \(or FR\)
* de \(or DE\)
* en \(or EN\)

## Url parameter

An example to get results that have a French translation:

```
GET https://search.uitdatabank.be/offers/?languages[]=fr
```

You can repeat this parameter to filter by multiple languages \(note that this uses the `AND` operator, so you will only get results that have translations for both languages\).

```
GET https://search.uitdatabank.be/offers/?languages[]=fr&languages[]=de
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `languages` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=languages:fr OR languages:de
```

Note that while you can combine this with [free text search](/free-text-search.md), you will probably not get the intended results:

```
GET https://search.uitdatabank.be/offers/?q=languages:en the worst band ever
```

In the example above we're filtering documents to only search through those that have an EN translation and one or more matches with the words "the worst band ever". However, the word "worst" is also a Dutch word, and while we filtered the documents to only return results that have an English translation, the free text search will still look for text matches in all available languages on those \(filtered\) documents. So we might have an event that includes the word "worst" in Dutch and that also has an English translation, and it would be a valid result.

To fix this, you should use the `textLanguage` parameter as described in the [free text search](/free-text-search.md) documentation.

