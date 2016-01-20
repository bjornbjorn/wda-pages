---
title: Config File Settings
taxonomy:
    category: docs
---

## Settings

In the `config/simple-registration.php` file you can find these settings:

### simple_registration_no_other_registrations

Default: TRUE

```php
/**
 * If enabled registrations using /member/register will not be allowed. It's wise to keep this TRUE since if you
 * don't spammers will use /member/register to create accounts on your website
 */
$config['simple_registration_no_other_registrations'] = TRUE;
```

### simple_registration_global_honeypot_field

Default: FALSE

```php
/**
 * Specify a global honeypot field here. Use this to specify that "username" is always a honeypot and if it is
 * filled out register it as spam and deny the registration
 */
$config['simple_registration_global_honeypot_field'] = FALSE; //'username';
```

More information about the [honeypot field here](/simple-registration/anti-spam#honeypot-field).

### simple_registration_input_name_rewrites

Default: array()


```php
/**
 * Use this array to rewrite input. For example if you specify that 'username' is a global honeypot above
 * you can use this array to say that the real username value can be found in the input field named 'hexagon'
 * for example.
 *
 * Like this:
 *
 * $config['simple_registration_input_name_rewrites'] = array(
 *    'username' => 'hexagon',
 * );
 *
 * Simple Registration will then use 'hexagon' for username. You can use this array to rewrite all fields,
 * ie. you can say that password shall be found in 'hairy_animal' and password_confirm shall be found in
 * 'hairy_animal_confirm'. This enables you to create a 100% custom signup form quickly for each website
 * that spammer bots will have a hard time auto-registering at.
 *
 */
$config['simple_registration_input_name_rewrites'] = array(
   // 'username' => 'hexagon',
);
```

More information about [input name rewrites here](/simple-registration/anti-spam#input-name-rewrites).
