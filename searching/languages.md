# Languages

All documents created in UiTdatabank are available in Dutch \(NL\). Besides Dutch, content editors can translate their documents in French \(FR\), German \(DE\) and English \(EN\).

To limit your results to documents that have translations for a specific language, you can use the `languages` URL parameter, or the `languages` field in [advanced queries](/advanced-queries.md).

Allowed values for both are:

* nl \(or NL\)
* fr \(or FR\)
* de \(or DE\)
* en \(or EN\)

## Url parameter

An example to get results that have a French translation:

```
GET https://search.uitdatabank.be/offers/?languages[]=fr
```

You can repeat this parameter to filter by multiple languages \(note that this uses the `AND` operator, so you will only get results that have translations for both languages\).

```
GET https://search.uitdatabank.be/offers/?languages[]=fr&languages[]=de
```

## Advanced queries

Using the `q` parameter, you can execute more [advanced queries](/advanced-queries.md) than by using the `languages` URL parameter.

For example:

```
GET https://search.uitdatabank.be/offers/?q=languages:fr OR languages:de
```

Note that while you can combine this with [free text search](/free-text-search.md), you will probably not get the intended results:

```
GET https://search.uitdatabank.be/offers/?q=languages:en the worst band ever
```

In the example above we're filtering documents to only search through those that have an EN translation and one or more matches with the words "the worst band ever". However, the word "worst" is also a Dutch word, and while we filtered the documents to only return results that have an English translation, the free text search will still look for text matches in all available languages on those \(filtered\) documents. So we might have an event that includes the word "worst" in Dutch and that also has an English translation, and it would be a valid result.

To fix this, you should use the `textLanguage` parameter as described in the [free text search](/free-text-search.md) documentation.

## Incomplete translations

Using either the URL parameter or advanced queries to filter by language\(s\), you might still get results that only have partial translations. This is because as soon as a single field is translated to a specific language, the whole document is considered to have a translation \(albeit an incomplete one\).

If you require specific fields to be translated, you can search for those documents by using [advanced queries](/advanced-queries.md) to check for the existence of a field translation:

```
GET https://search.uitdatabank.be/offers/?q=_exists_:name.fr AND _exists_:description.fr
```

The example above will filter out any documents that do not have both their `name` and `description` translated to French.

The same way, you can also search for documents that are missing translations for specific fields:

```
GET https://search.uitdatabank.be/offers/?q=!(_exists_:name.fr) OR !(_exists_:description.fr)
```

This will return all documents that are missing French translations for either `name` and/or `description`.

Alternatively, you use the `completedLanguages` URL parameter \(and field in [advanced queries](/advanced-queries.md)\) to only look for documents that are fully translated to a specific language.

```
GET https://search.uitdatabank.be/offers/?completedLanguages[]=fr
```

```
GET https://search.uitdatabank.be/offers/?q=completedLanguages:fr OR completedLanguages:de
```

Note that if an optional field is left empty in all languages, a translation can still be considered to be complete if all other fields that have a value are translated.

## Main Language

Traditionally, each document starts as Dutch and can then be translated to other languages. However, in the future the main language of a document might become configurable. To accommodate this, each document already has a `mainLanguage` property on which you can also search in the Search API.

For example:

```
GET https://search.uitdatabank.be/offers/?mainLanguage=nl
```

Or using [advanced queries](/advanced-queries.md):

```
GET https://search.uitdatabank.be/offers/?q=mainLanguage:nl
```