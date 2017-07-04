# Availability

Most events in UiTdatabank v3 have a limited availability, from the time they are published \(or their scheduled publication date has been reached\) until the end date of the event.

Places are considered to be permanently available, starting when they are published \(or, again, their scheduled publication date has been reached\). A small portion of the events is permanent as well, depending on their calendar information.

Note however, that an event's availability is not the same as the date and time that the event actually takes place. Instead, it is an indication of when the event can be shown on public output channels. **Generally, you will only want to search through events and places that are available right now**, unless you are building a backend in which users can create and edit their events and places, in which case they need to be able to view their events that are no longer available or will become available in the future.

Because of this, Search API v3 has default filters that hide any events or places that are considered to be either no longer available, or not available yet. However, you can disable these default filters, and even override them.

The API provides two parameters which are **both set to the current date and time by default**:

* `availableFrom` \(ISO-8601 datetime, eg. "2017-04-11T12:08:01+01:00"\)
* `availableTo` \(ISO-8601 datetime, eg. "2017-04-11T12:08:01+01:00"\)

**Note that the "+" sign should be encoded for URLs \(as %2B\)!** Otherwise it will be interpreted as whitespace and the given date time will be considered invalid.

## Retrieving all events and places regardless of availability

To search through all events and places regardless of their availability, you can disable the `availableFrom` and `availableTo` URL parameters by passing a wildcard `*` instead of an ISO-8601 datetime:

```
GET https://search.uitdatabank.be/offers/?availableFrom=*&availableTo=*
```

By disabling these filters, you will get all events and places that are currently available, as well as events and places that were available in the past or will be available in the future.

Alternatively you can disable all default filters at once, as described in [Default filters](/getting_started/default-filters.md):

```
GET https://search.uitdatabank.be/offers/?disableDefaultFilters=true
```

## Retrieving all currently available events and places, and those that were available in the past

To get all events and places that were available in the past as well as available right now, you can simply disable the `availableFrom` filter:

```
GET https://search.uitdatabank.be/offers/?availableFrom=*
```

Because the `availableTo` filter still uses the current date and time as the default value, this request can be interpreted as _"return everything that has been available up to this moment"_.

## Retrieving all currently available events and places, and those that will become available in the future

The other way around, you can disable the default `availableTo` filter to get all events and places that are available right now, as well as those that will become available at some point in the future:

```
GET https://search.uitdatabank.be/offers/?availableTo=*
```

Because the `availableFrom` filter still uses the current date and time as the default value, this request can be interpreted as _"return everything that is available at some point from now on"_.

## Using a custom availability range

Using the same `availableFrom` and `availableTo` parameters, you can get all events and places that were available in a given range in the past, or will be available in a given range in the future.

For example:

```
GET https://search.uitdatabank.be/offers/?availableFrom=2017-04-01T00:00:00%2B01:00&availableTo=2017-04-30T23:59:59%2B01:00
```

This will return all events and places that were, at some point, available in April 2017. \(Even if they were only available for a portion of April 2017, they will still get returned.\)

You can also disable on of the two, and still pass a custom date and time to the other.

For example:

```
GET https://search.uitdatabank.be/offers/?availableFrom=*&availableTo=2016-12-31T23:59:59%2B01:00
```

This will return all events and places that were, at some point, available before 2017.

## Advanced queries

You can also search by availability using [advanced queries](/reference/advanced-queries.md). **However! You should always reset the default **`availableFrom`** and **`availableTo`** if you want to search by availability in your advanced queries.**

To search by availability in advanced queries, you can use the `availableRange` field and either look for a specific date, or a range.

For example, the following request will return all events and places that were available on January 1st 2017 at midnight, using an advanced query:

```
GET https://search.uitdatabank.be/offers/?q=availableRange:2017-01-01T00:00:00%2B01:00&availableFrom=*&availableTo=*
```

The following example returns all events and places that were available at some point between January 1st 2017, and March 31st 2017, using an advanced query:

```
GET https://search.uitdatabank.be/offers/?q=availableRange:[2017-01-01T00:00:00%2B01:00 TO 2017-03-31T23:59:59%2B01:00]&availableFrom=*&availableTo=*
```

For more info, see the documentation for [advanced queries](/reference/advanced-queries.md).
