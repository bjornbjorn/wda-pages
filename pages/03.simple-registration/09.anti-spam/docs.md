---
title: Anit-Spam measures
taxonomy:
    category: docs
---

Anyone that's ever left an ExpressionEngine website with user registration open unattended for a while, knows that spam member signups can be a real hassle.

Most spambots attacking EE’s member registration will be used to EE’s built in registration form – and thus POST to /member/register. So, just by placing your registration form elsewhere **you’ve already done a great deal to minimize spam signups**. And by default, Simple Registration will block the /member/register endpoint, unless you changed that setting in the [config file](/simple-registration/configuration/config-file).

However, as we all know spammers are sneaky – so we have added some sneaky anti-spam functionality to Simple Registration; a **honeypot field** and **input name rewrites**.

## Honeypot Field

The Honeypot Field is a simple setting in the config file that tells Simple Registration the name of some input that should never be filled out. So, basically you can say that "username" is a honeypot field - so, if it is filled, Simple Registration won't create a new user.

```php
$config['simple_registration_global_honeypot_field'] = 'username';
```

A spambot will typically fill out any field called "username" (or "email") and thus be denied. In your form you can hide this field using CSS/JS to prevent regular users from filling it.

A honeypot field can be used alone, but typically it will be used in **conjunction with the input name rewrites** setting, *especially* if you actually call it "username" (since EE and Simple Registration expects that to be the username).

If you call it something not used by EE / Simple Registration though you can use it alone.

Note, that if you don't want to set this as a global setting in the config file, it's also available as a [parameter](/simple-registration/tags#expsimple_registrationform) in the {exp:simple_registration:form} tag:

```html
{exp:simple_registration:form honeypot="email"}
```

## Input name rewrites

This setting is basically an array of "rewrites" telling Simple Registration that, in the registration form, the value for "username" can be found in "any-new-field-name" etc. You can rewrite as many input names as you want.

Example;

```php
$config['simple_registration_input_name_rewrites'] = array(
    'username' => 'hexagon',
    'email' => 'hairy_creature',
);
```
The above settings will tell Simple Registration that **username** can be found in an input field called **hexagon** while **email** can be found in an input field called **hairy_creature**.

So, your HTML signup form could look something like this:

```html
{exp:simple_registration:form}
<div class="hidden">
Username: <input type="text" name="username"/>
Password: <input type="password" name="password"/>
E-mail: <input type="text" name="email"/>
</div>
Username: <input type="text" name="hexagon"/>
E-mail: <input type="text" name="hairy_creature"/>
<p><input type="submit" value="Register account"/></p>
{/exp:simple_registration:form}
```

The theory here is that **most spambots** won't fill out hexagon for username (because you made that up), but they will however fill the input field named **username** (because that is pretty standard).