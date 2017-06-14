# Id

You can search by id using two methods:

* URL parameter
* Advanced queries

This search is always done with an exact match. 

It is possible to search by an offer id (event or place), and/or a related location id, and/or a related organizer id.

## URL parameter

You can filter by an exact match using the `id`, `locationId` or `organizerId` URL parameter:

```
GET https://search.uitdatabank.be/offers/?id=f29d2182-2db0-4f99-831a-8e6a64c1c9c1
```
```
GET https://search.uitdatabank.be/offers/?locationId=b8bff8fa-988a-44db-8dd8-70bef77f3933
```
```
GET https://search.uitdatabank.be/offers/?organizerId=7d1f485d-dab5-4ad2-8894-322060a2bc52
```

Note that the locationId and organizerId parameters will return offer results, with a matching related location and/or organizer.

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=id:f29d2182-2db0-4f99-831a-8e6a64c1c9c1 or location.id:b8bff8fa-988a-44db-8dd8-70bef77f3933 and organizer.id:7d1f485d-dab5-4ad2-8894-322060a2bc52
```

For more info, see the [advanced queries documentation](/advanced-queries.md).



