VoidyBootstrap
==============

A `Bootstrap 3 <http://getbootstrap.com>`_ blog theme for the
`Pelican <http://getpelican.com>`_ static site generator.

A blog theme that aims to be mobile friendly, responsive and easily
customisable.  On larger screens it provides a clean 2 column layout, with
a Jumbotron and navbar containing page links at the top, categories and
tag-cloud in the sidebar, and `Font Awesome 4 <http://fontawesome.io/>`_
icons.

First and foremost this theme is designed to be usable right out of the
box with minimal configuration, and all the common features expected in a
modern blog -- albeit with the ubiquitous Bootstrap look and feel.

But it's mostly intended to be a sane starting point for building custom
Boostrap-based themes for Pelican -- with all the usual scaffolding and
fiddly bits already taken care of.


Installation
------------

Clone this repo, then in your ``pelicanconf.py`` set the ``THEME`` variable
to point to it::

  THEME = 'path/to/voidy-bootstrap/'

Out of the box what you get is the stock standard Bootstrap 3 look.  To
customise things see below.


Example Settings
----------------

All of these are optional, but here is a basic example of common variables
that you might want to configure

The following should be set in ``pelicanconf.py``::

  SITESUBTITLE ='Sub-title that goes underneath site name in jumbotron.'
  SITETAG = "Text that's displayed in the title on the home page."

  # Extra stylesheets, for bootstrap overrides or additional styling.
  STYLESHEETS = ("pygment.css", "voidybootstrap.css",)

  # Use the default sharing button implementation.
  CUSTOM_ARTICLE_SHARING = "sharing.html"
  CUSTOM_ARTICLE_SCRIPTS = "sharing_scripts.html"


The following are probably better suited for ``publishconf.py``::

  FEED_DOMAIN = SITEURL
  FEED_ALL_ATOM = 'feeds/all.atom.xml'

  DISQUS_SITENAME = "disqussitename"
  GOOGLE_ANALYTICS = "UA-xxxxxxxxxx"
  GOOGLE_ANALYTICS_SITEID = "gasiteid"
  TWITTER_USERNAME = "twitterusername"



Basic Configuration and Customisation
-------------------------------------

By default all required CSS and JavaScript files are downloaded from a CDN.
Note how little is supplied in the theme's ``static/css``.  Just a
``pygment.css`` file, and a sample css file (``voidybootstrap.css``) with
very minimal styling is provided as a starting point.

The simplest way to customise things is just to override the standard
Bootstrap styles as necessary.  The theme intentionally avoids loading any
local stylesheets by default.  Instead, any local stylesheets must be
explicitly specified using the ``STYLESHEETS`` setting.  ``STYLESHEETS`` is
an array for listing all the local stylesheets that should be loaded by the
``base.html`` template.  Place any CSS stylesheet files you may require in
``static/css`` and add the filenames to the ``STYLESHEETS`` array in 
``pelicanconf.py``

As a starting point, my suggestion is to rename the supplied
``voidybootstrap.css`` to something more appropriate (like ``custom.css``),
then use it as a base for your own modifications and custom styling.  In
this case, you would need something like this in your ``pelicanconf.py``::

  STYLESHEETS = ("pygment.css", "custom.css",)


Custom Bootstrap
----------------

As an alternative, or in addition, it's possible to easily replace the
standard Bootstrap file with a customised local one.  The
``MAIN_LOCAL_STYLESHEET`` setting is provided for this.  If this variable
is not set, the standard ``bootstrap.min.css`` will be used, from a CDN.  

Otherwise, set ``MAIN_LOCAL_STYLESHEET`` to the name of a local style to
use that stylesheet instead of the standard Bootstrap CSS.  

For example, you could use the `Bootstrap customizer
<http://getbootstrap.com/customize/>`_ to create your own customised css
file.  Place that file in ``static/css`` and set ``MAIN_LOCAL_STYLESHEET``
to be the filename.  

Similarly, a `Bootswatch <http://bootswatch.com/>`_ theme can be easily
integrated.  Select a theme and download the files.  Place all the
necessary CSS files in ``static/css``.  Set ``MAIN_LOCAL_STYLESHEET`` to
the filename of the main Bootstrap file, and put any additional CSS files
in the ``STYLESHEETS`` array.



Settings
--------

All of these settings are optional.


``SITESUBTITLE``
  Sub-title -- displayed in jumbotron.

``SITETAG``
  Text that will be placed in the title on the home page.

``DEFAULT_METADESC``
  Default value for HTML meta description tag.  Individual articles and
  pages can specify their own meta description by using the theme's custom
  ``description`` metadata tag.

``MAIN_LOCAL_STYLESHEET``
  Local Bootstrap CSS file, as described above.

``STYLESHEETS``
  An array for listing all the local stylesheets that should be loaded by
  the ``base.html`` template, as described above.

``TWITTER_USERNAME``
  Set to a valid Twitter username to enable the twitter sharing button.

``OPEN_GRAPH``
  Set to True to enable Facebook Open Graph meta-properties.

``OPEN_GRAPH_FB_APP_ID``
  Facebook App ID

``OPEN_GRAPH_ARTICLE_AUTHOR``
  Value for Open Graph ``article:author`` property, which will be set on
  article pages.

``OPEN_GRAPH_IMAGE``
  Default value for Open Graph ``og:image`` property.
  Posts can use the custom ``og_image`` metadata tag to specify a
  per-article page value.



Custom Includes
---------------

The following variables (all optional), if specified, should be set to 
paths for template fragments that will be included at strategic points
from the primary templates.  All paths must be relative to the theme's 
``templates/includes`` directory.

``CUSTOM_ARTICLE_SHARING``
  Template fragment for custom social media sharing buttons.  
  Included in ``article.html`` at the bottom of the article, after
  ``article_end.html`` but before ``article_bottom.html``.
  Set to ``includes/sharing.html`` to use the default provided implementation.

``CUSTOM_ARTICLE_SCRIPTS``
  Template fragment for any javascript code necessary for article pages
  (namely code for any social media sharing buttons).  
  Will be included right at the bottom of article pages, just before the
  closing body tag.  Set to ``includes/sharing_scripts.html`` to use the 
  default provided implementation.

``CUSTOM_ARTICLE_HEADER``
  Replaces the default article header in ``includes/article_header.html`` 
  with a custom implementation on *article pages only*.

``CUSTOM_ARTICLE_HEADER_INDEX``
  Replaces the default article header in ``includes/article_header.html`` 
  with a custom implementation on *index pages only*.

``CUSTOM_ARTICLE_PREHEAD``
  Template fragment for content just before main article heading.
  (e.g. date)

``CUSTOM_ARTICLE_POSTHEAD``
  Template fragment for content right after main article heading.
  (e.g. author, category, etc)

``CUSTOM_SIDEBAR``
  Don't like the sidebar provided by the theme?  Have something totally 
  different in mind?  Well then you're in luck.  Build your own sidebar 
  template (you can use ``includes/sidebar.html`` as a starting point), 
  and set ``CUSTOM_SIDEBAR`` to point to it -- this  completely replaces 
  the default sidebar with your custom sidebar.



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


Screenshot
----------

.. image:: screenshot.png
   :alt: Screenshot of VoidyBootstrap theme with default Bootstrap 3 styling.


License
-------

Licensed under the `MIT License <http://opensource.org/licenses/MIT>`_

Feel free to use as-is or as a basis for your own custom theme.
