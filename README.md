[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# Full Stack Project Modeling Lab

During this lab we are going to talk project ideas, how to take a 'shoot for
the stars' idea, and build it in a methodical fashion that will keep you on
track, while fixing *one* problem at a time.

When you're starting out as a developer, it's often a struggle to take a
grandiose idea and consolidate it into more manageable pieces.

## Prerequisites

- [full-stack-project-practice](https://git.generalassemb.ly/ga-wdi-boston/full-stack-project-practice)

## Objectives

By the end of this, developers should be able to:

- Properly scope projects.
- Break apart an ERD into a 'to-do' list.
- Plan feature progress effectively.
- Prioritize objectives/tasks and descope accordingly.

## Preparation

1. Fork and clone this repository.
 [FAQ](https://git.generalassemb.ly/ga-wdi-boston/meta/wiki/ForkAndClone)
1. Create a new branch, `training`, for your work.
1. Checkout to the `training` branch.

## What is `scope`? Why it is important

Scope is typically a list of features or goals you have in mind for your
project. For example, if I wanted to have users be able to sign up, log in,
change password, etc. those are all features I would like my application to
have. They are *within* the scope of my project.

## What is `MVP`? Why it is important

MVP, **Minimum Viable Product**, not Most Valuable Player, is a product that
meets the minimum specifications or *requirements*. If I have a project idea
that includes multiple features and accesses 3rd party APIs, the additional
features would be *extra* for my project. The base level of the project would
include the barest minimum in order to have a working application.

## Demo: Write an ERD and prioritize it

Let's take our 'library-api' as an example. In this domain, our main resource
is *books*. Books should belong to authors though, so we can look up all the
books that belong to an author, right!? What happens if an author has multiple
books, but some books have multiple authors!? We also probably need to have
*users* so that they can take out books, and users need to have passwords, and
need to be able to change their passwords, and what if we have multiple books,
can multiple users take out different versions of the same boo--[ohh no I've gone crosseyed](https://i.imgur.com/a7Yyjg8.gif).

Let's back it up, and take it one step at a time. Books. Books is our first
custom resource. So let's start there. The scope of my project would likely
just start with Books. I would make sure I could CRUD on Books, then I would
add a relationship to Users. Once that worked I would think about adding some
Authors.

Remember, it's OK for your ERD to change!

If I were building this out, I would start with just Book. ![Book](https://i.imgur.com/bXtwCKO.png)

Once I had CRUD working on Book (using curl and perhaps a dummy client), I
would move on to User ownership.

To add User ownership I would first make sure that I can do all the
authentication steps that I would expect to be able to. That means signing up
and in and changing my password, as well as signing out.

![User](https://i.imgur.com/gGSAgI4.png)

Now we need to build a relationship between these resources so that a Book is
owned by a User. With that in place, we don't want to have any Books remaining that are not owned by a User.

![Relationship](https://i.imgur.com/U7o0eVS.png)

Test the relationship. Make sure you can get all Books that belong to a
User. We should also make sure that as another User, I can't delete the Books created by the first User.

What's next? Let's bring in that Author model, we want to be able to have a relationship between Books and the Author that wrote them, before we can have a relationship we need the appropriate resources.

![Author](https://i.imgur.com/QIevbE9.png)

Boom. Now we have Authors. Let's pause for a second for some `testing best practices`!

## CURL Scripts: The why

CURL is your friend. It allows us as developers to *completely eliminate* the
front end or client from the equation. After you've built out a feature with
your API your FIRST inclination should be to test it with CURL. Because of this
we've put a `/scripts` directory in each of the templates we provide. Do
Future You a favor and start writing them out, save, and commit ones that you
know work. That way when you come back later and want to add a feature, it's
easy to test your previous work!

## Demo Continued

Where were we? Because we have our overall ERD mapped out already, we have a
roadmap for where our final destination is. At this point, our current relationship between Users and Books does not reflect how our ERD is set up. We also don't have a relationship yet between Books and Authors.

It's time to choose your own adventure... Should you a) add a join table
because you know you're going to want Books and Authors to have a `many-to-many`
relationship further down the road? OR b) build out your API methodically,
making sure everything is working before jumping in the deep end? If you picked
a) you're likely setting yourself up for headache.

a) ![a](https://i.imgur.com/AiQVpVd.png)

b) ![b](https://i.imgur.com/1b3hySk.png)

Start with b. Once it's working properly then you can add the join table.

Remember: It's OK to change your ERD. It's ok to modify your database. There
are things to remember when you do, but don't feel like you need to get your
database and relationships all set up perfectly on Day 1. Things change, and
that's ok. The only way to be methodical when you build out these features is
to be ok with that inevitable change.

## Lab: Consider the previous example

Think about the example we just ran through.

- What are the *must* haves?
- What are the nice to haves?
- Are there any resources we could do without?
- What would we sacrifice if we aren't developing features as fast as we'd hoped?
- What if I wanted Books to be able to be checked out by multiple Users?
  - How would our ERD change?
- What if I wanted there to be two types of users; admins and non-admins?
  - What priviliges would I allow?
  - How would I control user AND admin ownership?

## Lab: Pitch Time

You all should've completed the [full-stack-project-practice](https://git.generalassemb.ly/ga-wdi-boston/full-stack-project-practice) at this point. We'll go around the room, and have people present,
or share their ideas and we'll descope and prioritize them together. Once we're
done, think about how YOUR project might be descoped, and what the priorities
are. Set yourself up for success! If you're unclear by the end of all of this,
schedule a 1-1 with a consultant to review your ERD, wireframes, and plan of
attack!

## [License](LICENSE)

1. All content is licensed under a CC­BY­NC­SA 4.0 license.
1. All software code is licensed under GNU GPLv3. For commercial use or
    alternative licensing, please contact legal@ga.co.
