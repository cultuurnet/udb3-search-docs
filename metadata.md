# Metadata

UiTdatabank v3 keeps track of offer creation en modification dates. This metdata can be queried with the following parameters:

* `createdFrom` \(ISO-8601 datetime, eg. "2017-04-01T12:08:01+01:00"\)
* `createdTo` \(ISO-8601 datetime, eg. "2017-04-20T12:08:01+01:00"\)

* `modifiedFrom` \(ISO-8601 datetime, eg. "2017-04-01T12:08:01+01:00"\)
* `modifiedTo` \(ISO-8601 datetime, eg. "2017-04-10T12:08:01+01:00"\)

**Note that the "+" sign should be encoded for URLs \(as %2B\)!** Otherwise it will be interpreted as whitespace and the given date time will be considered invalid.

## Looking for offers created or modified beyond and on a specific date

To find all offers that were modified or created beyond and on a specific date and time, use the `createdFrom` or `modifiedFrom` query parameters.

```
From: 2017-04-11T12:08:01+01:00
GET https://search.uitdatabank.be/offers/?createdFrom=2017-04-11T12:08:01%2B01:00
GET https://search.uitdatabank.be/offers/?modifiedFrom=2017-04-11T12:08:01%2B01:00
```

## Looking for offers created or modified before and on a specific date

To find all offers that were modified or created before and on a specific date and time, use the `createdTo` or `modifiedTo` query parameters.

```
To: 2017-04-11T12:08:01+01:00
GET https://search.uitdatabank.be/offers/?createdTo=2017-04-11T12:08:01%2B01:00
GET https://search.uitdatabank.be/offers/?modifiedTo=2017-04-11T12:08:01%2B01:00
```

## Only looking up places or events

The same parameters work for just places or events.

```
From: 2017-04-11T12:08:01+01:00
GET https://search.uitdatabank.be/event/?createdFrom=2017-04-11T12:08:01%2B01:00
GET https://search.uitdatabank.be/places/?createdFrom=2017-04-11T12:08:01%2B01:00

To: 2017-04-11T12:08:01+01:00
GET https://search.uitdatabank.be/event/?createdTo=2017-04-11T12:08:01%2B01:00
GET https://search.uitdatabank.be/places/?createdTo=2017-04-11T12:08:01%2B01:00
```