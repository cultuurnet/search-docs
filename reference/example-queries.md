# Example queries

## Date
Given: 
- 'NOW' is `2017-06-01T12:30:00+02:00`
- 'HERE' is `50.9268474,4.9143493`

### Today
> What is going on today in Leuven

**params**
- URL param:
```
GET https://search.uitdatabank.be/events/?dateFrom=2017-06-01T00:00:00%2B01:00&dateTo=2017-06-01T23:59:59%2B01:00&regions=gem-leuven
```
- Advanced query:

```
GET https://search.uitdatabank.be/events/?q=(dateRange:[2017-06-01T00:00:00%2B01:00%20TO%202017-06-01T23:59:59%2B01:00]%20AND%20regions:gem-leuven)
```


### This week
> What is going on in the next week to come

**params**
- URL param: 

```
GET https://search.uitdatabank.be/events/?dateFrom=2017-06-01T00:00:00%2B01:00&dateTo=2017-06-07T23:59:59%2B01:00
```

### Next 30 days
> What courses are going on in the next month in Leuven

**params**
- Advanced query: `q=(dateRange:[2017-06-01T00:00:00+01:00 TO 2017-06-30T23:59:59+01:00] AND regions:gem-leuven AND terms.id:0.3.1.0.0)`

```
GET https://search.uitdatabank.be/offers/?q=(dateRange:[2017-06-01T00:00:00%2B01:00 TO 2017-06-30T23:59:59%2B01:00] AND regions:gem-leuven AND terms.id:0.3.1.0.0)
```

### Now
> What is going on now in a perimeter of 10 km around me?

**params**
- URL param: `dateFrom=2017-06-01T12:30:00+01:00&dateTo=2017-06-07T12:30:00+01:00&coordinates=50.9268474,4.9143493&distance=10km`

```
GET https://search.uitdatabank.be/offers/?dateFrom=2017-06-01T12:30:00%2B01:00&dateTo=2017-06-07T12:30:00%2B01:00&coordinates=50.9268474,4.9143493&distance=10km
```

## Address

### Search by postal code
> filter all events that take place on a location based in a specific postal code

**params**
* URL param: `postalCode=3000`

```
GET https://search.uitdatabank.be/offers/?postalCode=3000&embed=true
```

### Search by city
> filter all events that take place on a location based in a specific city

**params**
* Advanced query: `q=addressLocality:Leuven`

```
GET https://search.uitdatabank.be/offers/?q=addressLocality:Leuven&embed=true
```

### Search by coordinates and a specific distance
> filter all events that take place within a given range of a specific point

**params**
* URL param: `coordinates=50.8511740,4.3386740&distance=10km`
```
GET https://search.uitdatabank.be/offers/?coordinates=50.8511740,4.3386740&distance=10km
```

### Province/Region/Municipality
> filter all events that take place in a specific region, see [Region](/region.md).

## Age

### Events for children
> All events for children between the age of 6 and 11

**params**

* URL: `minAge=6&maxAge=11`
* Advanced query: `q=typicalAgeRange:[6 TO 11]`

```
GET https://search.uitdatabank.be/events/?embed=true&minAge=6&maxAge=11
```

```
GET https://search.uitdatabank.be/events/?embed=true&q=typicalAgeRange:[6 TO 11]
```

### Outdoor events for children
> All events that combine the category 'outdoors' with one of these properties: 'typicalAgeRange between 6 and 11' OR 'label "ook voor kinderen"'

 
**params**

* Advanced query: `q=typicalAgeRange:[* TO 11] OR labels:"ook voor kinderen"&termIds[]=umv.5`

```
GET https://search.uitdatabank.be/events/?q=typicalAgeRange:[*%20TO%2011]%20OR%20labels:%22ook%20voor%20kinderen%22%20OR%20terms.id:%22umv*%22&termIds[]=umv.5
```

### No events for children
> Exclude all events for children

**params**

* Advanced query: `q=!(typicalAgeRange:[* TO 11] OR labels:"ook voor kinderen")`

```
GET https://search.uitdatabank.be/events/?q=!(typicalAgeRange:[* TO 11] OR labels:"ook voor kinderen")&embed=true
```

## Audience type

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

## calendar type

### All non-recurring events in Ghent
> return events with calendarType 'single' or calendarType 'multiple' in Ghent to get a list of events that only have one or a few occurences


**params**
- Advanced query: `q=((calendarType:single OR calendarType:multiple) AND regions:gem-gent)`

```
GET https://search.uitdatabank.be/events/?q=((calendarType:single OR calendarType:multiple) AND regions:gem-gent)&embed=true
```

### Exclude permanent events
> exclude events with a specific calendartype

- Advanced query: `q=!(calendarType:permanent)`

```
GET https://search.uitdatabank.be/events/?q=!(calendarType:permanent)
```

## Free text search

### Search for "DJ Shadow"
> All offers that contain the string "DJ Shadow" in one of the following fields: title, description, labels, organizer


**params**
* Advanced query: `q="DJ Shadow"`
* URL param: `text="DJ Shadow"`

```
GET https://search.uitdatabank.be/offers/?q="DJ Shadow"&embed=true
```

