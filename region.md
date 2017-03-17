# Region

Searching by region is based on the geographical coördinates of events and places, that are then matched with pre-indexed geographical shapes.

Currently the only way to search by region is using the `regionId` URL parameter. Support for searching by region in [advanced queries](/advanced-queries.md) is coming soon.

For example:

```
GET https://search.uitdatabank.be/offers/?regionId=gem-leuven
```

Will return all events and places located in Leuven.

A complete list of region IDs can be found here:

* Municipalities: [https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/gem](https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/gem)
* Provinces: [https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/prv](https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/prv)

The file names represent the region IDs \(without the .geojson extension\).

