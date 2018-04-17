---
layout: post
title:      "Accepts_Nested_Attributes_For"
date:       2018-04-17 03:48:29 -0400
permalink:  accepts_nested_attributes_for
---


So far one of the more difficult topics I have encountered in Rails is nested forms and how it produces HTML and interacts with objects. A first glance it seems simple, it's like a nested array...sort of...right? Well sort of...also not sort of. First off when white-listing attributes and nested attribute it comes out a hash. Second off, when you add the nested attributes (ie categories_attributes in the following code) it gets confusing. There are very specific naming conventions that must be followed.


/app/controllers/posts_controller.rb
```
  def post_params
    params.require(:post).permit(:name, category_ids:[], categories_attributes: [:name, :some_attribute])
  end

```


At first glance just whitelisting the params should work since rails is full of magic. However, in addition, you need to do is add a line in the MODEL that adds methods. Just like `has_many:` adds methods so does `accepts_nested_attributes_for:`

/app/models/post.rb

```
class Post < ActiveRecord::Base
  has_many :categories
  accepts_nested_attributes_for :categories
end
```



Here is an example with a `belongs_to:` relationship notice it's singular and not plural.

/app/models/comment.rb

```
class Comment < ActiveRecord::Base
  belongs_to :user
  accepts_nested_attributes_for :user
end
```


/app/controllers/comments_controller.rb

```
  def comment_params
    params.require(:comment).permit(:content,, :user_id, user_attributes:[:username])
  end
```

	
However, everything else  a bit less intuitive.

When `accepts_nested_attributes_for` is added it creates a method which is named in this situation
**categories_attributes** or **user_attributes**. It is named after whatever model you happen to be using.

Now that we have gone over how to setup this association we can talk about the method.

```
def categories__attributes=(category_attributes)

   code and probably more code
	 
end
```


Seems simple. However, it doesn't do what it looks like it does. It intercepts from a nested form an appropriately placed :category and runs the data through categories_attributes=. In fact, if you placed :category_attributes in place of :category it wouldn't work. 
`categories_attributes=` intercepts the expected setter method in a nested form. So you just have to remember that when using a nested form that 


```  
<%= f.fields_for :categories do |category| %>
    <%= category.label :name %>
    <%= category.text_field :name %>
<% end %>
```


will produce `[post][categories_attributes][0][name]`  


``` 
<%= f.fields_for :categories_attributes do |category| %>
    <%= category.label :name %>
    <%= category.text_field :name %>
<% end %>
```


will produce `[post][categories_attributes][name]`

	
