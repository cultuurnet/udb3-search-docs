# Date & time

Using Search API v3, you can easily search all events that occur within a given time frame, and all places that are open within that same time frame.

## Url parameters

To search by date and time, you can use the `dateFrom` and `dateTo` URL parameters. Each one accepts an `ISO-8601` datetime, for example `2017-04-11T12:08:01+01:00`. A timezone offset is required, and will be taken into account. Both parameters are optional and have no default value.

When searching by date using the `dateFrom` and `dateTo` URL parameters, you will get two kinds of results:

* Events and places without `openingHours`, where the `startDate` and `endDate` of the event / place intersect with the `dateFrom` and `dateTo` parameters. \(If an event or place has multiple `startDate` and `endDate` properties as `subEvents`, they will each be evaluated against the query and if at least one intersects the relevant event / place is considered to be a match.\)
* Events and places with `openingHours`, of which at least one of the `openingHours` intersects with the given `dateFrom` and `dateTo`. For example a place that is open on Mondays from 08:00 to 12:00 will be a match for a date query that includes a Monday and intersects with those hours.
* Events and places that are `permanent`  and have no opening hours are always considered to be matches when searching by date.

**Examples**

Get all events that occur on a given day, and all places that are open on that same day:

```
GET https://search.uitdatabank.be/offers/?dateFrom=2017-01-01T00:00:00+01:00&dateTo=2017-01-01T23:59:59+01:00
```

Get all events that occur on an exact moment, and all places that are open at that same moment:

```
GET https://search.uitdatabank.be/offers/?dateFrom=2017-01-01T12:00:00+01:00&dateTo=2017-01-01T12:00:00+01:00
```

Get all events that occur starting from a specific moment, and all places that are open at some point from that moment on:

```
GET https://search.uitdatabank.be/offers/?dateFrom=2017-01-01T12:00:00+01:00
```

Get all events that occured at least once before a given moment, and all places that were open at some point before that moment:

```
GET https://search.uitdatabank.be/offers/?dateTo=2017-01-01T12:00:00+01:00
```

## Advanced queries

You can also search by date using [advanced queries](/advanced-queries.md), which allows you to create more complex queries than by using the URL parameters, but with the downside that opening hours will not be taken into account. So you will only get events and places that have no opening hours.

To search by date using advanced queries, you can use the `dateRange` field that is indexed for each date range on an event or place. This field can be queried with either a single value or a range.

Single value example:

```
GET https://search.uitdatabank.be/offers/?q=dateRange:2017-01-01T00:00:00+01:00
```

Range example:

```
GET https://search.uitdatabank.be/offers/?q=dateRange:[2017-01-01T00:00:00+01:00 TO 2017-01-01T23:59:59+01:00]
```

Same as the URL parameters, the expected value is an `ISO-8601` datetime including a timezone offset.

