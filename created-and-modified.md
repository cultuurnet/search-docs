# Metadata

UiTdatabank v3 keeps track of offer creation en modification dates. This metdata can be queried with the following parameters:

* `createdFrom` \(ISO-8601 datetime, eg. "2017-04-01T12:08:01+01:00"\)
* `createdTo` \(ISO-8601 datetime, eg. "2017-04-20T12:08:01+01:00"\)
* `modifiedFrom` \(ISO-8601 datetime, eg. "2017-04-01T12:08:01+01:00"\)
* `modifiedTo` \(ISO-8601 datetime, eg. "2017-04-10T12:08:01+01:00"\)

**Note that the "+" sign should be encoded for URLs \(as %2B\)!** Otherwise it will be interpreted as whitespace and the given date time will be considered invalid.

## Retrieving all offers created or modified on or after a specific date

To find all offers that were `modified` or `created` on or after a specific date and time, use the `createdFrom` or `modifiedFrom` query parameters.

```
From: 2017-04-11T12:08:01+01:00
GET https://search.uitdatabank.be/offers/?createdFrom=2017-04-11T12:08:01%2B01:00
GET https://search.uitdatabank.be/offers/?modifiedFrom=2017-04-11T12:08:01%2B01:00
```

## Retrieving all offers created or modified on or before a specific date

To find all offers that were `modified` or `created` on or before a specific date and time, use the `createdTo` or `modifiedTo` query parameters.

```
To: 2017-04-11T12:08:01+01:00
GET https://search.uitdatabank.be/offers/?createdTo=2017-04-11T12:08:01%2B01:00
GET https://search.uitdatabank.be/offers/?modifiedTo=2017-04-11T12:08:01%2B01:00
```

## Advanced queries

You can also search on `created` or `modified` using [advanced queries](/advanced-queries.md).

For example to search for all offers created on or after a specific date use the following query:

```
GET https://search.uitdatabank.be/offers/?q=created:[2017-04-11T12:08:01%2B01:00 TO *]
```

The next example searches for all offers modified before or on a specific date:

```
GET https://search.uitdatabank.be/offers/?q=modified:[* TO 2017-04-11T12:08:01%2B01:00]
```



