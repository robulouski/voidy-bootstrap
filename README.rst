VoidyBootstrap
==============

A `Bootstrap 3 <http://getbootstrap.com>`_ blog theme for the
`Pelican <http://getpelican.com>`_ static site generator.

A blog theme that aims to be mobile friendly, responsive and easily
customisable.  On larger screens it provides a clean 2 column layout.  At
the top there's a navbar containing page links, and jumbotron area.  The
sidebar has category links and a tag-cloud.  `Font Awesome 4
<http://fontawesome.io/>`_ is used for icons.

Designed to be usable right out of the box with minimal configuration, and
all the common features expected in a modern blog -- albeit with the
ubiquitous Bootstrap look and feel.  

However, customised CSS and other modifications can be easily
incorporated using config settings, without even having to modify
any templates.

But it's mostly intended as a "clean slate" for creating custom
Bootstrap-based themes, where all the usual scaffolding and fiddly bits are
already taken care of, and all that remains is to provide a custom design
on top of the Bootstrap base.


Installation
------------

Clone this repo, then in your ``pelicanconf.py`` set the ``THEME`` variable
to point to it::

  THEME = 'path/to/voidy-bootstrap/'

Out of the box what you get is the stock standard Bootstrap 3 look and
feel.  To customise things see below.


Example Settings
----------------

All of these are optional, but here is a basic example of common variables
that you might want to configure

The following should be set in ``pelicanconf.py``::

  SITESUBTITLE ='Sub-title that goes underneath site name in jumbotron.'
  SITETAG = "Text that's displayed in the title on the home page."

  # Extra stylesheets, for bootstrap overrides or additional styling.
  STYLESHEET_FILES = ("pygment.css", "voidybootstrap.css",)

  # Use the default sharing button implementation.
  CUSTOM_ARTICLE_SHARING = "sharing.html"
  CUSTOM_ARTICLE_SCRIPTS = "sharing_scripts.html"

  SOCIAL = (('Google+', 'http://plus.google.com/userid',
           'fa fa-google-plus-square fa-fw fa-lg'),
          ('Twitter', 'https://twitter.com/username', 
           'fa fa-twitter-square fa-fw fa-lg'),
          ('LinkedIn', 'http://linkedin-url', 
           'fa fa-linkedin-square fa-fw fa-lg'),
          ('BitBucket', 'http://bitbucket.org/username', 
           'fa fa-bitbucket-square fa-fw fa-lg'),
          ('GitHub', 'http://github.com/username',
           'fa fa-github-square fa-fw fa-lg'),
          )


The following are probably better suited for ``publishconf.py``::

  FEED_DOMAIN = SITEURL
  FEED_ALL_ATOM = 'feeds/all.atom.xml'

  DISQUS_SITENAME = "disqussitename"
  GOOGLE_ANALYTICS = "UA-xxxxxxxxxx"
  GOOGLE_ANALYTICS_SITEID = "gasiteid"
  TWITTER_USERNAME = "twitterusername"



Basic Configuration and Customisation
-------------------------------------

By default all required CSS and JavaScript files are downloaded from CDNs.
Intentionally little is supplied in the theme's ``static/css``.  Just a
``pygment.css`` file, and a sample css file (``voidybootstrap.css``) with
very minimal styling is provided as a starting point.

The simplest way to customise things is to override the standard Bootstrap
styles as necessary.  The theme intentionally avoids loading any additional
stylesheets by default, but this can easily be done by using the
``STYLESHEET_FILES`` setting.  ``STYLESHEET_FILES`` is an array for specifying
additional stylesheets that will be loaded by the ``base.html`` template
after the main Bootstrap CSS file.  Place any CSS stylesheet files you may
require in the ``static/css`` directory and add the filenames to the
``STYLESHEET_FILES`` setting in ``pelicanconf.py``

For example, if you've placed your own CSS styling in a stylesheet called
``custom.css`` (possibly using ``voidybootstrap.css`` as a starting point),
then you would need something like this in your ``pelicanconf.py``::

  STYLESHEET_FILES = ("pygment.css", "custom.css",)


Custom Bootstrap
----------------

As an alternative, or in addition, it's possible to easily replace the
standard Bootstrap file with a customised one.  The
``MAIN_LOCAL_STYLESHEET`` setting is provided for this.  If this variable
is *not* set, a standard ``bootstrap.min.css`` will be used from a CDN.  

