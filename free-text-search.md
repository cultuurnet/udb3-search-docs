# Free text search

Using the `q` URL parameter, you can search for text across multiple pre-defined fields:

```
GET https://search.uitdatabank.be/offers/?q=dit is een test
```

## Fields

The following fields will be searched when using the `q` parameter with free text:

`id`, `name`, `description`, `labels`, `terms.id`, `terms.label`, `performer.name`, `addressLocality`, `postalCode`, `streetAddress`, `location.id`, `location.name`, `organizer.id`, `organizer.name`

**Important notes:**

* IDs only return results if the complete ID is given in the free text input.
* Name & description fields are translatable, but currently only the NL translations are searched when using free text search.
* Searching for a part of a word does not work yet. For example, searching for "Fiets" will not return an event with the title "Fietsen langs de Dijle".

## Operators

By default the `OR` operator is used in between multiple given words.

So the query `wandelen fietsen dijle` actually becomes `wandelen OR fietsen OR dijle`.

It is possible to define the operator you want to use in the query itself.  
You could, for example, search for:

```
GET https://search.uitdatabank.be/offers/?q=(wandelen OR fietsen) AND dijle
```

See the [Query String Query syntax for ElasticSearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax) for more info, or more documentation on [advanced queries](/advanced-queries.md).

