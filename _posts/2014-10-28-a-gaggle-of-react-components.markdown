---
layout: post
title:  A Gaggle of React Components
date:   2014-10-28 22:33:00
categories: software react
---
Let's walk through a common React.js pattern, making a list of things.  The idea today is to get a sense of how to unravel a problem with a live example.

So, let's start.  Generally, there is a thing:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var Task = React.createClass({
  render: function() {
    return (
      <h1>Task</h1>
    )
  }
});

module.exports = Task;
{% endhighlight %}

This creates a single component.  I've tried to make it as simple/plain as I can.  Now, imagine it with data:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var Task = React.createClass({
  render: function() {
    var task = {id: 1, title: "Something to do"};
    return (
      <h1>{task.title}</h1>
    )
  }
});

module.exports = Task;
{% endhighlight %}

The important thing to grasp is that we've added a variable inside a function (just for now), and we use it (var task = ... and {task.title}).  Also, notice, we use the curly braces.  It's important to feel comfortable with this, and practice will get you further down the road than anything else.  The point here is that we're __starting with things we're comfortable doing.__

Now, if that's all good, let's talk about a task list.  The trick, for me, is to start with what I have and go from there.  That keeps me from trying to memorize a bunch of steps.  I should understand each step, then remember what else I need to have.

So, let's do this:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var TaskList = React.createClass({
  render: function() {
    return (
      {taskViews}
    )
  }
});

module.exports = Task;
{% endhighlight %}

Notice, it's the same as the first snippet, but with a {taskView} added.  Also, notice, __this is a decision__: there should be something there, and we have to name it.  By naming it, we have to have an opinion (at least a small one, the safe and easy kind) about what that thing is.  I could call it tasks, that's fine.  I might come back and decide that's a little confusing later.  But, there is something that should be added, and taskViews tells my mind that there's a list of views in that variable.

Now, one thing I like to do when I'm tired is let things fail.  It's more of a game that way.  Everything blows up, just like I thought it should.  If it doesn't blow up, I sit down and understand what's going on.  Remember, we're trying to __comfortably unravel a problem__.  So, the workflow is important.  So, let it blow up, or try and find where it blows up.  You'll get a sense of what's happening where.  That's a good thing.

So, let's create that variable:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var TaskList = React.createClass({
  render: function() {
    var taskViews = tasks.map(this.renderTask);
    return (
      {taskViews}
    )
  }
});

module.exports = Task;
{% endhighlight %}

This will blow up as well.  Good.  I've done something normal (created a variable) and some weird things:

* map was introduced
* a new method is expected to be on the TaskList
* tasks is introduced, with no introduction

Now, you might not choose to do all of this.  It's a single line of code, but you could say var taskViews = something else.  Or, you may decide that you need the data at the same time:

{% highlight javascript %}
var data = [{id: 1, title: "A task"}, {id: 2, title: "Another task"}];
{% endhighlight %}

That's where we're going, it's kind of a high-wire act.  You'll get a feel for how you approach this.  Let's not get ahead of ourselves.  I introduced map, let me deal with that.

Map is a function.  You may already know it.  The format is:

    someData.map(someFunction);

It's an easy way to produce a list of views from a list of data.  Every item in the tasks list is passed to this.renderTask.  Remember, that function doesn't exist yet.  It was a decision that helped me think about what I need next: a way to produce a task view.

I should probably put some training together about how to comfortably use these kinds of ideas in your code.

OK, let's review what that last step did:

* __map:__ make a list from another list
* __new method:__ make a decision about what it needed next
* __data:__ make a decision about where the data is coming from

Let's look at the same thing, but with the tasks variable defined.

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var TaskList = React.createClass({
  render: function() {
    var tasks = [{id: 1, title: "A task"}, {id: 2, title: "Another task"}];
    var taskViews = tasks.map(this.renderTask);
    return (
      {taskViews}
    )
  }
});

module.exports = Task;
{% endhighlight %}

Nothing new here, we're just making sure we can see the whole thing in one place:

* there's a regular component
* there's taskViews rendered in the component
* taskViews are created from tasks and another function
* tasks are a loose guess about what a task should have

