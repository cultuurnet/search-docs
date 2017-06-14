# Geo distance

Searching by geo distance is based on the geographical coördinates of events and places. The difference with [searching by region](/region.md) is that a geo distance query starts from a single pair of coördinates, and looks for events and places in a specific range from the given location.

Currently the only way to search by geo distance is using the `coordinates` and `distance` URL parameters.

For example:

```
GET https://search.uitdatabank.be/offers/?coordinates=50.8511740,4.3386740&distance=10km
```

The coordinates should be decimal representations of latitude & longitude \(in that order\), separated by a comma.

The distance string can be anything supported by ElasticSearch. A dot should be used as decimal separator. See the ElasticSearch [documentation on distance units](https://www.elastic.co/guide/en/elasticsearch/reference/5.0/common-options.html#distance-units) for more information.

