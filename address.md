# Address

You can filter by address-related fields using two methods:

* URL parameter
* Advanced queries

By default, the search API will only return results that are in Belgium. You can reset this default as described in [Default filters](/default-filters.md).

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
GET https://search.uitdatabank.be/offers/?addressCountry=*&q=addressCountry:BE AND postalCode:3000 AND addressLocality:Leuven AND streetAddress:Bondgenotenlaan*
```

All address fields allow wildcards and/or complete matches \(using quotes\) like regular string fields, but only when using advanced queries.

Note that `streetAddress` also includes the street number, so make sure to use a wildcard to filter by a street name!

For more information, see [advanced queries](/advanced-queries.md).