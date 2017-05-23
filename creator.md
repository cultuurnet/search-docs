# Creator

You can search by creator using two methods:

* URL parameter
* Advanced queries

## Url parameter

You can filter by an exact match with the `creator`  URL parameter.

```
GET https://search.uitdatabank.be/offers/?creator=janedoe
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `creator` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=creator:janedoe OR creator:john*
```

For more info, see the [advanced queries documentation](/advanced-queries.md).

