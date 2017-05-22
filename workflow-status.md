# Workflow status

You can search by workflow status using two methods:

* URL parameter
* Advanced queries


## URL parameter

You can filter by an exact match using the `workflowStatus` URL parameter:

```
GET https://search.uitdatabank.be/offers/?workflowStatus=DRAFT
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `workflowStatus` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=workflowStatus:DRAFT or workflowStatus:READY_FOR_VALIDATION
```

For more info, see the [advanced queries documentation](/advanced-queries.md).

## Allowed values

A workflow status can be any of the following values \(case-insensitive\):

* DRAFT
* READY\_FOR\_VALIDATION
* APPROVED
* REJECTED
* DELETED

By default offers with workflow status 'DRAFT', 'REJECTED' and 'DELETED' are filtered from the results

## Examples

### Approved events in Mechelen
> Show only approved events that take place in city Mechelen

**params**
* URL param: `workflowStatus=APPROVED&regionId=gem-mechelen`

```
GET https://search.uitdatabank.be/offers/?workflowStatus=APPROVED&regionId=gem-mechelen
```

