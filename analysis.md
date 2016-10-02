# Before you start

Before you start any new software project, regardless of what anyone tells you, there are a few things you must do.

## Understand the problem
If you are going to make technology choices and a system-level architecture, you should start by understanding the problem.
Quite often, companies make technological assumptions early in the project to come up with good cost/time estimations. That's normal. It definitely helps if you know what those assumptions were so you can gain insight from your technical point of view.

You could use the following checklist, and add questions of your own.

- What was the *problem* that led to the decision of building a website?
- Who are the *users*?
- What do they *need*?
- Who are the other *stakeholders*?
- What exactly did they *ask* for?
- Is a website indeed the right solution?
- Does it need to be completely *custom-built*?
- What is the *cost* and *merit* of the proposal?

If you raise any doubt with these questions, don't skip over them.
Use the [5 Whys](https://en.wikipedia.org/wiki/5_Whys) or similar techniques.
You want to build something that lasts, and to do that you need to figure out *what is important, and what is not*.
Which brings us to the process.

## Choose a process
If there is no process in place yet, great! You can create one.
The goal of a process is to coordinate the team, track the progress towards your goal and to minimize risk.

You probably want to choose some sort of [Agile](https://en.wikipedia.org/wiki/Agile_software_development) framework like [Scrum](https://en.wikipedia.org/wiki/Scrum_(software_development)) or [Kanban](https://en.wikipedia.org/wiki/Kanban_(development)). Decide which one is best for you.
Although [Waterfall](https://en.wikipedia.org/wiki/Waterfall_model) is often frowned upon, it *can* be the best approach if applied correctly.
More important that the framework is a correct **approach**. You might be agile and coding faster than anyone else, but if you're going in a random direction you won't get anywhere.

Many greenfield projects have a limited budget to prove their value. If they can't, the project gets cancelled.
Each project functions like a start-up, and the unfortunate truth is that [90% of new products fail](http://fortune.com/2014/09/25/why-startups-fail-according-to-their-founders/). 
By far the biggest cause of failure is a lack of [product-market fit](https://en.wikipedia.org/wiki/Product/market_fit). No matter how much effort went into the business case,
you only *really* know it's good when the users come in, stay in, and start generating revenue.
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
performance in mind. That way, it can be built many times faster than a production-ready MVP.

Prototypes are meant to be **discarded** after they serve their purpose. It was not built with
 maintenance in mind, and those who tried building an MVP on top of a prototype will tell you it was a nightmare. Keep in mind that the
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

## Analyze the requirements
Now that you know what you are building, it's time to take another look at the **requirements**. Start with an empty page and write down those things that actually apply to *your* product. 
All the requirements above should automatically translate into meaningful trade-offs. Since it's rather hard to generalize, here are some examples:

- Are the users technically capable to update their browsers? No: support IE6 but consider dropping the rich client. Yes: limit yourself to *evergreen* browsers, 
  use *feature detection* and show a friendly notice if the user is too far behind the curve.
- Will you go bankrupt if the website is hacked? Yes: hire a security expert for advice.
- Will people die if the website goes down? No: 99% uptime is probably good enough. Perhaps you can tolerate additional downtime at night.
 
**Technical choices** like HTML5, REST and microservices should not be included in the requirements, unless your users are software developers or systems administrators. These 
choices should be made (or not made) in the architecture phase. 