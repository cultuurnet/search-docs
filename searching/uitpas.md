# UiTPAS

You can search for UiTPAS related events or places using an URL parameter.

## Url parameter

You can search for all UiTPAS related events or places by setting the `uitpas` URL parameter to `true`:

```
GET https://search.uitdatabank.be/offers/?uitpas=true
```

It is also possible to search for all events or places which are not marked as UiTPAS by setting the `uitpas` URL parameter to `false`:

```
GET https://search.uitdatabank.be/offers/?uitpas=false
```

Behind the screens this filter is converted to a Lucene query that searches for the labels `UiTPAS*` or `Paspartoe` on each event's or place's organizer.

