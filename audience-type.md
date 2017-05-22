# Audience type

You can search by audience type using two methods:

* URL parameter
* Advanced queries

There are 3 possible values for audience type on a place or event:

* everyone \(this is the default value\)
* members
* education

## Url parameter

You can filter by an exact match with the `audienceType`  URL parameter.

```
GET https://search.uitdatabank.be/offers/?audienceType=members
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `audienceType` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=audienceType:members OR audienceType:education
```

For more info, see the [advanced queries documentation](/advanced-queries.md).

## Examples

### UiTPAS-events for members
> filter all events with an UiTPAS organizer and audienceType "members"

**params**
* URL param: `audienceType=members&uitpas=true` *'uitpas' URL param not yet available*
* Advanced query: `q=audienceType:members AND labels:(UiTPAS* OR paspartoe)`
 
```
GET https://search.uitdatabank.be/events/?q=audienceType:members AND labels:(UiTPAS* OR paspartoe)
```

### Events for schools in Leuven
> filter all events with target audience "schools" and location in city "Leuven"

**params**
* URL param: `audienceType=education&regionIds[]=gem-Leuven`
* Advanced query: `q=audienceType:members AND regions:gem-Leuven`

```
GET https://search.uitdatabank.be/offers/?audienceType=education&regionIds[]=gem-Leuven
```