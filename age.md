# Age

You can search by age using two methods:

* URL parameter
* Advanced queries

## Url parameter

You can filter by minimum and maximum age like this:

```
GET https://search.uitdatabank.be/offers/?minAge=12&maxAge=16
```

This will look for all events and places that have an age range that overlaps with the given range.

Because of this, the query above will also match with documents with an age range of \(for example\) `10-14` because the two overlap partially.

Both `minAge` and `maxAge` are optional and can be used on their own, or together.

For example, you could search for all 16+ events, without having to specify a maximum age:

```
GET https://search.uitdatabank.be/offers/?minAge=16
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `minAge` and/or `maxAge` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=typicalAgeRange:[12 TO 14] OR typicalAgeRange:[* TO 8]
```

For more info, see the [advanced queries documentation](/advanced-queries.md).

## Examples

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

