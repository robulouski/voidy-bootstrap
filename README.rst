VoidyBootstrap
==============

A `Bootstrap 3 <http://getbootstrap.com>`_ blog theme for the
`Pelican <http://getpelican.com>`_ static site generator.

This theme aims to be mobile friendly, responsive and easily customisable.

Configuration
-------------

TBD

::

  CUSTOM_ARTICLE_SHARING = "sharing.html"
  CUSTOM_ARTICLE_SCRIPTS = "sharing_scripts.html"



Custom Includes
---------------

CUSTOM_ARTICLE_SHARING

CUSTOM_ARTICLE_SCRIPTS 



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
  Included by ``sidebar.html`` at the top of the sidebar.

sidebar_bottom.html
  Included by ``sidebar.html`` at the bottom of the sidebar.



Author
------

Robert Iwancz
www.voidynullness.net
Twitter: @robulouski
