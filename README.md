RedGreenGrid
============

A baseline grid for the web. Based on an original concept from 2014.

Background
----------

I stopped working on it as it got too complex. While this was a
technical problem, I still like the concept. I also like readme driven
development. So here’s my idea, maybe I’ll use it to rewrite the gem.
The original version is still available in the [master 
branch](https://github.com/hagenburger/redgreengrid/tree/master).


Concept
-------

![visualisation](https://cdn.rawgit.com/hagenburger/redgreengrid/restart/visualisation.svg)


Technical Implementation
------------------------

There’s a nice post on
[aligning Sass to the baseline grid](https://medium.com/p/e258fce47a9b)
by [@razvanonofrei](https://twitter.com/razvanonofrei). It builds a 
traditional baseline grid. It can be adopted our needs easily. Three
things are missing:

  * Margins (the current implementation makes it impossible)
  * The red grid in the visualisation above
  * The right cap height

The first two issues can be solved, the second one is hard work each
time. So it would be nice to have the data collected in a gem—easily
extendable by pull requests.

The API could look like:

``` scss
$redgreengrid: (
  base-font-size: 14px,
  base-line-height: 1.5
);

.example {
  @include font(helvetica-neue, 14px);
}
```


Feedback
--------

Let me know your feedback on [my Twitter
account](https://twitter.com/hagenburger) or just [open an 
issue](https://github.com/hagenburger/redgreengrid/issues/new).

