ChangeLog - VoidyBootstrap
==========================

2.1 (January 2017)
-----------------------

* Added DEFAULT_SOCIAL_IMAGE, FAVICON and CUSTOM_HTML_HEAD settings.

* Sidebar changes:

  * Tag cloud not present by default (for Pelican 3.6+ compatibility).
  * Removed SIDEBAR_HIDE_TAGS and added CUSTOM_SIDEBAR_MIDDLES.
  * Added new (optional) tag cloud implementation based on the tag_cloud plugin (sb_tagcloud.html).
  * To use LINKS, now need to add "sb_links.html to CUSTOM_SIDEBAR_MIDDLES.

* Updated Dependencies: 

  * Bootstrap 3.3.7
  * Font Awesome 4.7.0
  * jQuery 1.12.4


2.0 (January 2015)
------------------

* Changed so much stuff (and added/removed/renamed lots of settings,
  breaking backward compatibility somewhat -- sorry!), that decided this
  should constitute version 2.0.

* Updated Dependencies: 

  * Pelican 3.5 (should work with 3.3 and 3.4, but untested)
  * Bootstrap 3.3.1
  * Font Awesome 4.2.0
  * JQuery 1.11.1

* Sidebar changes:

  * Sidebar is now optional (and defaults to single column, which I'm not
    overly happy about, but it makes the implementation simpler/neater).
  * Support for LINKS setting added.
  * SOCIAL setting changed a bit.
  * New settings to disable category links and tag cloud.

* Renamed MAIN_LOCAL_STYLESHEET to BOOTSTRAP_STYLESHEET. 

* Footer taken out of main column container, so now spans entire width of
  page.

  * If you're using a custom footer template, you'll probably want to put
    any content inside a container div.

* More flexible CSS and script handling.

  * New settings: STYLESHEET_URLS, JAVASCRIPT_URLS, JAVASCRIPT_FILES.
  * STYLESHEET_FILES setting replaces STYLESHEETS.
  * Ability to disable loading any default CSS or scripts from CDNs via
    new SKIP_DEFAULT_CSS and SKIP_DEFAULT_JS settings.
  * The above means it's now possible to configure a site to load all CSS
    and JS files from static (sub)directory, without using CDN files at
    all.
  * Added javascript metatag for pages.

* Replaced all optional templates with custom includes:

  * Removed most CUSTOM_ARTICLE_*.
  * Added CUSTOM_ARTICLE_HEADERS, CUSTOM_INDEX_ARTICLE_HEADERS,
    CUSTOM_ARTICLE_PRECONTENT, CUSTOM_ARTICLE_FOOTERS.
  * Added CUSTOM_INDEX_META, CUSTOM_SIDEBAR_TOP, CUSTOM_SIDEBAR_BOTTOM

* New custom includes: CUSTOM_PAGE_FOOTERS, CUSTOM_FOOTER,
  CUSTOM_SCRIPTS_ARTICLE, CUSTOM_SCRIPTS_PAGE, CUSTOM_SCRIPTS_BASE,
  CUSTOM_ARTICLE_PREFIX

* New header outside of the main container, customisable  via CUSTOM_HEADER_*

* More comprehensive, fine grained ability to add content, using:

  * CUSTOM_CONTAINER_TOP_*
  * CUSTOM_CONTENT_TOP_*
  * CUSTOM_CONTENT_BOTTOM_*
  * CUSTOM_CONTAINER_BOTTOM_*
  * Because of this, the "home-top" button cluster moved to a separate
    template, and is not used by default.  End users of the theme now have
    the flexibility using the various new CUSTOM_* options to (optionally)
    add the default home-top buttons (or custom implementation) where they
    see fit.

* Fixes for unexpected Typogrify side-effects, and possible problems 
  caused by quote characters in article headings: title and description 
  fields are now stripped of tags and escaped.


1.0 Initial Release (February 2014)
-----------------------------------

* Dependencies: 

  * Bootstrap 3.0.3
  * Font Awesome 4.0.3
  * JQuery 1.9.1

* Includes Open Graph and Twitter Summary Card meta data.

* Some initial microdata support.

* Archives grouped by year, reverse chronological.

* Featured images, social images, standfirst, meta descriptions.

