# Advanced queries

The `q` parameter used for [free text search](/searching/free-text-search.md) can also be used to execute more complex queries.

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

## Supported fields

| Field | Type | Comments |
| :--- | :--- | :--- |
| id | String | Looks for complete matches |
| address.{[lang](/searching/languages.md)}.addressCountry | Enum | See [Address](/searching/address.md) |
| address.{[lang](/searching/languages.md)}.addressLocality | String | See [Address](/searching/address.md) |
| address.{[lang](/searching/languages.md)}.postalCode | String | See [Address](/searching/address.md) |
| address.{[lang](/searching/languages.md)}.streetAddress | String | See [Address](/searching/address.md) |
| audienceType | String | See [Audience type](/searching/audience-type.md) |
| availableRange | Date range | See [Availability](/searching/availability.md) |
| calendarType | String | Looks for complete matches |
| createdRange | DateRange | See [Created and Modified](/searching/created-and-modified.md) |
| creator | String | See [Creator](/searching/creator.md) |
| dateRange | Date range | See [Date & time](/searching/date.md) |
| description.{[lang](/searching/languages.md)} | String |  |
| labels | String | See [Labels](/searching/labels.md). Looks for complete matches |
| languages | String | See [Languages](/searching/languages.md) |
| location.id | String | Looks for complete matches |
| location.name.{[lang](/searching/languages.md)} | String |  |
| location.labels | String | Looks for complete matches |
| location.terms.id | String | Looks for complete matches |
| location.terms.label | String | Looks for complete matches |
| mediaObjectsCount | Integer | See [Media objects](/searching/media-objects.md) |
| modifiedRange | DateRange | See [Created and Modified](/searching/created-and-modified.md) |
| name.{[lang](/searching/languages.md)} | String |  |
| organizer.id | String | Looks for complete matches |
| organizer.name.{[lang](/searching/languages.md)} | String |  |
| organizer.labels | String | Looks for complete matches |
| price | Integer | See [Price](/searching/price.md) |
| regions | Enum | See [Region](/searching/region.md) |
| terms.id | String | Looks for complete matches |
| terms.label | String | Looks for complete matches |
| typicalAgeRange | Integer range | See [Age](/searching/age.md) |
| workflowStatus | Enum \(String\) | See [Workflow status](/searching/workflow-status.md) |

### Notes
* Wildcards (`*` or `?`) allowed to search for partial matches. (See [ElasticSearch documentation on syntax](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html\#query-string-syntax))
* `{lang}` should always be replaced by either a specific language (`nl`, `fr`, ...) or an **escaped** wildcard (`\*`)

## Examples

Searching by label `fietsen`

```
GET https://search.uitdatabank.be/offers/?q=labels:fietsen
```

Searching by all labels that start with `fiets`
```
GET https://search.uitdatabank.be/offers/?q=labels:fiets*
```

Searching by `postalCode` in the `nl` address:
```
GET https://search.uitdatabank.be/offers/?q=address.nl.postalCode:3000
```

Searching by `postalCode` in any address translation:
```
GET https://search.uitdatabank.be/offers/?q=address.\*.postalCode:3000
```

