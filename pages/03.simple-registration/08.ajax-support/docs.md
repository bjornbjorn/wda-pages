---
title: AJAX Support
taxonomy:
    category: docs
---

## Signup

This is an example of an ExpressionEngine member signup AJAX example:

HTML

```html
<div class="row">

    <div class="small-12 columns">
        <h1>Register member (AJAX)</h1>
    </div>

    <div class="small-12 columns">

        <div class="error" style="display:none; color: red;">
            <h2 class="error-title"></h2>
            <ul class="error-list"></ul>
        </div>

        <div class="success" style="display:none">
            <h1>Thanks for registering</h1>
            <p>We've sent you an email</p>
        </div>

        {exp:simple_registration:form id="register_member_form"}
        E-mail: <input type="text" name="email"/>
       <p>
           <a href="#" class="ajax-register-link">Register</a>
       </p>
        {/exp:simple_registration:form}
    </div>

</div>
```

jQuery:

```javascript

    $('body').on('click', '.ajax-register-link', function(e) {
        e.preventDefault();

        $('.error').hide();

        $.post(
            $('#register_member_form').attr("ACTION"),  $('#register_member_form').serialize(), function(response) {
                var response_el = $(response);

                // ERROR
                if (response.indexOf('<title>Error</title>') !== -1) {

                    var error_h1 = response_el.find('h1').html();
                    var error_li = response_el.find('ul').html();

                    $('.error-title').html(error_h1);
                    $('.error-list').html(error_li);
                    $('.error').slideDown();

                } else {
                    // SUCCESS

                    $('#register_member_form').hide();
                    $('.success').show();
                }


            }, "html"
        )

    }); 
```