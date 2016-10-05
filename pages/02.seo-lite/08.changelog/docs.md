---
title: Changelog
taxonomy:
    category: docs
---

>>> The dates in this changelog use international date format: YYYY-MM-DD (ISO8601)

#### 1.5.4 - 2016-10-05

* PHP 5.3 compatibility fix

#### 1.5.3 - 2016-05-10

* Added [PHP 7 compatibility](https://github.com/bjornbjorn/SEO-Lite/issues/27).

#### 1.5.2 - 2016-03-03

* Fixed [bug](https://github.com/bjornbjorn/SEO-Lite/issues/26) where content would not be deleted from exp_seolite_content when deleting an entry

#### 1.5.1 - 2016-01-14

* EE3 release, requires 3.1.0. Note that extra tags support for PhotoFrame and Assets have been removed (these field types are currently not available for EE3).

#### 1.4.9.2 - 2014-10-07

* Added support for "photo_frame" in extra fields - more info here: https://gist.github.com/bjornbjorn/4039233#comment-1313462

#### 1.4.9.1 - 2014-08-12

* Bugfix: {extra:desc} is now wrapped in htmlentities()

#### 1.4.9 - 2014-07-14

* Adding global option to strip out pagination string from canonical URLs.

#### 1.4.8 - 2014-05-07

* Support for "max_length" in extra text field + fix for extra fields for EE 2.8.1+

#### 1.4.7 - 2014-03-19

* Added hooks: seo_lite_tab_content_save, seo_lite_tab_content and seo_lite_fetch_data


#### 1.4.6.1 - 2013-11-06

* Added tag parameters array to the seo_lite_template hook

     		
#### 1.4.6 - 2013-11-06

* Added hook: "seo_lite_template" which will enable developers to modify the SEO Lite template before it is returned.
  This could be used similar to the CP's add_to_head hooks, if you'd like to add something to the headers globally from
  one of your addons.
  
#### 1.4.5.1 - 2013-10-29

* Fixes issue with old/new versions of the SEO Lite Assets extra field.


#### 1.4.4 - 2013-05-16

* Fixed use of function that was deprecated in EE 2.6.1

#### 1.4.3 - 2013-04-19

* Replace &nsbp; and   in all tag parameters with normal whitespace (since EE will remove space at the beginning of a parameter people are using   or   - we replace these with a standard space)

#### 1.4.2 - 2013-02-19

* Bugfix for using SEO Lite as a tag pair inside an exp:channel:entries loop - use {exp:seo_lite:pair} now - ie. {exp:seo_lite:pair entry_id="{entry_id]"} Meta: {meta_description}{/exp:seo_lite:pair}
* Added support for hiding the keywords field (use $config['seolite_show_keywords_field'] = 'n'; in config/seolite.php. This can also be overridden in a master config if you use that)
* Support for Publisher
* Bugfix: if the client used soft-hypen tag in the title (­) it would display in the browser title as the tag
* Made {entry_title} available as a tag (no title prefix/postfix etc.)
* Fixed so that   won't be included in the title (if it is used in default_postfix)
* Bugfix: there was a regression bug where using the "category_url_title" parameter would not work

#### 1.3.6 - 2012-09-18

* Fixed bug where pagination segment would be duplicated in the "canonical_url" tag on pagination pages (ie. /P4). This seems to have been introduced recently (2.5.x+?)

#### 1.3.5 - 2012-02-23

* Increased the size of the "default_keywords" and "default_description" fields to 1024 in the database

#### 1.3.4 - 2011-12-19

* Added support for config override of publish tab title (e.g. $config['seo_lite_tab_title'] = 'SEO';)

#### 1.3.3 - 2011-10-14

* Fixed bug where {canonical_url} would be blank on standard channel entries

#### 1.3.2 - 2011-09-27

* Changed constructor name

#### 1.3.1 - 2011-09-02

* Fix for canonical URLs on pages / structure pages


#### 1.3 - 2011-08-30

* Added support for category_url_title for fetching titles/descriptions of categories (for use as seo metadata)
* Added support for using seo_lite as a tag pair (if done the template won't be used, good for overriding etc.)
* Fixed minor bug in backend where the instructions would not hide after clicking view/hide

#### 1.2.5 - 2011-03-18

* French language file added
* Renamed language key "welcome" to "seo_lite_welcome" as this sometimes confliced with other modules who used the same language key

#### 1.2.4 - 2011-02-23

This update includes database changes and requires that you visit the module in the backend (EE will then automatically run the update script).)

* htmlspecialchars() all metadata before output (there were problems with the use of quotes etc. in default description)
* Increased size of the default keywords / descripton to 1024 chars
* Changed coltype of default_title_postfix to VARCHAR(60) instead of CHAR(60) (char would strip trailing space, thus the need for   .. that's no longer needed)


#### 1.2.3 - 2011-02-21

* Added support for {canonical_url} for use in the SEOLite template like this:	
* Added 'ignore_last_segments' parameter which tells SEO Lite to ignore the X last url segments (ie. 2 would be logical for URL: entries/some_entry_here/sort/asc)
* Improved support for pages - the "Pages URI" will now override "URL Title"
* Minor change in how the "title_postfix" parameter works - the default postfix (specified in admin) will now always be added after this

Docs have been updated with the new tags.