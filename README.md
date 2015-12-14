# Angular Introduction

## Objectives

1. Getting to know what Angular brings to the table
2. Understand the MVVM pattern and how it differs from traditional MVC pattern

## Introduction

We're all used to writing frontend Javascript bits to satisfy our needs, but
what happens when it starts to become a bit unmanageable? Luckily, we have 
frontend frameworks such as Angular to manage the meyhem. 

Angular was first introduced in 2009 as a side project at Google. It was 
one of the first frameworks to lead Model-View-ViewModel pattern or MVVM 
into the frontend programming world. Today it is known as the framework
to use to bootstrap an application quickly and is used by many companies
as their framework of choice.

## What is MVVM?

If you're familiar with the traditional Model-View-Controller (MVC),
MVVM shares the same ideology of models and views. 

*Models* define the structure of data. An example model would be a _person_
where a person has a first name and a last name.

*Views* are user interfaces or in our case, HTML and CSS.

In order for our views to display models and create them, we would
use a *controller* to fuse the two together in a MVC pattern. A jQuery
example of a controller would look something like:

```
// bind the view to the model
$('#new-person-form').on('submit', function(){})

// bind the model to the view
var people = [{...},{...}]
var html = ''
for (var i = 0; i < people.length; i++) {
  var person = people[i]
  html.append('<div class="person">...</div>')
}
$('#people').html(html)
```

The *ViewModel* simplifies the controller by abstracting data binding
back to the view. In our case, our HTML now defines how the model binds
to the view and how the view binds to models. This is also known as 
_two-way data binding_. 

```
<form ng-submit="doSubmit()"></form>
<div id="#people">
  <div class="person" ng-repeat="person in people"></div>
</div>
```

Angular brings binding back to the HTML just as it binded CSS styles
to elements. This way your bindings stay in one place instead of in
both your HTML and your Javascript files. 
