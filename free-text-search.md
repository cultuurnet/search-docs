# Free text search

Using either the `text` and the `q` URL parameters, you can search for text across multiple pre-defined fields:

```
GET https://search.uitdatabank.be/offers/?text=dit is een test
```

```
GET https://search.uitdatabank.be/offers/?q=dit is een test
```

The main difference between the two is that `q` allows you to search through other fields than the pre-defined free text search fields.

For example, the following queries will NOT return the same results:

```
GET https://search.uitdatabank.be/offers/?text=labels:Paspartoe
```

```
GET https://search.uitdatabank.be/offers/?q=labels:Paspartoe
```

In this example, the `text` parameter will look for documents that have the string `labels:Paspartoe` in them, while the `q` parameter will look for documents that actually have the label `Paspartoe`.

See [advanced queries](/advanced-queries.md) for more info on the `q` parameter.

## Fields

The following fields will be searched when using either the `text` parameter, or the `q` parameter with free text:

`id`, `name`, `description`, `labels`, `terms.id`, `terms.label`, `performer.name`, `addressLocality`, `postalCode`, `streetAddress`, `location.id`, `location.name`, `organizer.id`, `organizer.name`

**Important notes:**

* IDs only return results if the complete ID is given in the free text input.
* Searching for a part of a word is not supported at the time of writing. For example, searching for `Fiets` will not return an event with the title `Fietsen langs de Dijle`.

## Operators

By default the `OR` operator is used in between multiple given words.

So the query `wandelen fietsen dijle` actually becomes `wandelen OR fietsen OR dijle`.

It is possible to define the operator you want to use in the query itself.  
You could, for example, search for:

```
GET https://search.uitdatabank.be/offers/?text=(wandelen OR fietsen) AND dijle
```

See the [Query String Query syntax for ElasticSearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax) for more info, or more documentation on [advanced queries](/advanced-queries.md).

Note: if you want to specify the fields you want to search on, or search through fields that are not included by default, you should use the `q` parameter.

## Exact matches

By default the free text search looks for one or more matches with any of the given terms, regardless of their order and/or position in the document's text.

For example, both an event with the title `Lekker veggie` and a different event with the title `Veggie eten is lekker` would be returned as results when searching for `text=lekker veggie`.

To limit the results to exact matches, encapsulate the given search terms with quotes:

```
GET https://search.uitdatabank.be/offers/?text="lekker veggie"
```

This will only return results that have `lekker veggie` in exactly that order in their text.

Encapsulated terms can still be combined with other terms, for example:

```
GET https://search.uitdatabank.be/offers/?text="lekker veggie" eten bereiden klaarmaken
```

## Localization \(Translations\)

By default the free text search looks for matching terms in both the original documents and their translations.

To limit your free text queries to one or more specific languages, you can use the `textLanguages` URL parameter.

```
GET https://search.uitdatabank.be/offers/?text="the editors"&textLanguages[]=nl
```

You can search through multiple languages by repeating the same parameter with a different value:

```
GET https://search.uitdatabank.be/offers/?text="the editors"&textLanguages[]=nl&textLanguages[]=fr
```

Note that the `textLanguages` parameter does not filter documents by their available languages. For example, when searching in both `nl` and `fr`, you can get results that only have either one language but still have a matching term in that specific language.

To actually filter documents by their available languages, see [Languages](/languages.md).


## Examples

### Search for "DJ Shadow"
> All offers that contain the string "DJ Shadow" in one of the following fields: title, description, labels, organizer


**params**
* Advanced query: `q="DJ Shadow"`
* URL param: `text="DJ Shadow"`

```
GET https://search.uitdatabank.be/offers/?q="DJ Shadow"&embed=true
```