## Labels

### UiTPAS Oostende
> show all events that take place in Oostende and have an UiTPAS organiser

**params**
* URL param: `labels[]="UiTPAS Oostende"&regionId=gem-oostende`
* Advanced query: `q=labels:"UiTPAS Oostende" AND regions:gem-Oostende`

```
GET https://search.uitdatabank.be/offers/?q=labels:"UiTPAS Oostende" AND regions:gem-Oostende
```

### Jazzmozaiek
> show all events that are labeled with "jazzmozaiek"

**params**
* URL param: `labels[]=jazzmozaiek`

```
GET https://search.uitdatabank.be/offers/?labels[]=jazzmozaiek
```

### Open Monumentendag
> show all events that were organized for the Open Monumentendag event

**params**

* Advanced query: `q=labels:"Open Monumentendag*"` 

```
GET https://search.uitdatabank.be/offers/?q=labels:"Open Monumentendag*"
```

## Languages

### French events
> Search for events that have translated fields (titel and description) in French

**params**
* URL param: `languages[]=fr`
* Advanced query: `q=_exists_:name.fr AND _exists_:description.fr&languages[]=fr`

```
GET https://search.uitdatabank.be/events/?embed=true&q=_exists_:name.fr AND _exists_:description.fr&languages[]=fr
```

### Fully translated events
> Search for events that are fully translated in 3 languages: FR, DE, EN

**params**
* URL param: `languages[]=fr&languages[]=de&languages[]=en`
* Advanced query: `q=((_exists_:name.fr AND _exists_:description.fr) OR (_exists_:name.en AND _exists_:description.en) OR (_exists_:name.de AND _exists_:description.de))`

```
GET https://search.uitdatabank.be/events/?embed=true&q=((_exists_:name.fr AND _exists_:description.fr) OR (_exists_:name.en AND _exists_:description.en) OR (_exists_:name.de AND _exists_:description.de))&languages[]=fr&languages[]=de&languages[]=en
```

### Translated events
> Search for events that have at least one translation in EN, FR or DE

**params**
* Advanced query: `q=languages:("fr" OR "de" OR "en")`

```
GET https://search.uitdatabank.be/events/?embed=true&q=languages:("fr" OR "de" OR "en")
```

## Offers endpoint

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

## Price

### Free PASPARTOE events in Brussels
> Show only free events that take place in Brussels and have the PASPARTOE label

**params**
* URL param: `price=0&labels[]=paspartoe&regionIds=gem-brussel`
* Advanced query: `q=price:0 AND labels:paspartoe AND regions=gem-brussel`

```
GET https://search.uitdatabank.be/events/?price=0&labels[]=paspartoe&regionIds=gem-brussel
```

### Less than 5 EUR
> Show events  that cost 5 EUR or less

**params**
* URL param: `maxPrice=5`
* Advanced query: `q=price:[* TO 5]`


```
GET https://search.uitdatabank.be/events/?maxPrice=5
```

## Region

### Courses in Scherpenheuvel-Zichem
> filter all events with eventtype "Cursus of workshop" that take place in city "Scherpenheuvel-Zichem"

**params**
* URL param: `regions=gem-scherpenheuvel-zichem&termIds=0.3.1.0.0`

``` 
https://search.uitdatabank.be/events/?regions=gem-scherpenheuvel-zichem&termIds=0.3.1.0.0&embed=true
```

### All events in "Provincie West-Vlaanderen" AND "Provincie Oost-Vlaanderen"
> filter all events with a location in "Oost-Vlaanderen" OR "West-Vlaanderen"

**params**
* Advanced query: `q=regions:("prv-oost-vlaanderen" OR "prv-west-vlaanderen")`

``` 
https://search.uitdatabank.be/events/?q=regions:("prv-oost-vlaanderen" OR "prv-west-vlaanderen")&embed=true
```

## Terms

### Jazz and blues concerts
> All events with eventtype "concert" and theme "Jazz en blues".

**params**

* URL params: `termIds[]=0.50.4.0.0&termIds[]=1.8.2.0.0`
* URL params: `termLabels[]=Concert&termLabels[]="Jazz en blues"`

```
GET https://search.uitdatabank.be/events/?embed=true&termIds[]=0.50.4.0.0&termIds[]=1.8.2.0.0
```

### Parties
> All events with eventtype "Party of fuif"

**params**

* URL params: `termIds[]=0.49.0.0.0`

```
GET https://search.uitdatabank.be/events/?embed=true&termIds[]=0.49.0.0.0
```

### Landscape or nature reserve
> All places with type 'Natuurgebied of park'


**params**
* URL params: `termIds[]=0.15.0.0.0`

*Note the endpoint `/places`:*
```
GET https://search.uitdatabank.be/places/?embed=true&termIds[]=0.15.0.0.0
```

## Workflowstatus

### Approved events in Mechelen
> Show only approved events that take place in city Mechelen

**params**
* URL param: `workflowStatus=APPROVED&regionId=gem-mechelen`

```
GET https://search.uitdatabank.be/offers/?workflowStatus=APPROVED&regionId=gem-mechelen
```
