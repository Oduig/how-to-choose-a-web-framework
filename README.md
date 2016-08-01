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

This is the definitive guide on *how to make a full-featured website from scratch*.

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

> If product development is a drag race, using the wrong approach is driving really fast in a random direction.

Many greenfield projects have a limited budget to prove their value. If they can't, the project gets cancelled.
Each project functions like a start-up, and the unfortunate truth is that [90% of new products fail](http://fortune.com/2014/09/25/why-startups-fail-according-to-their-founders/). 
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

## Analyzing the requirements
Now that you know what you are building, it's time to take another look at the **requirements**. Start with an empty page and write down those things that actually apply to *your* product. 
All the requirements above should automatically translate into meaningful trade-offs. Since it's rather hard to generalize, here are some examples:

- Are the users technically capable to update their browsers? No: support IE6 but consider dropping the rich client. Yes: limit yourself to *evergreen* browsers, 
  use *feature detection* and show a friendly notice if the user is too far behind the curve.
- Will you go bankrupt if the website is hacked? Yes: hire a security expert for advice.
- Will people die if the website goes down? No: 99% uptime is probably good enough. Perhaps you can tolerate additional downtime at night.
 
**Technical choices** like HTML5, REST and microservices should not be included in the requirements, unless your users are software developers or systems administrators. These 
choices should be made (or not made) in the architecture phase. 

## Product architecture

Once you reach the *MVP* phase, your decisions affect the long-term value and maintainability of the software.
This is where you start looking at the **architecture**. There are many ways to define a good architecture, for example:

> A good architecture maximizes the number of decisions *not* made. - Robert "Uncle Bob" Martin

> To make decisions revocable you need to design for flexibility. - Martin Fowler

It sounds counter-intuitive. Isn't the job of an architect to make decisions and get them right the first time? 
Wouldn't *no architecture* be the best architecture?

The point is that no matter how good you are, you *will* get it wrong some of the time and some requirements *will* change. The goal is not to prevent architectural changes but to make them as easy as possible. So, what decisions do you *need* to make that cannot be sensibly delayed?

#### Anatomy of a web application

Every web application has a **backend** server which provides the **frontend** (a browser) with a *view* and some *data*. 

The **view** typically consists of HTML for layout, CSS for presentation and JS for behavior. There are exceptions. In fact, there are so many alternatives that it warrants a section in and of itself. At the system level, it is sufficient to remember that the browser receives a view from the server and somehow renders it into a web page.

In a **static** web application, **data** is *embedded* in the view by the server and fully rendered to HTML before it is sent to the client. Each time you want new data, you refresh the page. Very little *client-side scripting* is necessary to display the page. Static web pages are good in scenarios where the browser is slow or the data doesn't change much. An example of this is your yearly tax report. That said, most use cases for a static website can also be implemented dynamically, which offers several advantages.

**Dynamic** web applications send the view and data to the client separately. The *browser* combines the two with scripting and generates the complete HTML. While this is slightly more work for the client, it has many advantages:

- Reduced server load thanks to client-side rendering
- Separation of data and presentation
- The same data can be used in multiple views
- The browser does not need to refresh when requesting/submitting data
- Requests are smaller and faster

The choice between static and dynamic web pages may rule out certain technologies. It is therefore a choice that you should make in the architecture phase. Today, dynamic web pages are the gold standard. Nearly all modern technologies are aimed at dynamic content and its community is much larger. You need a *really* good reason to choose a static application. If you have an example of such a reason, please put it here!

#### Data exchange

On the web, clients talk to the server by doing HTTP requests to URLs. URLs conform to a certain *architectural style*. Requests and responses may contain data in some *data format*.

The most common **architectural style** is REST, which uses the path section of URLs to access named resources through a stateless interface. Other options are websockets or SOAP. One example where REST is not ideal is controlling physical machinery where the server is inherently stateful. Modeling state transitions (which are generally verbs) on top of REST can be cumbersome; RPC-style websockets are much more convenient in that situation.

If you did not pick SOAP, you can also choose a **data format**. Since the client is generally written in JavaScript, *JSON* is most common and easiest format to deal with. For certain types of data, you might choose *plain text*. *XML* also has a [great past](https://www.google.com/trends/explore#q=json%2C%20xml&cmpt=q&tz=Etc%2FGMT-2), but has been losing traction due to its verbosity and ambiguity with sequences and plain text nodes. It's still quite popular in enterprises for legacy reasons.

For both XML and JSON, there are **schema specification formats** which describe the data model. These models specify e.g. which parameters are required and which are optional, minimal and maximal values, etc. These specifications can be really useful for *code generation* when multiple 
parties produce and consume the same messages.

Data exchange can be mixed and matched if necessary. It is not a critical choice by itself, but some languages and frameworks have better support for certain styles and data formats. Choosing a specific format might influence your decisions later on. 

#### Monolith vs Microservices

This is a decision that influences most technological choices as well as the integration and release cycle. There are those that consider microservices the only way forward, but [monoliths are simpler as long as you can manage the complexity](http://martinfowler.com/bliki/MicroservicePremium.html). An MVP is generally not complex enough to warrant a microservices architecture by itself. The question becomes: do you think you will need it later? 

There are ways to [start with a monolith and expand it to a microservices architecture later](http://martinfowler.com/bliki/MonolithFirst.html). An example is to gradually split off services from the monolith and rewrite them as microservices. As long as the monolith was designed with stateless behavior in mind, a HTTP proxy can redirect relevant traffic to the new service and everything still works as before. Over time the monolith will shrink and the new architecture will take over. 

Choosing a simple start with a migration path to a more complex future is *still* a decision, but it is a *flexible* decision.

#### Data storage
At some point your application likely needs to store data. Here are your options.

- Cache (volatile)
- SQL database
- NoSQL database
- Filesystem

###### TO BE CONTINUED...

#### Languages

#### Server-side frameworks

#### Client-side frameworks
More of a "how to find the right framework" instead of "what is the right framework".

- Funny quotes
- TodoMvc
- Framework benchmarks
- Technology radar

#### Folder structures
Sort by topic

#### Version control
Simple. Learn git, and then use it.

#### Deployment infrastructure
Jenkins, containers, cloud vs physical.

## Design and implementation
You have made the necessary architectural choices and are now ready for the next phase: installing and configuring all the tools, designing the features and implementing the solution. 

This guide can't hold your hand forever. If you have any question about web technologies, chances are someone has already posted it on StackOverflow. In fact, even if you already know the answer, it's still good to go there and see what other people think. The web is a moving target, and you do yourself a disservice by assuming you already know everything!

## Education
Resources on Coursera etc.

## About
Notes about me
