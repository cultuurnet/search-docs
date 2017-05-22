# Address

You can filter by address-related fields using two methods:

* URL parameter
* Advanced queries

## URL parameter

Currently, the only URL parameters for address fields are `postalCode` and `addressCountry`.

While `postalCode` can be any integer or string, `addressCountry` should always be an [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code.

Example usage:

```
GET https://search.uitdatabank.be/offers/?postalCode=3000
```

```
GET https://search.uitdatabank.be/offers/?addressCountry=BE
```

These URL parameters look for complete matches, but are case insensitive.

## Advanced queries

Using advanced queries, you can not only filter by `postalCode` or `addressCountry`, but also by `addressLocality` and `streetAddress`.

For example:

```
GET https://search.uitdatabank.be/offers/?q=addressCountry:BE AND postalCode:3000 AND addressLocality:Leuven AND streetAddress:Bondgenotenlaan*
```

All address fields allow wildcards and/or complete matches \(using quotes\) like regular string fields, but only when using advanced queries.

Note that `streetAddress` also includes the street number, so make sure to use a wildcard to filter by a street name!

For more information, see [advanced queries](/advanced-queries.md).


## Examples

### Search by postal code
> filter all events that take place on a location based in a specific postal code

**params**
* URL param: `postalCode=3000`

```
GET https://search.uitdatabank.be/offers/?postalCode=3000&embed=true
```

### Search by city
> filter all events that take place on a location based in a specific city

**params**
* Advanced query: `q=addressLocality:Leuven`

```
GET https://search.uitdatabank.be/offers/?q=addressLocality:Leuven&embed=true
```

### Search by coordinates and a specific distance
> filter all events that take place within a given range of a specific point

**params**
* URL param: `coordinates=50.8511740,4.3386740&distance=10km`
```
GET https://search.uitdatabank.be/offers/?coordinates=50.8511740,4.3386740&distance=10km
```

### Province/Region/Municipality
> filter all events that take place in a specific region, see [Region](/region.md).
