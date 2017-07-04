# Facet counts

It is possible to get facet counts for specific fields using the `facets` URL parameter.

Supported values are:

* `regions`
* `types`
* `themes`
* `facilities`

Example request:

```
GET https://search.uitdatabank.be/offers/?facets[]=regions
```

You can request multiple facets like this:

```
GET https://search.uitdatabank.be/offers/?facets[]=regions&facets[]=types
```

Example response:

```
{
  "@context": "http://www.w3.org/ns/hydra/context.jsonld",
  "@type": "PagedCollection",
  "itemsPerPage": 30,
  "totalItems": 50,
  "member": [ ... ],
  "facet": {
    "regions": {
      "prv-vlaams-brabant": {
        "name": {
          "nl": "Vlaams-Brabant",
          "fr": "Brabant Flamand",
          "en": "Flemish Brabant"
        },
        "count": 22,
        "children": {
          "gem-leuven": {
            "name": {
              "nl": "Leuven",
              "fr": "Louvain"
            },
            "count": 7
          },
          "gem-diest": {
            "name": {
              "nl": "Diest",
              "fr": "Diest"
            },
            "count": 4
          },
          // ... more region children omitted ...
        }
      },
      // ... more regions omitted ...
    }
  }
}
```

The key of each facet node is the value you should use to filter that specific field. In the example above, you can filter by using the `regionId` [URL parameter](/searching/region.md) or the `regions` field in [advanced queries](/reference/advanced-queries.md) in combination with any key from the returned facets, to narrow down your search.

**Important!** You should never assume a specific amount of levels for a particular facet in your code. Instead, you should parse the given facets recursively by looking for the `children` property in each one.