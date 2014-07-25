---
layout: home
title: Linked APIs
---

# Linked APIs

> A Linked API is an API that uses URLs [[RFC1738](http://www.ietf.org/rfc/rfc1738.txt)] as primary identifiers of data entities, and for references to connected entities.

The benefit of using URLs is that we can deterministically fetch an entity representation from anywhere on the web. Usage of URLs for identifiers and for referencing, as opposed to: synthetic keys or other types of internal pointers, allows data entities to be externalized and  linked across organizational boundaries, thus connecting API providers and breaking data silos.

### Linked APIs vs. Hypermedia APIs.

Linked APIs style of API design focuses on [unbundling](http://www.vox.com/2014/6/24/5840248/the-powerful-economic-principle-behind-yo) of data storage from the interface, in APIs, which has the affect of allowing APIs to operate on data-sets that are distributed across organizational boundaries. The benefit of such design is better distribution of responsibilities among data-set owners and API publishers

Hypermedia style of API design focuses on "simultaneous presentation of information and controls such that the information becomes the affordance through which the user obtains choices and selects actions"<sup><a href="#fn1" id="ref1">1</a></sup>. The benefit of such design is increased flexibility and adaptability over time.  

Both of the styles use hypermedia controls (e.g. hyperlinks) extensively so they are very complementary, but still orthogonal in their design focus.

### Motivation

Linked APIs are a novel breed of APIs that fix a significant flaw with the current generation of APIs.

The problem with the current APIs is that: most APIs are, at best, creating narrow windows into solid walls surrounding the silo-ed data islands. Even the most well-known and large APIs – such as those provided by Twitter, Facebook or Google – only operate on the data that is within their own databases.

To take Twitter as the example: there is a lot that you can do with their public API; but in the end all of the created content always resides on Twitter's servers. The same is true for Facebook, of course. 

In that sense, current APIs create isolated, guarded data islands in the universe of the web. Which is very "anti-web" — the web was created in the spirit of decentralized equal participation. On the web, everybody publishes everywhere, owns their data, and then we have ways to reach that data through hyperlinks, rss feeds, activity streams, Google search and other methods. APIs have not really reached that stage of maturity, yet. APIs are highly centralized, in terms of data storage, and virtually none of them ever link to other APIs.

We need APIs that link to each other. Hyperlinks were essential for the growth of human web. They are equally essential for the Internet of Things ahead of us. 

We can only truly have open and free data, if we jail-brake the data out of the silos that data is stashed-away at, currently. Linked APIs are the key to data freedom on the web. They are the engine of that freedom. 

Let's get the engine cranking!

### Example

#### A Linked API Response

```json
{ "href"  : "http://mydomain.com/posts/linked-apis-definition",
  "title" : "A Blog Post About Something",
  "links" : [
              {"rel" : "author", "href" : "http://api.our-company.com/authors/johndoe"},
              {"rel" : "series", "href" : "http://api.different-company.org/someseries"}
            ]
}
```     

#### A Siloed API Response

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

#### An [UBER](https://rawgit.com/mamund/media-types/master/uber-hypermedia.html) Response That Is Not a Linked API Response.

```json
{ "uber": {
    "version" : "1.0",
    "data" : [
      { "name" : "article_id", "value" : 58321 },
      { "name" : "title", "value" : "A Blog Post About Something" },
      { "name" : "author",
        "data" : [
          { "name" : "username", "value" : "johndoe"  },
          { "name" : "name",     "value" : "John Doe" },
          { "name" : "id",       "value" : 14912949 }
        ]
      },
      { "name" : "series", "value" : 394 }
    ]    
  }
}
```

#### An [UBER](https://rawgit.com/mamund/media-types/master/uber-hypermedia.html) Response That Is A Linked API.


```json
{ "uber": {
    "version" : "1.0",
    "data" : [
      { "rel"  : ["self"],    "url" : "http://mydomain.com/posts/linked-apis-definition" },
      { "name" : "title",   "value" : "A Blog Post About Something" },
      { "rel"  : ["author"],  "url" : "http://api.our-company.com/authors/johndoe" },
      { "rel"  : ["series"],  "url" : "http://api.different-company.org/someseries" }
    ]    
  }
}
```

### How To Contribute

If you find a typo, or have a suggestion about this document, please either submit a pull request to the [Github Repo](https://github.com/inadarei/linkedapis) where this page is hosted, or open an [issue request](https://github.com/inadarei/linkedapis/issues)

-----------------------

### Have Feedback? Leave a Comment:

<div id="disqus_thread"></div>
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
    var disqus_shortname = 'linkedapis'; // required: replace example with your forum shortname

    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
<a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>


-----------------------

#### References

<sup id="fn1">1.</sup> Roy T. Fielding [Architectural Styles and
the Design of Network-based Software Architectures](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)

-----------------------

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">Linked APIs Definition</span> was originally coined by <a xmlns:cc="http://creativecommons.org/ns#" href="https://twitter.com/inadarei" property="cc:attributionName" rel="cc:attributionURL">Irakli Nadareishvili</a>  and is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

Contributors: [Mike Amundsen](https://twitter.com/mamund)