# Example queries

## Tipswidget "Mijn Kind op Kamp"
> show a selection of the first 5 occuring events for children with eventtype "kamp of vakantie" that take place during the summer of 2017

- [periode](/searching/date.md): zomervakantie 2017 
`q=dateRange:[2017-07-01T00:00:00+01:00 TO 2017-08-31T23:59:59+01:00]`
- [type](/searching/terms.md):"Kamp of vakantie" 
`q=terms.label:"Kamp of vakantie"`
- [leeftijd](/searching/age.md): jonger dan 14 jaar 
`q=typicalAgeRange:[* TO 14]`
- met [afbeelding](/searching/media-objects.md) 
`q=mediaObjectsCount:>=1`
- [gesorteerd](/searching/sorting.md) op startdatum
`sort[availableTo]=asc`
- toon enkel [5 results](/getting_started/pagination.md)
`limit=5`


```
GET https://search.uitdatabank.be/events/?q=terms.label:%22Kamp%20of%20vakantie%22%20AND%20typicalAgeRange:[*%20TO%2014]%20AND%20dateRange:[2017-07-01T00:00:00%2B01:00%20TO%202017-08-31T23:59:59%2B01:00]%20AND%20mediaObjectsCount:%3E=1&sort[availableTo]=asc&limit=5
```


## In the mood for "arts & culture"
> show all temporary events that focus on "arts & culture" (a selection based on specific eventtypes and themes)

**Include**
- [eventtype](/searching/terms.md): tentoonstelling
`q=terms.id:0.0.0.0.0`
- [eventtype](/searching/terms.md): theatervoorstelling
`q=terms.id:0.55.0.0.0`
- [eventtype](/searching/terms.md): dansvoorstelling
`q=terms.id:0.54.0.0.0`
- [theme](/searching/terms.md): jazz & blues
`q=terms.id:1.8.2.0.0`
- [theme](/searching/terms.md): klassiek
`q=terms.id:1.8.1.0.0`
- [temporary](/searching/calendar-type.md) events
`q=calendarType:single OR calendarType:multiple`


**Exclude**
- [eventtype](/searching/terms.md): cursus en workshop
`q=terms.id:0.3.1.0.0`
- [eventtype](/searching/terms.md): lezing en congres
`q=terms.id:0.3.2.0.0



```
GET https://search.uitdatabank.be/events/?q=(((terms.label:Tentoonstelling%20OR%20terms.label:Theatervoorstelling%20OR%20terms.label:Dansvoorstelling%20OR%20terms.label:%22Jazz%20en%20blues%22%20OR%20terms.label:%22Klassieke%20muziek%22)%20NOT%20(terms.label:%22Cursus%20of%20workshop%22%20OR%20terms.label:%22Lezing%20of%20congres%22))%20AND%20(calendarType:single%20OR%20calendarType:multiple))
```

## Free events in Ghent

- [free](/searching/price.md) events
`q=price:0`
- [Ghent](/searching/region.md)
`q=regions:gem-gent`

```
GET https://search.uitdatabank.be/events/?q=price:0%20AND%20regions:gem-gent
```


## UiTPAS Oostende events
> show all events that take place in Oostende and have an UiTPAS organizer

- [UiTPAS](/searching/uitpas.md) Oostende
`q=regions:gem-oostende AND organizer.labels:"UiTPAS Oostende"`
OR
`uitpas=true&q=regions:gem-oostende`


```
GET https://search.uitdatabank.be/events/?q=regions:gem-oostende%20AND%20organizer.labels:"UiTPAS%20Oostende"
```
