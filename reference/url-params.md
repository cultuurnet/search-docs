## Reference 

| URL param | Value | Example | doc |
| :-----: | :-----: | :-----: | :-----: |
| addressCountry | ISO 3166-1 alpha-2 country code (Default = BE) | addressCountry=NL | [Address](/searching/address.md) | 
| audienceType | Supported values: everyone (default), members, education | audienceType=members | [Audience type](/searching/audience-type.md) |
| availableFrom | ISO-8601 datetime (default = current date)| availableFrom=2017-04-01T00:00:00+01:00 | [Availability](/searching/availability.md) |
| availableTo | ISO-8601 datetime (default = current date) | availableTo=2017-04-30T23:59:59+01:00 | [Availability](/searching/availability.md) |  
| calendarType | permanent, periodic, multiple, single | calendarType=single,multiple | [Calendar type](/searching/calendar-type.md) |
| createdFrom | ISO-8601 datetime | createdFrom=2017-01-01T00:00:00+01:00 | [Created and modified](/searching/created-and-modified.md) |
| createdTo | ISO-8601 datetime | createdTo=2017-01-01T00:00:00+01:00 | [Created and modified](/searching/created-and-modified.md) |
| creator | string | creator:janedoe@john.org | [Creator](/searching/creator.md) |
| completedLanguages | Supported values: nl, fr, de, en | completedLanguages[]=fr | [Languages](/searching/languages.md) |
| coordinates | decimal representation of latitude & longitude | coordinates=50.8511740,4.3386740 | [Geo distance](/searching/geo-distance.md) |  
| dateFrom | ISO-8601 datetime | dateFrom=2017-01-01T00:00:00+01:00 | [Date & time](/searching/date.md) |  
| dateTo | ISO-8601 datetime | dateTo=2017-01-01T23:59:59+01:00 | [Date & time](/searching/date.md) |  
| disableDefaultFilters | Boolean | disableDefaultFilters=true | [Default filters](/getting_started/default-filters.md) |  
| distance | ElasticSearch distance units| coordinates=50.8511740,4.3386740&distance=10km | [Geo distance](/searching/geo-distance.md) |
| embed | Boolean (default=false) | embed=true | [Embedding result bodies](/getting_started/embedding-full-result-bodies.md) |  
| facets | Supported values: regions, types, themes, facilities | facets[]=regions | [Facet counts](/searching/facet-counts.md) |
| hasMediaObjects| boolean | hasMediaObjects=true | [Media objects](/searching/media-objects.md) | 
| id | uuid | id=f29d2182-2db0-4f99-831a-8e6a64c1c9c1 | [Id](/searching/id.md) |
| labels | string | labels[]=paspartoe | [Labels](/searching/labels.md) |
| languages | Supported values: nl, fr, de, en | languages[]=fr | [Languages](/searching/languages.md) |  
| limit | integer | limit=5 | [Pagination](/getting_started/pagination.md)| 
| locationId | uuid | locationId=b8bff8fa-988a-44db-8dd8-70bef77f3933 | [Id](/searching/id.md) |  
| locationTermIds | UiTdatabank taxonomy | locationTermIds[]=JCjA0i5COUmdjMwcyjNAFA | [Terms](/searching/terms.md) |  
| locationTermLabels | UiTdatabank taxonomy | locationTermLabels[]=Jeugdhuis of jeugdcentrum | [Terms](/searching/terms.md) |
| mainLanguage | Supported values: nl (default), fr, de, en | mainLanguage=nl | [Languages](/searching/languages.md) |   
| maxAge | integer | maxAge=21 | [Age](/searching/age.md) |  
| maxPrice | numeric | maxPrice=25 | [Price](/searching/price.md) |
| modifiedFrom | ISO-8601 datetime | modifiedFrom=2017-01-01T00:00:00+01:00 | [Created and modified](/searching/created-and-modified.md) |
| modifiedTo | ISO-8601 datetime | modifiedTo=2017-01-01T00:00:00+01:00 | [Created and modified](/searching/created-and-modified.md) |  
| minAge | integer | minAge=12 | [Age](/searching/age.md) |  
| minPrice | numeric | minPrice=9.99 | [Price](/searching/price.md) |
| organizerId | uuid | organizerId=7d1f485d-dab5-4ad2-8894-322060a2bc52 | [Id](/searching/id.md) |  
| postalCode | integer or string | postalCode=3000 | [Address](/searching/address.md) |  
| price | numeric | price=5 | [Price](/searching/price.md) |  
| q | Query string syntax| q=(wandeling OR wandelen) AND femma | [Advanced queries](/reference/advanced-queries.md) and [Free text search](/searching/free-text-search.md) |  
| regions | region id | regions=gem-leuven | [Region](/searching/region.md) |  
| start | integer | start=10 | [Pagination](/getting_started/pagination.md) |
| sort | supported values: score, availableTo / order: asc, desc | sort[availableTo]=asc | [Sorting](/searching/sorting.md) |  
| termIds | UiTdatabank taxonomy | termIds[]=0.55.0.0.0 | [Terms](/searching/terms.md) |  
| termLabels | UiTdatabank taxonomy | termLabels[]=Theatervoorstelling | [Terms](/searching/terms.md) |  
| text | Query string syntax | text=(wandeling OR wandelen) AND femma | [Free text search](/searching/free-text-search.md) |  
| uitpas | Boolean (true/false/*) | uitpas=true | [UiTPAS](/searching/uitpas.md) |  
| workflowStatus | supported values: DRAFT, READY\_FOR\_VALIDATION, APPROVED, REJECTED, DELETED | workflowStatus=READY\_FOR\_VALIDATION,APPROVED (default) | [Workflow status](/searching/workflow-status.md) |