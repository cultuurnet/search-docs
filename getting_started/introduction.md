# Introduction

This documentation provides an overview of all public features available in CultuurNet's Search API v3 for UiTdatabank.

The API is available at the following urls:

* Production: [https://search.uitdatabank.be](http://search.uitdatabank.be)
* Test environment: [https://search-test.uitdatabank.be](http://search-test.uitdatabank.be)

## Building the docs

To build these docs on your local machine, install `gitbook` using `npm`:

```bash
npm install gitbook-cli -g
```

When finished, navigate to a clone of this repository on your local machine and run:

```bash
gitbook install # to install plugins like the API docs theme
gitbook serve
```

You can then view the docs by navigating to [http://localhost:4000](http://localhost:4000).

## Making changes

It is recommended to use the [GitBook Editor](https://www.gitbook.com/editor) to make changes to the docs.

Create a directory structure like this on your system, where `udb3-search-docs` is a clone of this repository:

```
GitBooks/Import/udb3-search-docs 
```

Now open the GitBook Editor application and click `Change Library Path...` under the `GitBook Editor` menu item. Navigate to the `GitBooks` directory in the dialog that opens, and open that directory in GitBook Editor as the library.

You should now be able to open `udb3-search-docs` from your GitBook Editor library window.

When you're done making changes, run the following command in the `udb3-search-docs` directory:

```bash
git push origin
```



