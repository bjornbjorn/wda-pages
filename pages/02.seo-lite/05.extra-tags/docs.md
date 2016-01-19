---
title: Extra Tags
taxonomy:
    category: docs
---

Extra Tags can be used to pull additional data from the custom fields in your channel entries. This data can then be used in the [SEO Lite Template](/seo-lite/configuration#template).

>>>> This is for advanced users only. If you enter a wrong database ID somewhere in the extra fields config array, it will just not work, and you may get errors.

Here's an example of a extra fields config array. This config goes in your [config file](/seo-lite/configuration#config-file-settings):

```php
/**
 *
 * Pull additional info for SEO Lite
 *
 * channel_id => array(field_id => tag_name)
 **/
$config['seolite_extra'] = array(
    '1' => array(                               // news
        'desc' => array(
            'field_id' => 3,
            'field_type' => 'text',
        ),
        'image' => array(
            'field_id' => 45,
            'field_type' => 'file',
        )
    ),
    '4' => array(                               //  blog
        'desc' => array(
            'field_id' => 18,
            'field_type' => 'text',
        ),
        'image' => array(
            'field_id' => 46,
            'field_type' => 'file',
        )
    ),
    '5' => array(                               // portfolio
        'desc' => array(
            'field_id' => 29,
            'field_type' => 'text',
        ),
        'image' => array(
            'field_id' => 43,
            'field_type' => 'file',
    )
);
```

Basically, we have three channels (news, blog, and portfolio). The index in the array is the **channel_id**. So, news has channel_id 1, blog has channel_id 4 and portfolio has 5. You can find these IDs in the database.

Then, for each channel, we specify the same extra fields; in this case **desc** and **image**. These config arrays contain the field_id and the field_type of the extra field.

```php
'desc' => array(
            'field_id' => 29,
            'field_type' => 'text',
)
```

The config array above will pull the contents from field_id 29 and expect it to be text.

There are currently support for two fieldtypes: **text** and **file** (native EE File). The text will just output the plain text, while file will output the full url to the file.

In the [SEO Lite template](/seo-lite/configuration#template) you can use the extra tags like this (more [examples here](/seo-lite/configuration#template)):

```html
<meta property="og:description" content="{extra:desc}"/>
<meta property="og:image" content="{extra:image}"/>
```

You can call the extra tags whatever you'd like, they'll be prefixed with "extra:".