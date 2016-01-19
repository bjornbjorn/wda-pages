---
title: Template Tag
taxonomy:
    category: docs
---

There’s just one tag – **{exp:seo_lite}** – and it will fetch the template you edit in the backend and populate it with the entry specific data (title/keywords/description).

The tag can be placed anywhere. It makes sense to put it in a global [Layout](https://docs.expressionengine.com/latest/templates/layouts.html), [Embed](https://docs.expressionengine.com/latest/templates/embedding.html) or [Snippet](https://docs.expressionengine.com/latest/templates/globals/snippets.html). Basically where you have the HTML header that you include everywhere.

>>>>>> In _most cases_ it will make sense to use the **last segment** as an identifier to fetch the SEO Lite data. What this means is that given the URL http://example.com/blog/what-i-discovered-in-vegas, the last segment (in this case "what-i-discovered-in-vegas") will be used to look up the correct entry (and find its SEO data). So, SEO Lite will search the datbase for an entry with **url_title** "what-i-discovered-in-vegas".

### {exp:seo_lite}

This tag will output the SEO Lite template with entry-specific SEO data.

You can fetch by segment or entry_id:

`{exp:seo_lite use_last_segment="yes"}` - use last segment as identifier; makes sense in most cases

`{exp:seo_lite url_title="{segment_3}"}`- use specific segment (in this case segment_3)

`{exp:seo_lite entry_id="{entry_id}"}` - use entry_id, ie. inside an {exp:channel:entries} tag

`{exp:seo_lite default_title=“About us”}` - static mode; this will output “About Us” for the title tag but still use the default keywords/description for the site.

`{exp:seo_lite default_title=“About us” default_keywords=“new, keywords” default_description=“This description is unique for this page”}` - static mode with everything overridden; use this in a static template for example with no channel entry associated with it. It will output the SEO template with the data provided in the tag.

`{exp:seo_lite title_override=“This is the only thing i Want inside the HTML title-tags”}` - title override; will ignore whatever specified in the SEO Lite template.


### Parameters

* **entry_id**: The id of the entry you wish to get metadata about
* **url_title**: The url title of the entry you wish to get metadata about (perfect for segments);
* **use_last_segment**: y/n – use this if you want to fetch metadata based on the last segment (Note; this will work w/pagination as well)
* **category_url_title**: optional, use if you wish to fetch a category (title will be category title, description will be category description -- or defaults)
* **site_id**: optional, if you are getting content from another site then the current use this
* **default_title**: Override the default title in the template
* **default_keywords**: Override the default keywords in the template
* **default_description**: Override the default description in the template
* **title_prefix**: A string to prefix the title with
* **title_postfix**: A string to postfix the title with
* **title_override**: Title hard override – ignore whatever is set in the database and use this title instead
* **ignore_last_segments**: (optional) - specify the number of segments to ignore at the end - e.g. 2 (ie. if you have an url that includes /sort/asc at the end you don't want to include those in the canonical url + when searching for the url entry in conjuction with the "use_last_segment" parameter)
* **friendly_segments**: y/n (default is n) if {segment_x} is used in the SEO Lite template make it friendly (ie. ‘this_is_some_url_title_segment’ will be ‘This is some url title segment’)
* **tag_prefix**: if you want to prefix the SEO Lite tags, use this (ie. the {meta_description} will be {seo-meta_description} if you add a tag_prefix="seo-"