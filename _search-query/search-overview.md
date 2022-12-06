---
layout: default
title: Search your data
nav_order: 20
has_toc: true
has_children: true
redirect_from: /opensearch/ux/
---

# Search your data

To get information from your indexed data, you create a *search query*, or *query* to retrieve the specific information that you want to know about your data. OpenSearch provides a set of REST APIs that you can use to query your data streams and indexed data.

You create a query with parameters and fields that define the question you want to know.

Query your data to answer various categories of questions:

* **keyword searches** – Think of a typical keyword search to a search engine to return results that have been indexed. You can locate specific terms, or search an index for all documents that contain that term.
* **Performance issues** – Find out which processes are taking longer than 40 milliseconds to respond.
* **Monitor large file relocation operations** – Make sure that large groups of documents are not removed from your organization with a SQL selective aggregation query.

## Search methods and plugins

There are several methods to perform search queries with OpenSearch. You can perform a simple HTTP search, or you can create searches with more options using either of the query languages:
* [Query DSL]({{site.url}}{{site.baseurl}}/query-dsl/index) – Use a wider range of search options for your queries.
* [Piped processing language (PPL)]({{site.url}}{{site.baseurl}}/search-plugins/sql/ppl/index/) – Use pipe syntax to explore and discover your data.

You can also use the search plugins for specialized searches.

* [SQL plugin]({{site.url}}{{site.baseurl}}/search-plugins/sql/index) plugin – Write queries in SQL instead of using Query DSL.
* [Quergy plugin]({{site.url}}{{site.baseurl}}/search-plugins/quergy/index) – Rewrite queries to solve relevance issues and improve search engine optimization (SEO) to get precise matches and scores.
* [k-NN plugin]({{site.url}}{{site.baseurl}}/search-plugins/quergy/index)  – Search for k-nearest neighbors (k-NN) to a query point across an index of vectors. You can use the score script plugin for an exact search, or the k-NN plugin for an approximate search.
* [Asynchronous search plugin]({{site.url}}{{site.baseurl}}/search-plugins/async/index/)  – Use an asynchronous search across multiple remote clusters, or large volume datasets that will take a long time.

## How to run a search

Use the [search API]({{site.url}}{{site.baseurl}}/api-reference/search/) to run queries on data you've indexed with OpenSearch.

The following request queries an index of hotel documents that provide parking.

#### Sample request

```json
GET /hotels-index/_search
{
  "query": {
    "match": {
      "text_entry": "parking"
    }
  }
}
```

#### Sample response

```json
{
  "took" : 26,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 0,
      "relation" : "eq"
    },
    "max_score" : null,
    "hits" : [ ]
  }
}
```


## Custom search options

You can also use any of the custom search functions 

* [Autocomplete functionality]({{site.url}}{{site.baseurl}}/opensearch/search/autocomplete) – Suggest phrases as the user types.
* [Did-you-mean functionality]({{site.url}}{{site.baseurl}}/opensearch/search/autocomplete) – Check spelling of phrases as the user types.
* [Paginate results]({{site.url}}{{site.baseurl}}/opensearch/search/paginate) – Rather than a single, long list, separate search results into pages.
* [Sort results]({{site.url}}{{site.baseurl}}/opensearch/search/sort) | Allow sorting of results by different criteria.
* [Highlight query matches]({{site.url}}{{site.baseurl}}/opensearch/search/highlight) – Highlight the search term in the results.