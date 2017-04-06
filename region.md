# Region

Searching by region is based on the geographical coördinates of events and places, that are then matched with pre-indexed geographical shapes.

You can search by region using two methods:

* URL parameter
* Advanced query

An important difference between the two is that the filtering by region uses a cache in advanced queries, which is faster but may be slightly inaccurate. The URL parameter on the other hand does the filtering on-demand, which is slower but may be more accurate.

## URL parameter

You can use the `regionId` URL parameter to filter all documents by a \(single\) specific region.

For example:

```
GET https://search.uitdatabank.be/offers/?regionId=gem-leuven
```

This will return all events and places located in Leuven.

Note that filtering the documents by region using the URL parameter does the filtering on-demand, which may be slower but more accurate. This is contrary to advanced queries, which use a cached list of regions per document.

## Advanced queries

Using advanced queries, you can create more complex queries than by using the `regionId` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=regions:gem-leuven OR regions:gem-gent
```

This will return all events and places located in both Leuven and Gent.

The `regions` property is a cached list, so it may be slightly outdated, but it is faster than the `regionId` URL parameter.

## Available regions and their ids

A complete list of region IDs can be found here:

* Municipalities: [https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/gem](https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/gem)
* Provinces: [https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/prv](https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/prv)

The file names represent the region IDs \(without the .geojson extension\).

