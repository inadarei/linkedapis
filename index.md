---
layout: home
title: Linked APIs
---

# Linked APIs

> A Linked API is a [Hypermedia API](http://www.infoq.com/articles/hypermedia-api-tutorial-part-one) that uses full URIs as primary identifiers of data items, as well as: to establish connections between various data items in the API.

Usage of dereferenceable URIs for identifiers and for referencing, as opposed to: synthetic keys or other types of internal pointers, allows any data item to be externalized and  linked across organizational boundaries, thus connecting API providers and breaking data silos.

All Linked APIs must be a Hypermedia API, but not all Hypermedia APIs are Linked APIs.

### Motivation

Linked APIs are a novel breed of APIs that fix a significant flaw with the current generation of APIs.

The problem with the current APIs is that: most APIs are, at best, creating narrow windows into solid walls surrounding the silo-ed data islands. Even the most well-known and large APIs – such as those provided by Twitter, Facebook or Google – only operate on the data that is within their own databases.

To take Twitter as the example: there is a lot that you can do with their public API; but in the end all of the created content always resides on Twitter's servers. The same is true for Facebook, of course. 

In that sense, current APIs create isolated, guarded data islands in the universe of the web. Which is very "anti-web" — the web was created in the spirit of decentralized equal participation. On the web, everybody publishes everywhere, owns their data, and then we have ways to reach that data through hyperlinks, rss feeds, activity streams, Google search and other methods. APIs have not really reached that stage of maturity, yet. APIs are highly centralized, in terms of data storage, and virtually none of them ever link to other APIs.

We need APIs that link to each other. Hyperlinks were essential for the growth of human web. They are equally essential for the Internet of Things ahead of us. 

We can only truly have open and free data, if we jail-brake the data out of the silos that data is stashed-away at, currently. Linked APIs are the key to data freedom on the web. They are the engine of that freedom. 

Let's get the engine cranking!

### Example

#### A Linked API

```json
{ "href"  : "http://mydomain.com/posts/linked-apis-definition",
  "title" : "A Blog Post About Something",
  "links" : [
              {"rel" : "author", "href" : "http://api.our-company.com/authors/johndoe"},
              {"rel" : "series", "href" : "http://api.different-company.org/someseries"}
            ]
}
```     

#### A Siloed API

```json
{ "article_id" : 58321,
  "title"      : "A Blog Post About Something",
  "author"     : {
      "username": "johndoe",
      "name": "John Doe",
      "id": 14912949
  }, 
  "series" : 394
}
```     


-----------------------

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">Linked APIs Definition</span> was originally coined by <a xmlns:cc="http://creativecommons.org/ns#" href="https://twitter.com/inadarei" property="cc:attributionName" rel="cc:attributionURL">Irakli Nadareishvili</a>  and is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

Contributors: [Mike Amundsen](https://twitter.com/mamund)