To use a different (i.e. customised) Bootstrap stylesheet, set
``MAIN_LOCAL_STYLESHEET`` to the filename of a stylesheet to use instead.

This could be a customised Bootstrap stylesheet compiled manually from the
Bootstrap Less files, or perhaps one obtained from an online source.

For example, you could use the `Bootstrap customizer
<http://getbootstrap.com/customize/>`_ to create your own customised CSS
file.  Place that file in ``static/css`` and set ``MAIN_LOCAL_STYLESHEET``
to be the filename.  

Similarly, a `Bootswatch <http://bootswatch.com/>`_ theme can be easily
integrated.  Select a theme and download the files.  Place all the
necessary CSS files in ``static/css``.  Set ``MAIN_LOCAL_STYLESHEET`` to
the filename of the main Bootstrap CSS file, and specify any additional CSS
files in the ``STYLESHEETS`` array.


Further Customisation
---------------------

Like any other Pelican theme, you can just take the templates provided
and modify them to your liking.  However, if you're happy with the overall
layout and just want to add/subtract things here are there, this theme
provides a range of "hooks" to do just that by simply setting specific
variables in your ``pelicanconf.py`` and/or providing your own template
fragments.  For simple customisations, this can make is relatively
straightforward to isolate modifications and easily keep up to date with
any upstream changes.

There are 2 types of hooks.  

One is a set of optional templates.  At strategic points, the theme's
templates use Jinja's include directive with "ignore missing" to allow
arbitrary content to be optionally added.  For example, if you'd like to
add an "About" section to the top of the sidebar, just create a template in
the ``includes`` directory called ``sidebar_top.html`` and put the content
in there.  The contents of that template fragment will automatically be
included at the top of the sidebar.

See the "Optional Templates" section below for details.

The other hook is custom includes.  These are variables that can be set in
``pelicanconf.py`` to point to the filename of a template fragment.  These
template fragments will replace content in the default
templates.  For example, if ``pelicanconf.py`` contains the line::

  CUSTOM_SIDEBAR = "custom/sidebar.html"

Then the entire sidebar would be replaced by whatever is in the template
file located at::

  templates/includes/custom/sidebar.html

See the "Custom Includes" section below for details.

Note that for both optional templates and custom includes, all filenames
must be relative to the theme's ``templates/includes/`` directory.


Standard Settings
-----------------

VoidyBootstrap honors the following `standard Pelican settings
<http://docs.getpelican.com/en/3.5.0/settings.html>`_:

* ``SITEURL``
* ``SITENAME``
* ``SITESUBTITLE``
* ``LINKS``
* ``SOCIAL``
* ``TWITTER_USERNAME``
* ``FEED_DOMAIN``
* ``FEED_ALL_ATOM``
* ``FEED_ALL_RSS`` 
* ``DISQUS_SITENAME``
* ``GOOGLE_ANALYTICS``

For the most part they should work as expected, although some may behave
slightly differently than in the default Pelican theme (see next section).


Settings
--------

This theme supports the following configuration settings.  All are
optional.  


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

``STYLESHEET_URLS``
  An array of URLS for additional stylesheets that should be pulled in by
  the ``base.html`` template, e.g. for CSS files from a CDN.

``STYLESHEET_FILES``
  An array of filenames (relative to the ``/theme/css/`` directory) for
  additional stylesheets that should be pulled in by the ``base.html``
  template (after any STYLESHEET_URLS entries).

``SKIP_DEFAULT_CSS`` 
  No default CSS files at all will be used if this is set to True.  In this
  case the only stylesheets used will be those specified in
  ``STYLESHEET_FILES`` and ``STYLESHEET_URLS``.  This setting is provided
  to give more control over which specific Bootstrap (and Font Awesome) CSS
  files are used (i.e. it allows a specific version to be configured
  through settings).  But it means for things to work properly at a minimum
  the Bootstrap and Font Awesome need to be configured using the
  STYLESHEET_* settings.

``SKIP_DEFAULT_JS``
  Don't load any default JavaScript in the base template.  If this is set
  to True, at a minimum jQuery and the Bootstrap JavaScript must be
  provided via ``JAVASCRIPT_FILES`` and/or ``JAVASCRIPT_URLS``.

``JAVASCRIPT_FILES`` and ``JAVASCRIPT_URLS`` 
  Similar to the STYLESHEET_* settings, these allow arbitrary JavaScript
  files to be loaded.  They will be referenced at the bottom of
  ``base.html``, after any default script files.

