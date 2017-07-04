# Authentication

To use Search API v3, you need to authenticate using an API key on every request.

You can add your API key to a request in two ways:

* As a query parameter
* In a custom `X-Api-Key` header

\[@stan Info over projectaanvraag etc toevoegen.\]

## Query parameter

You can add an `apiKey` parameter like this:

```
GET https://search.uitdatabank.be/offers/?apiKey=<your api key here>
```

For example:

```
GET https://search.uitdatabank.be/offers/?apiKey=c7c95c31-93b0-4a3b-8758-770e76d5ed46
```

## Request header

You can send your API key as a separate header like this \(for example using `curl`\):

```
curl -H "X-Api-Key: <your api key here>" http://udb-search.dev/offers/
```

For example:

```
curl -H "X-Api-Key: c7c95c31-93b0-4a3b-8758-770e76d5ed46" http://udb-search.dev/offers/
```



