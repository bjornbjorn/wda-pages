---
title: Changelog
taxonomy:
    category: docs
---

>>> The dates in this changelog use international date format: YYYY-MM-DD (ISO8601)

#### 1.6.1 - 2017-01-31

* Bugfix: Password / Confirm Password could not be enabled / disabled in settings. Note; the settings were still used so upgrading from EE2 worked, but people could not _change_ the settings.

#### 1.6.0 - 2016-01-21

>>>> This release contains some **deprecated functionality**.

* Initial release for EE 3 (requires 3.1+)
* AJAX functionality has been deprecated (see docs for a simple [ajax signup form](/simple-registration/ajax-support). Unfortunately, there currently isn't a way to implement the previous functionality where a JSON array with error messages etc. were returned.
* Parameters: 'skip_success_message', 'exact_return_url' and 'return' have been deprecated for now (no way to implement them)
* Config setting 'simple_registration_hide_tabs_for_non_superadmins' has been deprecated
 
#### 1.5.1 - 2014-03-20

* Added support for hiding tabs from non-super-admins + specifying redirect link when clicking the email login link in settings

#### 1.4.6 - 2013-08-15

* Fixed forgot_password form - example implementation can be found in "example_templates/default_site/sr.group/forgot.html"

#### 1.4.5 - 2013-05-16

* Fixed issue where js was not loaded in the CP
* Fixed use of function that was deprecated in EE 2.6.1

#### 1.4.4 - 2013-03-05

Added parameter "on_registration_disabled" which can be used to specify the template to display if registration is disabled. This way the admin can easily disable / enable registration and have the website reflect this change.

Use like this:

{exp:simple_registration:form on_registration_disabled='frontpage/please_wait'} ... {/exp:simple_registration:form}


#### 1.4.3 - 2012-10-22

* Workaround for issue with CodeIgniter that would sometimes make the signup emails look garbled https://github.com/EllisLab/CodeIgniter/issues/1409

#### 1.4.2 - 2012-10-10

* Added support for "Require at least one valid signup key" (new checkbox found in "Signup Keys" tab)

#### 1.4.1 - 2012-09-05

* Fixes EE core security/possible spam issue where one can save core profile fields upon registration (not all fields but some like location/bio/url)
* Added support for EE core profile fields - use the new "allow_fields" param to allow these fields to be added to the form (ie. allow_fields="location|occupation|bday") would allow you to store "location", "occupation" and "bday_y", "bday_m" and "bday_d" using input fields in the form
* member_id of newly registered member is now returned in the JSON success response (this was a feature request)
* Fixed issue w/PHP short opening tag was used in config file
* Fixed localization issue with AJAX functionality where Simple Registration would use English 'error' key to check for errors - more info: http://bit.ly/Q5OvEC

#### 1.4 - 2012-02-22

* Fixed bug where styles would not be loaded in the backend if using /admin.php (or renamed version of admin.php)
* Added hooks (see docs for more info):
  - simple_registration_success
  - simple_registration_email_password
  - simple_registration_signyp_key_triggered
  - simple_registration_honeypot_hit
* Also some awesome new anti-spam measures, see config/simple_registration.php for these ;-)


#### 1.3.3 - 2011-10-08

* Added support for parameters action & exact_return_url

#### 1.3.2 - 2011-08-08

* Additional information passed on errors when using AJAX (there's now an array called "error_fields" which lists the erroneous fields with some information)

#### 1.3.1 - 2011-08-06

* Temp workaround for bug in EE 2.2.2 http://expressionengine.com/bug_tracker/bug/16315/

#### 1.3.0 - 2011-07-19

* Added AJAX Support (parameter: ajax='y' - responses will be returned in JSON format)

#### 1.2.4 - 2011-06-09

* Added support for parameter "skip_success_message" in addition to "return" which will enable you to skip the default EE success and send the user to the template of your choice after a successful signup:

	{exp:simple_registration:form skip_success_message='y' return='member_section/welcome'}
	    E-mail: <input type="text" name="email"/>
	{/exp:simple_registration:form}


#### 1.2.3 - 2011-04-06

* Added support for "Signup Keys"

#### 1.2.2 - 2011-03-28

* Added full support for MSM
* Settings saved in different format in the db

#### 1.1.0 - 2011-03-24

* Better support for custom fields 
* Honeypot support added
* Added parameters for id, name and class to {exp:simple_registration:form} and {exp:simple_registration:forgot_password} to override the default values

See blog post for more information about these changes: http://www.addonbakery.com/blog/?p=82

#### 1.0.0 - 2011-02-09

Initial release