---
layout: post
title: "The Second Week"
date: 2015-10-11
categories:
comments: true
---

For me, this week was a step up; both in terms of subject matter and difficulty. I'm still having a great time, but I've probably said "I'm confused" more in the last week than I have in the last year.

The focus of the lessons and assignments for the last few days has been [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development) (TDD) and [design patterns](https://en.wikipedia.org/wiki/Software_design_pattern). Last week we covered the fundamentals of Ruby and object-oriented programming, most of which I was already fairly familiar with. The subjects this week were relatively new concepts to me (before Monday I had only ever written a handful of tests and never implemented a pattern), so, understandably, I had some difficulty getting my head around some of the ideas.

TDD
---
Test-driven development, as an idea, is pretty straightforward. Before you implement any part of your program, you write some tests that you expect to fail initially, but which will help guide you toward the finished implementation. For example, a test (using the Ruby library [Minitest](https://github.com/seattlerb/minitest)) for a calculator might look like this:

~~~
describe "A calculator" do
  it "adds two numbers" do
    Calculator.add(5, 5).must_equal 10
  end
  it "multiplies two numbers" do
    Calculator.multiply(5, 5).must_equal 25
  end
end
~~~

You then run these tests without writing any code for the calculator, and you'll see the following error:

~~~
1) Error:
A calculator#test_0001_Adds two numbers:
NameError: uninitialized constant Calculator
    calculator.rb:5:in `block (2 levels) in <main>'
~~~

"Uninitialized constant Calculator" is telling you to create a Calculator class. You then follow the errors and failures until you have a working calculator (adding more tests as you go).

The idea isn't difficult, but learning the discipline of the test-first approach can be frustrating, especially when you know exactly what needs to be coded without writing a test. The benefit is with bigger, more complex programs where writing the tests first can help you to think through the implementation, as well as the assurance of having a bunch of tests keeping an eye on your code in case you break something by adding a feature.

The more I write and use tests, the more I appreciate their value, and I'm happy to say I'm getting more comfortable with writing programs test-first.

Design Patterns are Hard
------------------------
Factory, Observer, Strategy, Command. These are four examples of design patterns, which are "prepackaged solutions to common design problems" ([*Design Patterns in Ruby*](http://www.amazon.co.uk/Design-Patterns-Ruby-Addison-Wesley-Professional/dp/0321490452), Russ Olsen).

In software development, the same problems often occur repeatedly. Design patterns exist to provide go-to solutions for these problems, as well as helping with general good-practice concepts like minimising the coupling between different classes and objects.

I think some of the difficulty comes with the abstraction - it's one thing to understand a class as being a blueprint for an entity like a calculator or a button, but it can be confusing to start imagining classes for more conceptual things like strategies or commands.

I won't go into detail about each of these patterns, as that could easily be a post unto itself. The book mentioned above is a great introduction if you want to find out more.

Through our assignments, these ideas and techniques are becoming clearer, but I think I will have to work with design patterns a lot more to be able to utilise them properly.

Confusion is Temporary
----------------------
As I explained at the start of this post, this is the first week where I've been exposed to new subjects, and it's a bit jarring. The other trainees are in a similar position, however, and it's comforting that everyone struggles with understanding this stuff. I think it's important to put things in perspective: when I first started programming, I struggled with a lot of things that seem easy to me now. I hope to look back and wonder how I ever had trouble implementing the strategy pattern.

I've come to appreciate that the problems that seem the most difficult are the most satisfying to solve, and the subjects that are the most confusing are the most satisfying to understand.

Next week is all about databases. This is another subject with which I have limited experience, so I'm expecting it to be challenging - but I'm excited to get started. Watch this space for how I get on.