I should say that I may add or remove attributes from the list of tasks.  To be honest, I decided to use id in that list.  Now, here's something hard about coding.  When you write your own code, things sneak into your thinking without you noticing them.  Id is a common thing to have.  It's a convenient thing I'll use in the next step.  When you are unraveling a problem, you'll find your own path.  __The important thing here is that you inch yourself along.__  There's always a path from what you understand to what you need to deliver.

Maybe a more important lesson is, __this isn't about finding a perfect pattern, it's about finding your way as you go along.__

OK, so, we're getting there.  The next step was introduced from the last step: there's a reference to this.renderTask.  Let's implement that:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var TaskList = React.createClass({
  renderTask: function(task) {
    return (
      <p>{task.title}</p>
    )
  },
  render: function() {
    var tasks = [{id: 1, title: "A task"}, {id: 2, title: "Another task"}];
    var taskViews = tasks.map(this.renderTask);
    return (
      {taskViews}
    )
  }
});

module.exports = Task;
{% endhighlight %}

I like to sometimes be so slow with work...it's because I need to practice.  I want to get workflow habits that creep into future problems.  If I've done this a hundred times, I will likely have some other thing on my mind when I'm making a list.  So, the old practices creep into the new ones...sometimes a good thing.

So, here, I've just made a lame function that returns a paragraph tag and a task title.  Probably I'll want a list item.  Before we add that, you could take a look at the page we're creating in the Developer Tools.  There will be a warning there about a key.  React is more efficient when lists have a key defined:

    <p key={task.id}>{task.title}</p>

That should work nicely.

Cleaning up the HTML a bit:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var TaskList = React.createClass({
  renderTask: function(task) {
    return (
      <li key={task.id}>{task.title}</li>
    )
  },
  render: function() {
    var tasks = [{id: 1, title: "A task"}, {id: 2, title: "Another task"}];
    var taskViews = tasks.map(this.renderTask);
    return (
      <ul>
        {taskViews}
      </ul>
    )
  }
});

module.exports = Task;
{% endhighlight %}

The TaskList is now creating a list, setting the key to every item in the list.  Almost there.  Let's pull the render method out into its own component.  It's going to introduce a few things that make sure you understand what you're really up to.  Let me show you:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');
var TaskSummary = require('./task-summary');

var TaskList = React.createClass({
  renderTask: function(task) {
    return (
      <TaskSummary task={task} />
    )
  },
  render: function() {
    var tasks = [{id: 1, title: "A task"}, {id: 2, title: "Another task"}];
    var taskViews = tasks.map(this.renderTask);
    return (
      <ul>
        {taskViews}
      </ul>
    )
  }
});

module.exports = Task;
{% endhighlight %}

And then in the task-summary.js file in the same directory:

{% highlight javascript %}
/** @jsx React.DOM */
var React = require('react');

var TaskSummary = React.createClass({
  render: function() {
    var task = this.props.task;
    return (
      <li key={task.id}>{task.title}</li>
    )
  }
});

module.exports = TaskSummary;
{% endhighlight %}

Here are the important parts:

* The TaskList uses require to find the TaskSummary code.
* The require statement uses './task-summary' instead of 'task-summary'.  If it's not an installed library, we need to give require a path to the file.
* <TaskSummary> is an HTML component, defined with the TaskSummary code (like any other component), but with the task passed into it.
* The TaskSummary render function pulls the task out of this.props.task and uses it.

Those are the only points I can think to bring up.  If you get lost, drop me a note and I'll try and update this.  Let's see if I've taught anything:

* You don't typically have the answers with something new.
* Practice helps you build confidence with this kind of thing.
* I try and use code that I wish I had, then fill in the gaps.
* I recognize that even when I try and keep my thinking clean, a lot is going on.
* Sometimes code that stays modular and simple requires that I understand things deeply.

Those lessons might not be easily won, however.  It's not all good news, I guess.  I suggest you take this basic idea and seriously drill yourself on it.  That's my habit when I'm trying to adopt a new-to-me technology.
