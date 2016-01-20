---
title: Tags
taxonomy:
    category: docs
---

## Available tags

### {exp:simple_registration:form}

```html
{exp:simple_registration:form skip_success_message='y' return='member_section/welcome'}
E-mail: <input type="text" name="email"/>
{/exp:simple_registration:form}
```

### {exp:simple_registration:forgot_password}

```html
{exp:simple_registration:forgot_password}
    Your email: <input type="text" name="email"/><br/>
    <input type="submit" value="Send me password reset link"/>
{/exp:simple_registration:forgot_password}
```

>>> Note; the forgot password E-mail is sent out by EE, and it will link to the standard member templates, so they need to be present.
