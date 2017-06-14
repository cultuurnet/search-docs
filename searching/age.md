# Age

You can search by age using two methods:

* URL parameter
* Advanced queries

## Url parameter

You can filter by minimum and maximum age like this:

```
GET https://search.uitdatabank.be/offers/?minAge=12&maxAge=16
```

This will look for all events and places that have an age range that overlaps with the given range.

Because of this, the query above will also match with documents with an age range of \(for example\) `10-14` because the two overlap partially.

Both `minAge` and `maxAge` are optional and can be used on their own, or together.

For example, you could search for all 16+ events, without having to specify a maximum age:

```
GET https://search.uitdatabank.be/offers/?minAge=16
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `minAge` and/or `maxAge` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=typicalAgeRange:[12 TO 14] OR typicalAgeRange:[* TO 8]
```

For more info, see the [advanced queries documentation](/advanced-queries.md).