# Joshua Mun's Blog App

## Overview
Rails provides a faster way to produce code common to many html pages such as buttons, hyperlinks, and even forms.

You embed these magic pieces of ruby into the html view document directly.

Demonstration goals:
  - familiarity with syntax
  - knowledge of where to execute
  - understanding of method specification
  - understanding of conditional logic
  - introduction to all form helpers

## Link_to 
Quick way to build hyper links. 

```
<%= link_to 'TEXT', url_helper_path %>
```
  - blog homepage, Delete and Edit

## method: :delete
In both Link_to and Button_to, you can specify which method you want this link or button to execute. i.e. put, patch, delete

![Methods](app/assets/images/rails_routes.png?raw=true "Rails Routes")

In the post_path, how do you specify which route you want to take? By specifying the method.

```
method: :delete

<%= link_to 'Delete', post_path(post), method: :delete %>

method: :put
method: :patch
```

## if & unless
Have you ever wished that you could put all of your conditional logic inside the html code itself??

__Link_to_if && Link_to_unless__

The if and unless are converse to one another.

```
<%= link_to_if(@user.nil?, "Login", { controller: "sessions", action: "new" }) %>
```
```
<%= link_to_unless(@user, "Login", { controller: "sessions", action: "new" }) %>
```

## form_for
Quick and dirty way to build a form!

```
<%= form_for @post do |f| %>
    <%= f.text_field :title %>
    <%= f.text_area :body %>
    <%= f.submit "Update" %>
    <% end %>
```
__is equivalent to__
```
<form class="edit_post" id="edit_post_1" action="/posts/1" accept-charset="UTF-8" method="post">
  <input name="utf8" type="hidden" value="✓">
  <input type="hidden" name="_method" value="patch"><input type="hidden" name="authenticity_token" value="u2ab1Z0TaiHSgJGhY04NTYJaSbVX5RkgQHLOwAehoEmxKFZsdHAZtrjUrspeLYv6H5i23mEDToMou7KkGMsM1w==">
    <input type="text" value="TEXT GOES HERE" name="post[title]" id="post_title">
    <textarea name="post[body]" id="post_body">MORE TEXT HERE</textarea>
    <input type="submit" name="commit" value="Update" data-disable-with="Update">
</form>
```

## button_to
Quick and dirty way to make buttons!

*__Caveat__*
buton_to by default execute POST methods. So must specify if using otherwise, such as get.

```
  <%= button_to "JoshBlog", root_path, method: :get %>
```
__is equivalent to__
```
<form class="button_to" method="get" action="/">
  <input type="submit" value="JoshBlog">
</form>
```

## form helpers

### Additional resources:
```
http://guides.rubyonrails.org/form_helpers.html
```

![Form Helpers](app/assets/images/form_helpers.png?raw=true "Form Helpers")