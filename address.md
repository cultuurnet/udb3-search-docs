# Address

You can filter by address-related fields using two methods:

* URL parameter
* Advanced queries

## URL parameter

Currently, the only URL parameter for address fields is `postalCode`.

Example usage:

```
GET https://search.uitdatabank.be/offers/?postalCode=3000
```

## Advanced queries

Using advanced queries, you can not only filter by `postalCode`, but also by `addressLocality` and `streetAddress`.

For example:

```
GET https://search.uitdatabank.be/offers/?q=postalCode:3000 AND addressLocality:Leuven AND streetAddress:Bondgenotenlaan*
```

All address fields allow wildcards and/or complete matches \(using quotes\) like regular string fields.

Note that `streetAddress` also includes the street number, so make sure to use a wildcard to filter by a street name!

For more information, see [advanced queries](/advanced-queries.md).



