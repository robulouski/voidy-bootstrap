VoidyBootstrap
==============

A `Bootstrap 3 <http://getbootstrap.com>`_ blog theme for the
`Pelican <http://getpelican.com>`_ static site generator.

A blog theme that aims to be mobile friendly, responsive and easily
customisable.  On larger screens it provides a clean 2 column layout, with
a Jumbotron and navbar containing page links at the top, and categories and
tag-cloud in the sidebar.

First and foremost this theme is designed to be usable right out of the
box with minimal configuration, and all the common features expected in a
modern blog -- albeit with the ubiquitous Bootstrap look and feel.

But it's mostly intended to be a sane starting point for building custom
Boostrap-based themes for Pelican -- with all the usual scaffolding and
fiddly bits already taken care of.


Configuration
-------------

TBD


Settings
--------

SITESUBTITLE
  Sub-title -- displayed in jumbotron.

SITETAG
  Text that will be placed in the title on the home page.

DEFAULT_METADESC

MAIN_LOCAL_STYLESHEET

STYLESHEETS

TWITTER_USERNAME

OPEN_GRAPH 

OPEN_GRAPH_FB_APP_ID 

OPEN_GRAPH_ARTICLE_AUTHOR 

OPEN_GRAPH_IMAGE





Custom Includes
---------------

CUSTOM_ARTICLE_SHARING

CUSTOM_ARTICLE_SCRIPTS 


::

  CUSTOM_ARTICLE_SHARING = "sharing.html"
  CUSTOM_ARTICLE_SCRIPTS = "sharing_scripts.html"



Optional Templates
------------------

If the following templates are provided, they must be placed in an
``includes`` subdirectory.

article_top.html
  Included by ``article.html`` before the article section.  Can be used 
  to provide things like pagination, breadcrumbs, ads, etc.

article_end.html
  Included by ``article.html`` right after the article contents.  There
  is a default implementation provided, which displays a tag-list.

article_bottom.html
  Included by ``article.html`` after the article content, after any 
  social media sharing buttons, but before disqus comments.  

footer.html
  Included by ``base.html``.  Anything here (e.g. copyright text) will
  appear between footer tags at the bottom of every page.

index_meta.html
  Included by ``index.html`` between the head tags.  Can be used 
  to add extra HTML meta tags to index pages, for example.

sidebar_top.html
  Included by ``sidebar.html`` at the top of the sidebar.  Provides a
  convenient place for an "about" blurb, for example.

sidebar_bottom.html
  Included by ``sidebar.html`` at the bottom of the sidebar.



Author
------

| Robert Iwancz
| www.voidynullness.net
| ``@robulouski``


License
-------

Licensed under the `MIT License <http://opensource.org/licenses/MIT>`_

Feel free to use as-is or as a basis for your own custom theme.
