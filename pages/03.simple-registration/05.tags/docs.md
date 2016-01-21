---
title: Form Tags
taxonomy:
    category: docs
---

## {exp:simple_registration:form}

This is the main form tag for Simple Registration. It will create a signup form. You can generate an example form code in [the settings](/simple-registration/configuration/form-html-code).

Example:

```html
{exp:simple_registration:form class="signup-form"}
E-mail: <input type="text" name="email"/>
{/exp:simple_registration:form}
```

### Parameters

All parameters are optional.

| Parameter          | Description |
| ----------------- | ----------- |
| id       | the id of the form |
| name     | the name of the form |
| class    | the class attribute of the form |
| allow_fields | pipe-seperated list of EE standard member fields to allow in registration form - [more info here](/simple-registration/standard-member-fields). |
| honeypot | the name of a [honeypot field](/simple-registration/anti-spam#honeypot-field) |
| action   | use this if you want to override the form's default action post url (by default this is /index.php or /) |


## {exp:simple_registration:forgot_password}

This tag creates a "Forgot password?" form you can put anywhere. 

Example:

```html
{exp:simple_registration:forgot_password}
    Your email: <input type="text" name="email"/><br/>
    <input type="submit" value="Send me password reset link"/>
{/exp:simple_registration:forgot_password}
```

>>> Note; the forgot password E-mail is sent out by EE, and it will link to the standard member templates, so they need to be present.
