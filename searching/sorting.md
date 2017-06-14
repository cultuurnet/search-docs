# Sorting

You can sort events and places either by `score` \(relevance\), or by their `availableTo` date \(most commonly used to show events that will be ending soon first\).

It is possible to change the sort `order`:

* Ascending order \(from smallest to biggest value\) by using `asc`
* Descending order \(from biggest to smallest value\) by using `desc`

Example:

```
GET https://search.uitdatabank.be/offers/?sort[availableTo]=asc
```

Example with multiple sort options:

```
GET https://search.uitdatabank.be/offers/?sort[availableTo]=asc&sort[score]=desc
```

Note that if you use multiple `sort` options,  the order of the `sort` options influences the order in which they are sorted. In the example above, all events and places will be sorted by `availableTo` first,  and afterwards any events or places with the same `availableTo` are sorted by `score`.

## Distance

When searching by [geo distance](/geo-distance.md), it is possible to sort the results by the distance from the given coördinates.

For example:

```
GET https://search.uitdatabank.be/offers/?coordinates=50.8511740,4.3386740&distance=10km&sort[distance]=asc
```

You can still combine this sort field with other sort fields:

```
GET https://search.uitdatabank.be/offers/?...&sort[distance]=asc&sort[score]=desc
```

However, the `distance` field can ONLY be used to sort when the `coordinates` and `distance` parameter are also present.


