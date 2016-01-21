---
title: Hooks
taxonomy:
    category: docs
---

>>>>>> Hooks can be used by other add on developers to hook onto Simple Registration.

The following hooks are available:

#### simple_registration_success($member_id, $data, $ref)

This hook is called after a member is successfully registered using Simple Registration.

Parameters:

- $member_id - the database id of the new member
- $data - an array with the members data
- $ref - reference to the Simple Registration object

```php
if (ee()->extensions->active_hook('simple_registration_success') === TRUE)
{
	ee()->extensions->call('simple_registration_success', $member_id, $data, $this);
	if (ee()->extensions->end_script === TRUE) return;
}
````

Return value: None

### simple_registration_email_password($email_info, $ref)

This hook is called just before sending an email to the user with the password (if this functionality is enabled). It can be used to modify the mail sent to the user.

Parameters:

- $email_info is an array containing the keys: email_subject, email_body and email (the email being sent to). This array must be returned from the hook.. Addons can hook onto this hook to modify the content of the email.
- $ref is a reference to the Simple Registration object.

```php
if (ee()->extensions->active_hook('simple_registration_email_password') === TRUE)
{
    $email_info = array('email_body' => $email_body, 'email_subject' => $email_subject, 'email' => $email);
    $email_info = ee()->extensions->call('simple_registration_email_password', $email_info, $this);
    if (ee()->extensions->end_script === TRUE) return;
    if($email_info && is_array($email_info)) {
        $email_body = $email_info['email_body'];
        $email_subject = $email_info['email_subject'];
        $email = $email_info['email'];
    }
}
```

Return value: Optional, but you can return a **modified $email_info array**.

### simple_registration_signyp_key_triggered($member_id, $signup_key, $trigger, $ref)

This hook is called when a signup key is triggered.

Parameters:

- $member_id - the database id of the member triggering the signup key
- $signup_key - the actual signup key used/triggered
- $trigger - string specifying when the signup key was triggered (either 'activation' or 'signup')
- $ref - reference to the simple registration object

Return value: None

```php
if (ee()->extensions->active_hook('simple_registration_signup_key_triggered') === TRUE)
{
    ee()->extensions->call('simple_registration_signup_key_triggered', $pending_event->member_id, $pending_event->signup_key, $trigger, $this);
    if (ee()->extensions->end_script === TRUE) return;
}
```

### simple_registration_honeypot_hit($registration_info, $ref)

Hook is called when a honeypot registration is encountered. It can be used to notify an anti-spam service for instance.

Parameters:

- $registration_info is an array containing the keys: ip_address, email, username, screen_name, url, honeypot, honeypot_key.
- $ref is a reference to the Simple Registration object

Return value: None