# PyMed - PubMed Access through Python
PyMed is a Python library that provides access to PubMed through the PubMed API.

## Why this library?
The PubMed API is not very well documented and querying it in a performant way is too complicated and time consuming for researchers. This wrapper provides access to the API in a consistent, readable and performant way.

## Features
This library takes care of the following for you:

- Querying the PubMed database (with the standard PubMed query language)
- Batching of requests for better performance
- Parsing and cleaning of the retrieved articles

## Examples
For full (working) examples have a look at the `examples/` folder in this repository. In essence you only need to import the `PubMed` class, instantiate it, and use it to query:

```python
from pymed import PubMed
pubmed = PubMed(tool="MyTool", email="my@email.address")
results = pubmed.query("Some query", max_results=500)
```

## Notes on the API
The original documentation of the PubMed API can be found here: [PubMed Central](https://www.ncbi.nlm.nih.gov/pmc/tools/developers/). PubMed Central kindly requests you to:

> - Do not make concurrent requests, even at off-peak times; and
> - Include two parameters that help to identify your service or application to our servers
>   * _tool_ should be the name of the application, as a string value with no internal spaces, and
>   * _email_ should be the e-mail address of the maintainer of the tool, and should be a valid e-mail address.

## Notice of Non-Affiliation and Disclaimer 
The author of this library is not affiliated, associated, authorized, endorsed by, or in any way officially connected with PubMed, or any of its subsidiaries or its affiliates. The official PubMed website can be found at https://www.ncbi.nlm.nih.gov/pubmed/.

## Information about this fork

Fixes:

* PMID issue (https://github.com/gijswobben/pymed/issues/22): fixed. The `paper.pubmed_id` attribute is now correct.
* Incomplete titles and/or abstracts (https://github.com/gijswobben/pymed/issues/23): fixed in most of cases.
* Retrieves only the english version of abstracts (some papers have multiple version for different languages).

Features:

* Adds `publication_type` field to PubMedArticle (it is a list since there are more types for each article).
* Adds `keyowrds` field to the `PubMedBookArticle`.
* Improves `PubMedBookArticle` title semantics.

Debugging:

* Adds a debug_dump_xml flag to dump the retrieved xml; it's also saved in case of xml ParseError.
