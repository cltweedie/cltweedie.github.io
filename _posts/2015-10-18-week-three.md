---
layout: post
title: "Week Three: Databases and Active Record"
date: 2015-10-18
categories:
comments: true
---

It's the end of week three, meaning we're now a quarter of the way through the course! I've learned a lot this week. We've been covering brand new topics, but we've been building on the foundations from the topics last week - we've been using TDD consistently and have come across several design patterns when working with Active Record.

Prior to Monday, we had built some programs that persisted data using YAML files. This is fine for when the data is fairly simple, but for larger and more complicated datasets, the best option is to use a database.

SQL
---
[Structured query language](https://en.wikipedia.org/wiki/SQL) is the way that humans (and ORMs - more on this shortly) create and interact with databases. The basic syntax is fairly straightforward. For example, a command to create a new table to store contact information in [SQLite3](https://www.sqlite.org) might look like this:

~~~
CREATE TABLE contacts (
  id integer primary key,
  name varchar,
  phone_number varchar,
  email varchar
);
~~~

A command to insert a row into this table might look like this:

~~~
INSERT INTO contacts VALUES (1, 'Chris', '07777777777', 'cltweedie@gmail.com');
~~~

...and a simple query to return every row with the name of "Chris" will look like:

~~~
SELECT * FROM contacts WHERE name = 'Chris';
~~~

Things get a bit more complicated when you start thinking about [normalization](https://en.wikipedia.org/wiki/Database_normalization), the process of reducing row duplication. Relational databases typically consist of multiple tables that are connected to each other through foreign keys. In the case of more complicated 'many to many' relationships, join tables are needed to hold the foreign keys from both of the existing tables.

This might not make much sense to anyone unfamiliar with the subject, but this isn't meant to be a lesson in relational databases. SQL databases can get quite complicated, and that's where ORMs come in.

Active Record
------------
Active Record is an [Object Relational Mapper](https://en.wikipedia.org/wiki/Object-relational_mapping), a tool for representing data inside a database as objects in Ruby. So a table called 'contacts' will have a corresponding *Contact* class (model), like so:

~~~
class Contact < ActiveRecord::Base
end
~~~

This means we can create new contacts like this:

~~~
@contact = Contact.create!(
  name: "Chris",
  phone_number: "07777777777",
  email: cltweedie@gmail.com
)
~~~

and ActiveRecord will generate the SQL and insert this into the table for us. Inheriting from ```ActiveRecord::Base``` also provides our object with read, update and delete functionality to complete the [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) actions.

Two of the most useful features of Active Record are migrations and validations, which are great for making changes to our schema and checking user input respectively. After dealing with pure SQL for a couple of days, being introduced to Active Record was great.

Blog Engines
------------

Our assignment over the last few days has been to create the back-end (the database and models) of a blog engine using Ruby. We initially constructed the tables using SQL, but later used Active Record migrations to achieve the same thing. We then created the relationships between models (using methods like belongs_to and has_many), before adding validations to each of them. I'm happy to say that I achieved the task of building the back-end, but also managed to create the front-end! It's not especially pretty, but it looks like this:

![The Blog](http://imgur.com/cYksi0D.png)

It currently allows viewing all posts, viewing individual posts, adding new posts, editing and deleting existing posts, as well as viewing all posts tagged with a certain word by clicking on the tag.

I used the models created in the assignment and built an application using the Ruby framework [Sinatra](http://www.sinatrarb.com/) to define routes and create views for the pages (using ERB). I made the whole thing look passable using the CSS framework [Bootstrap](http://getbootstrap.com).

I realise it might not look like much, but building an app like this and really understanding how all the parts work is pretty exciting.

At the moment, it's missing a few features like authentication (which would be pretty important in a real app!), but I'm glad I managed to get this far with it considering we haven't yet covered Sinatra on the course (although I have used it to make simple apps in the past).

It's beginning to feel like the topics we've been covering for the last three weeks are starting to coalesce to form a whole. It makes me happy to think about how much I've learned in a short time, and how much more I should learn over the coming weeks.

Next week is all about networking, which I believe will cover HTTP and Sinatra - so more on this in my next post!
