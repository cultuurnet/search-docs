# Labels

You can search by label\(s\) using two methods:

* URL parameter
* Advanced queries

## Url parameter

You can filter by one or more labels using the `labels` URL parameter.

```
GET https://search.uitdatabank.be/offers/?labels[]=uitpas&labels[]=paspartoe
```

You will only get results with complete matches. An event with for example the label `UiTPAS Leuven` will not be returned by the query above. Wildcards are not supported using the URL parameter!

Note that this method always uses the `AND` operator.

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `labels` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=labels:uitpas* OR labels:paspartoe
```

Searching by labels in advanced queries still looks for complete matches, but contrary to the `labels` URL parameter, wildcards are supported.

When searching for labels with spaces, be sure to encapsulate the label in quotation marks:

```
GET https://search.uitdatabank.be/offers/?q=labels:"uitpas leuven" OR labels:paspartoe
```

For more info, see the [advanced queries documentation](/advanced-queries.md).

## Examples

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