# Forms and Rails Helpers

## Intro to Forms

Forms are 1 of 2 ways to submit an HTTP request to our website using HTML. (The other is with an anchor tag).

An example form:

```html
<form method="get" action="/search">
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

- authenticity token
- params hash
- strong params review

## You do:

add 1 to your previous group number.

submit the form to update db

## Break

## Intro to helpers

- path helpers
- form helpers
  - input
  - textarea
  - dropdown
  - radio
  - checkbox

## You do:

Add 1 to your previous group number

convert HTML to use helper. when the page loads, show the saved value

## Custom Rails helpers

### We do: build an ordinalize helper
