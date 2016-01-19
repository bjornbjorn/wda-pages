---
title: Hooks
taxonomy:
    category: docs
---

>>> Hooks can be used by other add on developers to hook onto SEO Lite. Actually, SEO Lite is a pretty awesome hook candidate for global things as it outputs its content in the header on every page.



### seo_lite_template

Allows one to modify the returned SEO Lite header template

Params sent in:
- Parsed tagdata (the template)
- Array: The SEO Lite / Entry variables collected ( [tag_prefix:title] etc.)
- The tag prefix used (needed to look up the var array reliably, but is often empty)
- Array: The SEO Lite tag parameters used (any kind of params can be added to SEO Lite, even ones SEO Lite don't recognize)
- A reference to the Seo_lite class (mod.seo_lite.php)

The returned html will replace the data returned by the {exp:seo_lite} tag.

Remember the last_call variable in case other add ons than yours use this hook: return $html.$this->EE->extensions->last_call;

```php
if ($this->EE->extensions->active_hook('seo_lite_template') === TRUE)
{
    $this->return_data = $this->EE->extensions->call('seo_lite_template', $this->return_data, $vars, $this->tag_prefix, $this->EE->TMPL->tagparams, $this);
    if ($this->EE->extensions->end_script === TRUE) return;
}
```

### seo_lite_fetch_data

Allows one to pull from another table

Params sent in:
- The table name

Return data

May be an array containing 'table_name' (new name of table to pull from)

```php
if ($this->EE->extensions->active_hook('seo_lite_fetch_data') === TRUE)
{
    $hook_result = $this->return_data = $this->EE->extensions->call('seo_lite_fetch_data', $where, $table_name);
    if($hook_result && isset($hook_result['table_name'])) {
        $table_name = $hook_result['table_name'];
    }
    if($hook_result && isset($hook_result['where'])) {
        $where = $hook_result['where'];
    }

    if ($this->EE->extensions->end_script === TRUE) return;
}
```

### seo_lite_tab_content

Allows one to modify the SEO Lite pulled up in the tab (ie. for translation addons)

Params sent in:
- $where - an array of where (activerecord) to check for .. already contains 'entry_id' and 'site_id'
- $table_name - the name of the table to pull data from (without db prefix, defaults to 'seolite_content')

Return value:
Please return nothing at all or an array which contains 'where' and/or 'table_name' to replace the existing
where array and table name to pull data from. This will be used to ->get(where, table_name) the data so
you can basically pull whatever from any table.

But remember the results must contain 'title', 'keywords', 'description' which SEO Lite rely on for the tab content.

```php
if ($this->EE->extensions->active_hook('seo_lite_tab_content') === TRUE)
{
    $hook_result = $this->return_data = $this->EE->extensions->call('seo_lite_tab_content', $where, $table_name);
    if($hook_result && isset($hook_result['where'])) {
        $where = $hook_result['where'];
    }
    if($hook_result && isset($hook_result['table_name'])) {
        $table_name = $hook_result['table_name'];
    }

    if ($this->EE->extensions->end_script === TRUE) return;
}
```

### seo_lite_tab_content_save

Allows one to modify the SEO Lite saved in the tab (ie. for translation addons)

Params sent in:
- $where - an array of where (activerecord) on UPDATE .. already contains 'entry_id' and 'site_id'
- $table_name - the name of the table to pull data from (without db prefix, defaults to 'seolite_content')
- $content - the current content saved (an array of site_id, entry_id, title, keywords, description)
 
Return value:
Please return nothing at all or an array which contains 'where' and/or 'table_name' and/or 'content' to
replace any of these.

But remember the content must contain 'site_id', 'entry_id', 'title', 'keywords', 'description'

```php
if ($this->EE->extensions->active_hook('seo_lite_tab_content_save') === TRUE) {

    $hook_result = $this->return_data = $this->EE->extensions->call('seo_lite_tab_content_save', $where, $table_name, $content);
    if($hook_result && isset($hook_result['where'])) {
        $where = $hook_result['where'];
    }
    if($hook_result && isset($hook_result['table_name'])) {
        $table_name = $hook_result['table_name'];
    }
    if($hook_result && isset($hook_result['content'])) {
        $content = $hook_result['content'];
    }

    if ($this->EE->extensions->end_script === TRUE) return;
}
```
