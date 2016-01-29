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

```javascript
// bind the view to the model
$('#new-person-form').on('submit', function(){})
```

This is great! This is exactly what we want a controller to
do. It defines actions and doesn't mix itself up with our view.

But lets say we we want to display a table with an unknown 
number of people, we'd have to use Javascript to dynamically
create HTML elements.

```html
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

## The MVVM Pattern

The Model-View-ViewModel or MVVM patterm aims to solve problems 
that MVC introduces by moving template logic away from the Javascript 
and back into HTML. A rewrite of the above example in Angular would 
look like:

```html
<form ng-submit="doSubmit()"></form>
<table>
  <thead>
    <th>Name</th>
    <th>Email</th>
  </thead>
  <tbody id="people">
    <tr ng-repeat="person in people">
      <td>{{ person.name }}</td>
      <td>{{ person.email }}</td>
    </tr>
  </tbody>
</table>
```

You don't necessarily need to know what this code means just yet, but you can 
see that there is no Javascript involved and our HTML goes right back to 
the view. The code becomes much cleaner and a lot easier to write.

### What is the ViewModel?

The ViewModel controls and maintains states of your view and data. It serves
as a mediator for communication between your view and your controllers. This
can be a handful at first, but lets imagine it like this:

We have the **big boss** and his **secretary**

1. The big boss tells the secretary to let him know about any incoming calls
2. The secretary picks up a call and records the purpose of the call on a sticky note
3. The secretary then walks over to the big boss about the call
4. The big boss then figures out what to do about the call

If we break our example up into pieces, the:

* secretary is the _ViewModel_ since she answers and delivers calls
* big boss is the _controller_ because he determines what to do with the calls
* the phone is the _view_ since the secretary interacts with it

### Binding

Binding is a way of telling the ViewModel to run code based on certain
states that the ViewModel receives. In our secretary example, binding can
be shown where the boss is instructing his secretary. Because the secretary
is informing the boss and not vice-versa, we would call this a *one-way 
binding*.

Angular also does *two-way bindings* where the secretary and the boss
would inform each other of new phone calls.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/angular-basics' title='Angular Introduction'>Angular Introduction</a> on Learn.co and start learning to code for free.</p>
