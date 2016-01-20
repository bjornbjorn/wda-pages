---
title: Custom Member Fields
taxonomy:
    category: docs
---

Using ExpressionEngine's Custom Member Fields with Simple Registration is .. you guessed it; simple.

>>> First of all, please note that for custom fields you need to check the **"Show in registration?"** to be able to use the field with Simple Registration. This is a security measure by EE so that people cannot save data to custom fields which you have not explicitly specified should be visible for them upon registration. This setting is respected by Simple Registration.

First you need to create a new member field in ExpressionEngine - more about that <a href="https://docs.expressionengine.com/latest/cp/members/fields/index.html" target="_blank">here</a>.
 
Once you have your custom field, you need to add the field to the form (ie. modify the html).

Normally EE will use the field database column name in the form code, so – for instance – if you were to add a custom field called referral_source you’d have code that looked something like this:

```html
Where did you hear about us? <input name="m_field_id_23" type="text" />
```

You can use that code if you want. However, with Simple Registration you can simply use the name you gave the field in your form code instead:

```html
Where did you hear about us? <input name="referral_source" type="text" />
```

It makes more sense that way – it’s easier to remember and implement.

>>>>>> If you want you can still use the standard EE code for the registration form. So you could e.g. copy the code for the custom fields that is generated in /member/register/ and paste it into your simple registration code. If you have a lot of custom fields **this is the easiest way**.