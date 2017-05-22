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

## Examples

### All pubs in Leuven
> A list of places with type 'Horeca' combined with free-text-search for 'pubs'

**params**
* URL param: `regionIds=gem-Leuven&termLabels[]=Horeca`
* Free text search: `q=bar OR café OR staminee`

```
GET https://search.uitdatabank.be/places/?q=(bar OR café OR staminee)&regionIds=gem-Leuven&termIds[]=Horeca
```

### All monuments in Flanders
> a list of all places with type 'Monument'

**params**
* URL param: `termIds[]=0.14.0.0.0`

```
GET https://search.uitdatabank.be/places/?termIds[]=0.14.0.0.0
```

### All events  that take place in monuments in Flanders
> a list of all events that occur in a place with  type 'Monument'

**params**

* URL param: `locationTermIds[]0.14.0.0.0`

```
GET https://search.uitdatabank.be/events/?locationTermIds[]0.14.0.0.0
```