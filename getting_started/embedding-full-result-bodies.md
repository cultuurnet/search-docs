# Embedding result bodies

By default the API endpoints only return a list of links to the individual search results.

To get the actual bodies of the results, there are two options:

* Loop over the results yourself and perform GET requests using the given URLs.
* Use the `embed`  URL parameter \(`bool,` defaults to `false`\), which does the same for you, but server-side.

For example:

```
GET https://search.uitdatabank.be/offers/?embed=true
```

Notice that the response will now contain actual JSON-LD documents:

```js
{
  "@context": "http://www.w3.org/ns/hydra/context.jsonld",
  "@type": "PagedCollection",
  "itemsPerPage": 30,
  "totalItems": 12,
  "member": [
    {
      "@id": "https://io.uitdatabank.be/place/39e6d5ee-c3d6-453a-bcb5-4e6e0eaf7054",
      "@type": "Place",
      "@context": "/contexts/place",
      "name": {
        "nl": "Jeugdhuis Sojo"
      },
      "address": {
        "addressCountry": "BE",
        "addressLocality": "Kessel-Lo (Leuven)",
        "postalCode": "3010",
        "streetAddress": "Eenmeilaan 1"
      },
      "terms": [
        {
          "id": "JCjA0i5COUmdjMwcyjNAFA",
          "label": "Jeugdhuis of jeugdcentrum",
          "domain": "eventtype"
        }
      ],
      ...
    },
    ...
  ]
}
```



