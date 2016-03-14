# Forms and Rails Helpers

## Learning Objectives

- Indentify 3 ways to make HTTP requests using HTML
- Use HTML form elements to get user input
- Read form values using JavaScript
- Use authenticity token to prevent CSRF attacks
- Use strong params to prevent mass assignment attack

## You do: Local Setup

https://github.com/ga-wdi-exercises/rails-forms

## Intro to Forms

Forms are 1 of 2 ways to submit an HTTP request to our website using HTML. (The other is with an anchor tag).

An example form:

```html
<form method="get" action="/">
<!--  ^               ^
      type of HTTP    where to send
      request         the request
 -->
  <label for="search">Search: </label>
<!--      ^id for corresponding form element -->

  <input type="text" name="q" id="search">
<!--     ^ type of   ^ how to     ^ links to
           input       identify     above for=""
                       this form    attribute
                       element
                       on server
-->
  <button type="submit">Search</button>
<!--      ^ buttons submit forms  -->

</form>
```

##  We do: Build a search form

## You do: Doc dive

Count off 1-6

1. option and select
1. textarea and input type="hidden"
1. input type="text" and type="number" and type="password"
1. input type="checkbox"
1. input type="radio"
1. input type="date"

Answer the following questions:

1. When would you use this?
1. Any related attributes?
1. How do you get the value using javascript
1. submit a pull request to solution branch

## You do: Teach Back

## I do: form POST

### Authenticity Token

```html
<form action="/forms" method="post">
  <input name="authenticity_token" value="<%= form_authenticity_token %>" type="hidden">
  <input name="name" type="text" placeholder="name">
  <input name="url" type="text" placeholder="url">
  <button type="submit">Submit</button>
</form>
```

The authenticity token prevents our applications from being vulnerable to [CSRF attacks](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF))

### params hash

```rb
# app/controllers/forms_controller.rb

def post
  Language.create(name: params[:name], url: params[:url])
  redirect_to :back
end
```

### Strong params review

`strong_params` prevents [mass assignment](https://en.wikipedia.org/wiki/Mass_assignment_vulnerability)

```rb
# app/controllers/forms_controller.rb

def post
  Language.create(name: params[:name], url: params[:url])
  redirect_to :back
end
```

## You do:

add 1 to your previous group number.

Submit the form to update db

## Break

## Intro to helpers

We've already seen rails helpers in a couple of ways:

- `link_to`
  - anchor tag
- `form_for`
  - form tag
- `image_tag`
  - image tag
- path helpers
  - `new_artist_path`
  - `edit_artist_path(@artist)`

Rails helpers allow us to take complexity out of the view and modularize our
HTML generation.

## We do:

Convert create form to use `form_for`

## You do:

Add 1 to your previous group number

convert HTML to use helper. when the page loads, show the saved value

## Custom Rails helpers

### We do: build an ordinalize helper

```rb
# app/helpers/ordinalize_helper.rb

module OrdinalizeHelper
  def ordinalize int
    if (11..13).include?(int % 100)
       "#{int}th"
     else
       case int % 10
       when 1; "#{int}st"
       when 2; "#{int}nd"
       when 3; "#{int}rd"
       else    "#{int}th"
       end
     end
  end
end
```

And a couple of helpers being used in garnet! https://github.com/ga-dc/garnet/blob/master/app/helpers/application_helper.rb
