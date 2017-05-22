# Terms

You can search by term id\(s\) and term label\(s\) using two methods:

* URL parameter
* Advanced queries

## Url parameter

You can filter by one or more term ids or term labels using the `termIds` and/or `termLabels` URL parameters.

```
GET https://search.uitdatabank.be/offers/?termIds[]=JCjA0i5COUmdjMwcyjNAFA
```

```
GET https://search.uitdatabank.be/offers/?termLabels[]=Jeugdhuis of jeugdcentrum
```

You will only get results with complete matches. For example, an event with the term label `Jeugdhuis of jeugdcentrum` will not be returned when searching by term label `Jeugdhuis`. Wildcards are not supported using the URL parameter!

Note that this method always uses the `AND` operator.

To filter by term ids and/or term labels on embedded location, you can use the `locationTermIds` and `locationTermLabels` URL parameters.

```
GET https://search.uitdatabank.be/offers/?locationTermIds[]=JCjA0i5COUmdjMwcyjNAFA
```

```
GET https://search.uitdatabank.be/offers/?locationTermLabels[]=Jeugdhuis of jeugdcentrum
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the URL parameters mentioned above.

For example:

```
GET https://search.uitdatabank.be/offers/?q=terms.id:"0.7.0.0.0" or location.terms.id:JCjA0i5COUmdjMwcyjNAFA
```

Searching by term ids and/or term labels in advanced queries still looks for complete matches, but contrary to the URL parameters, wildcards are supported.

When searching for term ids or term labels with spaces, be sure to encapsulate the values in quotation marks:

```
GET https://search.uitdatabank.be/offers/?q=terms.label:"Begeleide rondleiding" OR location.terms.label:"Jeugdhuis of jeugdcentrum"
```

For more info, see the [advanced queries documentation](/advanced-queries.md).

For a list of available terms, see [UiTdatabank taxonomy](http://taxonomy.uitdatabank.be/api/domain):
* All available domains: http://taxonomy.uitdatabank.be/api/domain
* All terms in domain 'eventtype': http://taxonomy.uitdatabank.be/api/domain/eventtype/classification

## Examples

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