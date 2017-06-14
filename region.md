# Region

Searching by region is based on the geographical coördinates of events and places, that are then matched with pre-indexed geographical shapes.

You can search by region using two methods:

* URL parameter
* Advanced query

An important difference between the two is that the filtering by region uses a cache in advanced queries, which is faster but may be slightly out of date. The URL parameter on the other hand does the filtering on-demand, which is slower but always up to date.

## URL parameter

You can use the `regions` URL parameter to filter all documents by one or more regions.

For example:

```
GET https://search.uitdatabank.be/offers/?regions=gem-leuven
```

This will return all events and places located in Leuven.

If you want to filter multiple regions, pass them along as separate parameters
```
GET https://search.uitdatabank.be/offers/?regions[]=prv-vlaams-brabant&regions[]=gem-leuven
```

The `regions` URL parameter only accepts complete region ids, and wildcards are not supported. Any incomplete id will return zero results.

Note that filtering the documents by region using the URL parameter does the filtering on-demand, which may be slower but up to date. This is contrary to advanced queries, which use a cached list of regions per document.

## Advanced queries

Using advanced queries, you can create more complex queries than by using the `regions` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=regions:gem-leuven OR regions:gem-gent
```

This will return all events and places located in both Leuven and Gent.

Note that wildcards are supported:

```
GET https://search.uitdatabank.be/offers/?q=regions:gem-zo*
```

This will return all events and places located in municipalities starting with "zo". For example Zonhoven, Zolder, ...

The `regions` property is a cached list, so it may be slightly outdated, but it is faster than the `regions` URL parameter.

## Available regions and their ids

A complete list of region IDs can be found here:

* Municipalities: [https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/gem](https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/gem)
* Provinces: [https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/prv](https://github.com/cultuurnet/geojson-data/tree/master/geojson/BE/prv)

The file names represent the region IDs \(without the .geojson extension\).
