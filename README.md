RedGreenGrid
============

***Early alpha version. Internet Explorer not finished yet.***

A Compass plugin for all those who love typography.
RedGreenGrid provides a cross browser baseline grid for Helvetica, Arial, Verdana and Lucida Grande.
Other fonts can be easily added.

There are two grids:

- **Green**: The baseline grid for all text
- **Red**: The grid for all other elements (design, photos, boxes, …)

Why two grids? 
The answer is easy: I wouldn’t look good with only one.
With a red and a greed grid, it’s very easy to create well-balanced layouts from the scratch.


Example
-------

Add to your screen.sass:

    // import basics
    @import redgreengrid/redgreengrid.sass
    // set font family
    @import redgreengrid/typography/helvetica.sass
    // add RedGreenGrid
    +rgg
    // add styles to show the baseline grid
    +rgg-development
    
Add to your layout/application.html.haml:

    %body{ :class => browser_class }
      = redgreengrid


Font Sizes
----------

A RedGreenGrid based layout should have three font sizes: normal, big, huge.
You can define which CSS selectors will get which size.
Here’s the default.
Be sure to place your changes on top of the @imports:

    !rgg_normal = "p, li, dt, dd, td, th, h3, h4, h5, h6, address"
    !rgg_big    = "h2, legend"
    !rgg_huge   = "h1"
    
    @import redgreengrid/redgreengrid.sass
    @import redgreengrid/typography/helvetica.sass
    +rgg




Implementations Details
=======================


Mix-Ins
-------

Maybe you’ll ask, why font size selectors aren’t implemented as mix-in?
That’s because it needs a lot of browser fixes which can’t be done easily with mix-ins and would generate a lot of duplicate code.
Let’s stay DRY.


Browser Fixes
-------------

To make happy all of you who hate * or _ hacks,
to get standards compliant CSS files
and to avoid separate IE files (we would need separate Safari, Firefox and Opera files)
browser fixes are made with a browser super class:

    .webkit h1
      :fixes
    .gecko p, .presto p
      :fixes
    .trident h2
      :fixes
      
This browser superclass should be placed in the `<body>` tag.
RedGreenGrid provides a helper method `browser_class` for this task.

The following classes will be created:

* **.webkit** – Safari, Google Chrome
* **.gecko** – Firefox, Mozilla
* **.trident** – Windows Internet Explorer
* **.presto** – Opera
* **.other-browser**


Baseline Adjustments
--------------------

Each font size must be adjusted to the baseline on each browser.
I’ve did this by `position: relative`.
There are two mix-ins which help you for this job:

    +up(1px)
    +down(2px)




Extend RedGreenGrid
===================


Changes to Font Size and Line Height
------------------------------------

The default line height is 20px.
If you want to change the font size or line height:

1. copy the SASS file of your preferred font family
2. change the sizes
3. name the file `_<font-family>_<font-size>_<line-height>.sass`
4. test it and fix it for “all” browsers
5. make a pull request for RedGreenGrid to share it


Add New Font Families
---------------------

Do it the same way like new font sizes/line heights.


Bug Fixes
---------

Feel free to make a pull request.


Suggestions, Ideas, Critics
---------------------------

I love to hear from you.
Just drop me a mail to nico .. hagenburger .. net.
Follow me on [Twitter](http://twitter.com/Hagenburger).



Copyright (c) 2009 Nico Hagenburger <http://www.hagenburger.net>, released under the MIT license
