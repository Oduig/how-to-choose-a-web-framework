# How to make a website
The word is in. Someone has formulated a master plan to conquer the market.
Their first step is to reach as many users as possible,
for as small an effort as possible. They have chosen the most portable and
most widespread platform *in the world*: the web.

Eager to start on a greenfield project, you take the bag of money and get started.
Here are the requirements:

- The site should work in **all browsers**, including Safari, Opera and IE6.
- It should work on **all devices**, including but not limited to PCs, iPhones,
  Blackberries, smartwatches and the latest VR headset on Kickstarter.
- It should have a **rich client** with **HTML5**, **form validation** and **UX**.
- It should have reusable a **REST API** on the server.
- It should have a database with reliable **backups** and **historic** traceability.
- It should be **fast**, completely **secure** and always **available**.
- It should use **microservices**, **continuous integration** and this thing called **Docker**.

Full of energy, you get started.

## Introduction

This is the definitive guide on *how to bootstrap a full-featured commercial website*.

The **scope** is limited to websites where most of the above requirements are important.
If you just want a page for your local book club, you *could* follow this guide,
but a blogging platform like Wordpress would likely suit you better. The assumption is that your website is special and needs to be custom-built by real
software engineers. You are one of those software engineers. You already know the basic building blocks of the web, and seek help with the alarming
number of choices you face before you can deliver your first feature.

As the **author**, I am writing from my own experience as a full-stack web developer, in the interest of
 speeding up the bootstrapping phase of new web projects. I am just one voice in a very big crowd, and I cannot be
 an expert on *all* of the discussed topics.
 I ask you to judge the content on its merit and encourage you to share different views.
Feel free to submit pull requests for additions, clarifications, grammar fixes or any sort of change
in general that would improve the text. If this resonates with a lot of people,
we might even tackle the biggest challenge of them all: keeping a guide on web technology up to date.

## Before you start

Back to your project. Before you start any software project,
regardless of what anyone tells you, there are a few things you must do.

#### Understand the problem
If you are going to make technology choices and a system-level architecture, you should start with understanding the problem.
 Quite often, companies make initial assumptions for estimation and quotation purposes. That's normal. It will help you to know
 what those assumptions were so you can provide insight from your technical point of view.

You could use the following checklist, and add questions of your own.

- What was the *problem* that led to the decision of building a new website?
- Who are the *users*?
- What do they *need*?
- Who are the other *stakeholders*?
- What exactly did they *ask* for?
- Is a website indeed the right solution?
- Does it indeed need to be a *custom-built* website?
- What is the *cost* and *merit* of the proposal?

If you raise even one doubt with these questions, don't skip over them.
Use the [5 Whys](https://en.wikipedia.org/wiki/5_Whys) or similar techniques.
You want to build something that lasts, and to do that you need to figure out *what is important, and what is not*.
Which brings us to the process.

#### Understand the approach
If there is no process in place yet, great! You can create one.
The goal of a process is to coordinate the team, track the progress towards your goal and to minimize risk.

You probably want to choose some sort of Agile framework like *Scrum* or *Kanban*. Decide which one is best for you.
Although *Waterfall* is often frowned at, it can still be the best choice if applied correctly.
More important that the framework is a correct **approach** to building your new product.
```
If product development is a drag race,
using the wrong approach is driving really fast in a random direction.
```

Many greenfield projects have a limited budget to prove their value. If they can't, the project gets cancelled.
Each project functions like a start-up, and the unfortunate truth is that [90% of new products fail](](http://fortune.com/2014/09/25/why-startups-fail-according-to-their-founders/)).
By far the biggest cause of failure is a lack of **product-market fit**. No matter how much effort went into the business case,
you only *really* know a product works when the money starts rolling in.
To reach that milestone as soon as possible, consider the following development **phases**.

1. Conceptualization
2. Prototype
3. Minimal viable product (MVP)
4. Iterative growth

The rationale is as follows. **Conceptualization** means understanding a problem and its proposed solution.
It is likely already done at this point, with or without your help.

A **prototype** is a hacky, ugly, barely-there version of the software.
The purpose of a prototype is to **validate** the core business case with real users.
 A prototype can be made with pen and paper, wireframing tools, or actual code.
If you choose code, you should write it as fast as possible, without maintenance or
performance in mind. That way it can be built many times faster than a production-ready MVP.

Prototypes are meant to be **discarded** after they serve their purpose. It was not built with
 maintenance in mind, and those who try building an MVP on top of it will tell you it's a nightmare. Keep in mind that the
 real value of the prototype was to validate the business case and to gain information, not to develop the product.
 If you have any doubt that the prototype will be discarded, *don't make one* and skip to the MVP.

The **MVP** is a properly designed and fully implemented solution. It should have *at least one* feature that
solves a problem for a real user, making it **viable**. If there is any feature that you could *omit* without
destroying the viability, you should. A **minimal** product is easier, faster and cheaper to build,
allows an early launch and enables more input from real users.

After the MVP, the groundwork is done and the stage is set. The product is ready for **iterative growth**.
Conceptualize new features, judge their added value, build the features and validate them against real users. Try
to formulate objective **metrics** to determine whether or not a feature has merit. If it does not, be
ruthless and remove them from the product. After all, they have a maintenance cost but bring no added value.

## Product architecture

Once you reach the *MVP* phase, your decisions affect the long-term value and maintainability of the software.
This is where the **architecture** really begins.

#### TO BE CONTINUED...
