# Advanced queries

The `q` parameter used for [free text search](/free-text-search.md) can also be used to execute more complex queries.

For example:

```
GET https://search.uitdatabank.be/offers/?q=(labels:uitpas* OR labels:paspartoe) AND typicalAgeRange:[* TO 12]
```

The syntax is based on the Lucene query syntax. More info can be found in the ElasticSearch documentation:  
[https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html\#query-string-syntax](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax)

## Mixing free text search and advanced queries

As per the ElasticSearch documentation, it is possible to mix free text search and advanced queries.

For example:

```
GET https://search.uitdatabank.be/offers/?q=zwembad labels:uitpas*
```

This will execute a free text search for the term `zwembad`, combined with a label search for `uitpas*`.

Because of this, it is important to encapsulate field values that contain spaces, like this:

```
GET https://search.uitdatabank.be/offers/?q=zwembad labels:"uitpas leuven"
```

If we don't encapsulate `uitpas leuven` with quotes in the example above, `leuven` would become part of the free text search query instead of the label query.

Make sure to escape any quotes in the field values themselves if you encapsulate them!

For example, a valid label in UiTdatabank could be `"dag van de fiets"` \(with quotes!\).

To search for this label in an advanced query, it should be escaped and encapsulated like this:

```
GET https://search.uitdatabank.be/offers/?q=labels:"\"dag van de fiets\""
```

## Supported fields advanced query

| Field | Type | Comments |
| :--- | :--- | :--- |
| id | String | Complete matches only by default\* |
| workflowStatus | Enum \(String\) | See [Workflow status](/workflow-status.md) |
| name.nl | String |  |
| name.fr | String |  |
| name.de | String |  |
| name.en | String |  |
| description.nl | String |  |
| description.fr | String |  |
| description.de | String |  |
| description.en | String |  |
| languages | String | See [Languages](/languages.md) |
| terms.id | String | Complete matches only by default\* |
| terms.label | String | Complete matches only by default\* |
| labels | String | See [Labels](/labels.md). Complete matches only by default\* |
| price | Integer | See [Price](/price.md) |
| typicalAgeRange | Integer range | See [Age](/age.md) |
| audienceType | String | See [Audience type](/audience-type.md) |
| labels | String | Complete matches only by default\* |
| typicalAgeRange | Integer range |  |
| addressCountry | Enum | See [Address](/address.md) |
| addressLocality | String | See [Address](/address.md) |
| postalCode | String | See [Address](/address.md) |
| streetAddress | String | See [Address](/address.md) |
| regions | Enum | See [Region](/region.md) |
| location.id | String | Complete matches only by default\* |
| location.name.nl | String |  |
| location.name.fr | String |  |
| location.name.de | String |  |
| location.name.en | String |  |
| location.terms.id | String | Complete matches only by default\* |
| location.terms.label | String | Complete matches only by default\* |
| location.labels | String | Complete matches only by default\* |
| organizer.id | String | Complete matches only by default\* |
| organizer.name.nl | String |  |
| organizer.name.fr | String |  |
| organizer.name.de | String |  |
| organizer.name.fr | String |  |
| organizer.labels | String | Complete matches only by default\* |

\* Wildcards allowed to search for partial matches

## URL parameters

| URL param | Description | Example |
| :-----: | :-----: | :-----: |
| addressCountry | filter by address-related fields (ISO 3166-1 alpha-2 country code) | addressCountry=BE |  
| audienceType | filter by an exact match with one of three possible values: everyone, members, education | audienceType=members |
| availableFrom |   | availableFrom=2017-04-01T00:00:00+01:00 |  
| availableTo |   | availableTo=2017-04-30T23:59:59+01:00 |  
| calendarType | filter by calendar type: permanent, periodic, multiple, single |   |  
| coordinates | search by geo distance: start from a single pair of coördinates, and look for events and places in a specific range from the given location | coordinates=50.8511740,4.3386740&distance=10km |  
| dateFrom | filter by startdate | dateFrom=2017-01-01T00:00:00+01:00 |  
| dateTo | filter by enddate | dateTo=2017-01-01T23:59:59+01:00 |  
| defaultFilters |   | defaultFilters=false |  
| distance | search by geo distance: start from a single pair of coördinates, and look for events and places in a specific range from the given location | coordinates=50.8511740,4.3386740&distance=10km |
| embed | embed actual JSON-LD bodies of the results (default=false) | embed=true |  
| facets | get facet counts for specific fields: regions, types, themes, facilities | facets[]=regions |
| id | search by an offer id (event or place), and/or a related location id, and/or a related organizer id | id=f29d2182-2db0-4f99-831a-8e6a64c1c9c1 |
| labels | filter by one or more labels | labels[]=paspartoe&labels[]=muntpunt |
| languages | limit your results to documents that have translations for a specific language | languages[]=fr |  
| locationId | search by an offer id (event or place), and/or a related location id, and/or a related organizer id | locationId=b8bff8fa-988a-44db-8dd8-70bef77f3933 |  
| locationTermIds | filter by term ids and/or term labels on embedded location (http://taxonomy.uitdatabank.be/api/domain/eventtype/classification) | locationTermIds[]=JCjA0i5COUmdjMwcyjNAFA |  
| locationTermLabels | filter by term ids and/or term labels on embedded location (http://taxonomy.uitdatabank.be/api/domain/eventtype/classification) | locationTermLabels[]=Jeugdhuis of jeugdcentrum |  
| maxAge | filter by minimum and/or maximum age | maxAge=21 |  
| maxPrice | filter by minimum and/or maximum price | maxPrice=25 |  
| minAge | filter by minimum and/or maximum age | minAge=12&maxAge=16 |  
| minPrice | filter by minimum and/or maximum price | minPrice=9.99&maxPrice=20 |  
| organizerId | search by an offer id (event or place), and/or a related location id, and/or a related organizer id | organizerId=7d1f485d-dab5-4ad2-8894-322060a2bc52 |  
| postalCode | filter by address-related fields (integer or string) | postalCode=3000 |  
| price | filter on an exact price | price=9.99 |  
| q | search for text across multiple pre-defined fields | q=(wandeling OR wandelen) AND femma |  
| regionId | filter all documents by a (single) specific region | regionId=gem-leuven |  
| termIds | filter by one or more term ids or term labels (http://taxonomy.uitdatabank.be/api/domain/eventtype/classification) | termIds[]=0.55.0.0.0 |  
| termLabels | filter by one or more term ids or term labels (http://taxonomy.uitdatabank.be/api/domain/eventtype/classification) | termLabels[]=Theatervoorstelling |  
| text | search for text across multiple pre-defined fields | text=(wandeling OR wandelen) AND femma |  
| textLanguages | limit your free text queries to one or more specific languages | textLanguages[]=nl |  
| uitpas | limit results to offers with UiTPAS-organizer (true/false/*) | uitpas=true |  
| workflowStatus | search offers by their workflowstatus: DRAFT, READY\_FOR\_VALIDATION, APPROVED, REJECTED, DELETED | workflowStatus:READY\_FOR\_VALIDATION |  