# Audience type

You can search by audience type using two methods:

* URL parameter
* Advanced queries

There are 3 possible values for audience type on a place or event:

* everyone \(this is the default value\)
* members
* education

By default, the search API will only return results that have `audienceType` set as `everyone`. \(Places and events without an `audienceType` are always considered to be for `everyone`\)

You can reset this default as described in [Default filters](/getting_started/default-filters.md).

## Url parameter

You can filter by an exact match with the `audienceType`  URL parameter.

```
GET https://search.uitdatabank.be/offers/?audienceType=members
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/reference/advanced-queries.md) than by using the `audienceType` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?audienceType=*&q=audienceType:members OR audienceType:education
```

For more info, see the [advanced queries documentation](/reference/advanced-queries.md).