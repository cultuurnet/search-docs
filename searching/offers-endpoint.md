# Searching events & places

Events & places can be searched from the following endpoint:

```
GET https://search.uitdatabank.be/offers/
```

A typical response from this endpoint looks like this:

```js
{
  "@context": "http://www.w3.org/ns/hydra/context.jsonld",
  "@type": "PagedCollection",
  "itemsPerPage": 30,
  "totalItems": 12,
  "member": [
    {
      "@id": "https://io.uitdatabank.be/place/39e6d5ee-c3d6-453a-bcb5-4e6e0eaf7054",
      "@type": "Place"
    },
    {
      "@id": "https://io.uitdatabank.be/event/23017cb7-e515-47b4-87c4-780735acc942",
      "@type": "Event"
    },
    ...
  ]
}
```

This endpoint supports the following global features:

* [Pagination](/pagination.md)
* [Embedding result bodies](/embedding-full-result-bodies.md)

If you want to limit your search to specifically events or places, you can use the `/events/` and `/places/` endpoints instead:

```
GET https://search.uitdatabank.be/events/
```

```
GET https://search.uitdatabank.be/places/
```

All parameters applicable to the `/offers/` endpoint are also applicable on `/events/` and `/places/`. Because of this, the documentation will generally use the `/offers/` endpoint in examples.