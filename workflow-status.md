# Workflow status

You can search by workflow status using two methods:

* URL parameter
* Advanced queries

By default the API filters out any offers that are not `APPROVED` or `READY_FOR_VALIDATION`. You can reset and/or override this by using the URL parameter as described below. Alternatively you can use the `disableDefaultFilters` parameter, as described in [Default filters](/default-filters.md).

## URL parameter

You can reset the default `workflowStatus` filter by using a wildcard character:

```
GET https://search.uitdatabank.be/offers/?workflowStatus=*
```

You can filter by an exact match using the `workflowStatus` URL parameter:

```
GET https://search.uitdatabank.be/offers/?workflowStatus=DRAFT
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `workflowStatus` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?workflowStatus=*&q=workflowStatus:DRAFT or workflowStatus:READY_FOR_VALIDATION
```

Note that you still have to reset the default `workflowStatus` filter first. Alternatively you can use the `disableDefaultFilters` parameter, as described in [Default filters](/default-filters.md).

For more info, see the [advanced queries documentation](/advanced-queries.md).

## Allowed values

A workflow status can be any of the following values \(case-insensitive\):

* `DRAFT`
* `READY_FOR_VALIDATION`
* `APPROVED`
* `REJECTED`
* `DELETED`

**Important!** Documents with a `DRAFT` status are not considered to be "available" by default, because they have not been published yet. Therefor, to find `DRAFT` documents, you will have to disable the default `availableFrom` and `availableTo` parameters like this:

```
GET https://search.uitdatabank.be/offers/?workflowStatus=DRAFT&availableFrom=*&availableTo=*
```

Or when using advanced queries:

```
GET https://search.uitdatabank.be/offers/?availableFrom=*&availableTo=*&q=workflowStatus:DRAFT
```

See Availability for more info.

## Examples

### Approved events in Mechelen
> Show only approved events that take place in city Mechelen

**params**
* URL param: `workflowStatus=APPROVED&regionId=gem-mechelen`

```
GET https://search.uitdatabank.be/offers/?workflowStatus=APPROVED&regionId=gem-mechelen
```

