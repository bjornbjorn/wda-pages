---
title: Signup Keys
taxonomy:
    category: docs
---

Signup Keys is a pretty versatile feature. Simply put; you can generate as many signup keys you’d like and link each to a member group. This enables you to assign specific member groups to users on signup.

>>> Signup keys are used by adding an element named "signup_key" to your form.

Some use-cases could be:

- Placing users in a specific group on signup (doh!)
- Beta invites
- Placing users in different member groups on signup based on their selection in a drop down list
- Handing out a secret code that enables users to become super admins on signup
- etc.

### Some usecases

You want to automatically assign all registered users to a "Beta user group":

Add a signup key for the "Beta user group" and add this code to your signup form:

```html
<input type="hidden" name="signup_key" value="GENERATED_SIGNUP_KEY_GOES_HERE"/>
```

You want the user to be able to select his group when registering:

Add a signup key for each user group you want the user to be able to select between. Then use these values in a select dropdown in your form, like so:

```html
<select name="signup_key"> 
<option value="GENERATED_SIGNUP_KEY_1">User group #1</option>
<option value="GENERATED_SIGNUP_KEY_2">User group #2</option>
</select>
```

You want to limit registrations to users who know the secret signup code.

Add a signup key for the "Members" group and add an input field in your signup form:

```html
Invite code: <input type="text" name="signup_key"/>
```

Then in EE's Members -> Preferences set "Default Member Group Assigned to New Members" to "Pending" for instance and generate one or more keys that you hand out to people you would like to invite.

### A note about the "Trigger" event
    
This option decides when the member group assignment should happen. As a general rule; if you have activation enabled you should use the trigger "Activation". This means that members will be assinged to the selected member group once they activate their membership. If you do not use activation, it should be set to "Signup". Note that Simple Registration will default to the value you should use when you add a new key.
    