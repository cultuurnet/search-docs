# Price

You can search by price using two methods:

* URL parameter
* Advanced queries

In both methods it is possible to either search by an exact price or by a price range.

Currently a price parameter is always treated as EUR.

## Url parameter

### Exact price

You can filter on an exact price with the following query:

```
GET https://search.uitdatabank.be/offers/?price=9.99
```

This will return all events and places with an exact price of 9.99 EUR.

### Price range

You can filter by minimum and maximum price like this:

```
GET https://search.uitdatabank.be/offers/?minPrice=9.99&maxPrice=20
```

This will look for all events and places that have a price that is within the given range.

Both `minPrice` and `maxPrice` are optional and can be used on their own, or together.

For example, you could search for all events with a maximum price of 25 EUR, without having to specify a minimum price:

```
GET https://search.uitdatabank.be/offers/?maxPrice=25
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `price` and/or `minPrice` and/or `maxPrice` URL parameter.

### Exact price

It is possible to exactly match the price of an event or place:

```
GET https://search.uitdatabank.be/offers/?q=price:19.99 OR price:99.99
```

### Price range

It is possible to search on a range of prices:

```
GET https://search.uitdatabank.be/offers/?q=price:[9.99 TO 20] OR price:29.99
```

For more info, see the [advanced queries documentation](/advanced-queries.md).