``TWITTER_USERNAME``
  Set to a valid Twitter username to enable the twitter sharing button.

``TWITTER_CARD``
  If set to True, Twitter Card meta-data will be added to article pages.
  If this is enabled, ``TWITTER_USERNAME`` must also be set.

``OPEN_GRAPH``
  Set to True to enable Facebook Open Graph meta-properties.

``OPEN_GRAPH_FB_APP_ID``
  Facebook App ID.

``OPEN_GRAPH_ARTICLE_AUTHOR``
  Value for Open Graph ``article:author`` property, which will be set on
  article pages.

``OPEN_GRAPH_IMAGE``
  Default value for Open Graph ``og:image`` property.
  Articles can use the custom ``social_image`` metadata tag to specify a
  per-article page value.


Sidebar Settings
----------------

The "sidebar" area is probably something where everyone will want something
different, so it isn't possible to create an implementation that will
satisfy everyone all the time.  However, there are things that commonly
appear in sidebars (e.g author bio, categories, tag cloud, etc), so this
theme tries to make it simple to add those by providing a default sidebar
template which can be customised via settings in ``pelicanconf.py``.

However, it also provides the ability to completely replace the default
sidebar template with a custom implementation (see ``CUSTOM_SIDEBAR`` in
the "Custom Includes" section).

The following settings are available if using the default sidebar
implementation in ``includes/sidebar.html`` (or compatible variation
thereof):

``SOCIAL``
  Social media links to display in sidebar.  This option is handled a bit
  differently than in the default theme.  This should be a list/tuple where
  each element is a tuple with 3 elements: (name, URL, Font Awesome icon
  class).  (See the "Example Settings" section above for an example.)  The
  last element (icon class) can be omitted, in which case a generic icon
  will be used instead.

``LINKS``
  Optional list of arbitrary links to display in sidebar.  Each element
  must be a tuple with 2 elements: (link title, URL).

``SIDEBAR_HIDE_CATEGORIES`` 
  A list of category links is displayed in the sidebar by default.  Set
  this option to True to not display categories.

``SIDEBAR_HIDE_TAGS``
  A tag cloud is displayed in the sidebar by default.  Set this option to
  True to disable the tag cloud.

See also ``sidebar_bottom.html`` and ``sidebar_top.html`` in the "Optional
Templates" section below.


Custom Includes
---------------

The following variables (all optional), if specified, should be set to
paths for template fragments that will be included at strategic points from
the primary templates.  They will usually override existing sections of
content.  All paths must be relative to the theme's ``templates/includes``
directory.

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

Additional templates can be added to the ``templates/includes`` directory.
This provides a way to easily add small sections of content.

``article_top.html``
  Included by ``article.html`` before the article section.  Can be used 
  to provide things like pagination, breadcrumbs, ads, etc.

``article_end.html``
  Included by ``article.html`` right after the article contents.  There
  is a default implementation provided, which displays a tag-list.

``article_bottom.html``
  Included by ``article.html`` after the article content, after any 
  social media sharing buttons, but before disqus comments.  

``footer.html``
  Included by ``base.html``.  Anything here (e.g. copyright text) will
  appear between footer tags at the bottom of every page.

``index_meta.html``
  Included by ``index.html`` between the head tags.  Can be used 
  to add extra HTML meta tags to index pages, for example.

``sidebar_top.html``
  Included by ``sidebar.html`` at the top of the sidebar.  Provides a
  convenient place for an "about" blurb, for example.

``sidebar_bottom.html``
  Included by ``sidebar.html`` at the bottom of the sidebar.


Custom Metadata Tags
--------------------

This theme supports the following (optional) custom metadata tags.

``description``
  Can be used in pages and articles to provide a value for the HTML meta
  description tag, and social meta data (i.e. Open Graph).

``standfirst``
  Text for a summary/intro paragraph that will be placed at the start of an
  article.  This paragraph will be given a CSS class of "standfirst" so
  that additional styles can be applied.

``social_image``
  Set to an image filename (relative to ``{{ SITEURL }}/images/``) to 
  provide a value for an article's ``og:image`` meta property.

``image``
  Set to an image filename (relative to ``{{ SITEURL }}/images/``) to
  display a (responsive) "featured image" at the top of an article,
  underneath any standfirst.


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
