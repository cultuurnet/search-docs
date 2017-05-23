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

