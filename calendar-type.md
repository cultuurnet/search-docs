# Calendar type

All events and places in UiTdatabank v3 have one of four calendar types:

* **Single**: The event occurs on a single date, indicated by a single `startDate` and `endDate`
* **Multiple**: The event occurs on multiple dates, and has multiple `subEvent` entries with each a different `startDate` and `endDate`
* **Periodic**: The event or place runs for a specific period as indicated by its `startDate` and `endDate`, and can optionally have `openingHours`.
* **Permanent**: The event or place is permanent and has **no** `startDate` or `endDate`, but it can optionally have `openingHours`.

You can search through all of these types [by searching by date and time](/date.md), but you can also limit your results by their `calendarType`.

## URL parameter

Using the `calendarType` URL parameter, you can limit the results you get back to a single type:

```
GET https://search.uitdatabank.be/offers/?calendarType=single
```

Additionally, you can limit the results to documents that have either one of multiple `calendarType` values:

```
GET https://search.uitdatabank.be/offers/?calendarType=single,multiple
```

Delimiting the `calendarType` parameter using a comma works as if using an `OR` operator.

## Advanced queries

Using [advanced queries](/advanced-queries.md), you can make more complex combinations than using the calendarType URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=calendarType:single OR calendarType:multiple
```

```
GET https://search.uitdatabank.be/offers/?q=!(calendarType:permanent)
```

For more info, see [advanced queries](/advanced-queries.md).


## Examples

### All non-recurring events in Ghent
> return events with calendarType 'single' or calendarType 'multiple' in Ghent to get a list of events that only have one or a few occurences


**params**
- Advanced query: `q=((calendarType:single OR calendarType:multiple) AND regions:gem-gent)`

```
GET https://search.uitdatabank.be/events/?q=((calendarType:single OR calendarType:multiple) AND regions:gem-gent)&embed=true
```

### Exclude permanent events
> exclude events with a specific calendartype

- Advanced query: `q=!(calendarType:permanent)`

```
GET https://search.uitdatabank.be/events/?q=!(calendarType:permanent)
```