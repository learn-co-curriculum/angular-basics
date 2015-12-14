# Angular Introduction

## Objectives

1. Getting to know what Angular brings to the table
2. Understand the MVVM pattern and how it differs from traditional MVC patterns

## Introduction

If you've used Javascript or jQuery for your frontend needs, you're probably
no stranger to code that is hard to follow and code that's just all over the
place. Luckily frontend frameworks such as Angular can help alleviate this pain.

A lot of these frontend frameworks introduce *single page applications*, including
Angular. In a single page app, your app is loaded completely into the browser by a
single view from your server. From here on, your app takes over the UI portion and
only data (like JSON and XML) should be passed between your server and your app.

With this in mind, single page applications can become complex. This is where
we'd start using programming patterns such as the Model-View-Controller or MVC
pattern to help organize our code. But MVC can be way too verbose when binding
views and models together through scripts.

Angular aims to solve this by introducing a different pattern called
*Model-View-ViewModel* or MVVM.

## Introducing Angular

Angular was first introduced in 2009 as a side project at Google. It was 
one of the first frameworks to lead Model-View-ViewModel pattern or MVVM 
into the frontend programming world. Today it is known as the framework
to use to bootstrap an application quickly and is used by many companies
as their framework of choice.

## Traditional Frontend MVC

If you're familiar with the traditional Model-View-Controller (MVC),
MVVM shares the same ideology of models and views where:

* *models* define the structure of data. An example model would be a _person_
where a person has a first name and a last name
* *views* are user interfaces or in our case, HTML and CSS

In a MVC pattern, a controller written in Javascript defines what a
form does on submission. In technical terms, we call this _binding_.

```
// bind the view to the model
$('#new-person-form').on('submit', function(){})
```

This is great! This is exactly what we want a controller to
do. It defines actions and doesn't mix itself up with our view.

But lets say we we want to display a table with an unknown 
number of people, we'd have to use Javascript to dynamically
create HTML elements.

```
<table>
  <thead>
    <th>Name</th>
    <th>Email</th>
  </thead>
  <tbody id="people">
  </tbody>
</table>

<script>
  // for this example, we have a set amount
  // of people, but lets assume its dynamic
  var people = [{
    name:'Steven', 
    email:'steven@example.com'
  }]
  
  // start creating HTML code for each 
  // person that we have
  var html = ''
  for (var i = 0; i < people.length; i++) {
    var person = people[i]
    html += '<tr class="person">'
    html += '<td>' + person.name + '</td>'
    html += '<td>' + person.email + '</td>'
    html += '</tr>'
  }
  
  // then write it directly to the page
  $('#people').html(html)
</script>
```

It starts getting messy and we're starting to write HTML inside
our Javascript files. There are now UI elements in your controller
which is counter-intuitive to your MVC pattern. What happens when 
you need to add a CSS class? You would have edit elements through 
both your HTML templates and Javascript controllers. This is where 
controllers start to become confusing and unlogical.

## The ViewModel in MVVM

The *ViewModel* aims to solve problems that MVC introduces by moving
binding away from the Javascript and back into HTML. A rewrite of
the above example in Angular would look like:

```
<form ng-submit="doSubmit()"></form>
<div id="#people">
  <div class="person" ng-repeat="person in people"></div>
</div>
```

You can see that there is no Javascript involved and our HTML logic
goes right back to the view. The code is much cleaner and a lot
easier to write.
