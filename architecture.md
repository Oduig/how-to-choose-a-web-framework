# Product architecture
---

Once you reach the *MVP* phase, your decisions affect the long-term value and maintainability of the product.
This is where you start looking at the **architecture**. There are many ways to define a good architecture. Some related quotes:

> A good architecture maximizes the number of decisions *not* made. - Robert "Uncle Bob" Martin

> To make decisions revocable you need to design for flexibility. - Martin Fowler

It sounds counter-intuitive. Isn't the job of an architect to make decisions and get them right the first time? 
Wouldn't *no architecture* be the best architecture?

The point is that no matter how good you are, you *will* get it wrong some of the time and some requirements *will* change. The goal is not to prevent architectural changes but to make them as easy as possible. So, what decisions do you *need* to make that cannot be sensibly delayed?

## Anatomy of a web application

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

## Data exchange

On the web, clients talk to the server by sending HTTP requests to URLs. URLs conform to a certain *architectural style*. Requests and responses may contain data in some *data format*.

The most common **architectural style** is [REST](https://en.wikipedia.org/wiki/Representational_state_transfer), which uses the path section of URLs to access named resources through a stateless interface. Some standards for REST are defined in the [Open API Specification](https://github.com/OAI/OpenAPI-Specification). If REST does not suffice, other options are [SOAP](https://en.wikipedia.org/wiki/SOAP) and [WebSocket](https://en.wikipedia.org/wiki/WebSocket). One example where REST is not ideal is controlling physical machinery where the server is inherently stateful. Modeling state transitions (which are generally verbs) on top of REST can be cumbersome; RPC-style websockets are much more convenient in that situation.

If you did not pick SOAP, you can also choose a **data format**. Since the client is generally written in JavaScript, [JSON](http://www.json.org/) is most common and easiest format to deal with. For certain types of data, you might choose *plain text*. *XML* also has a [great past](https://www.google.com/trends/explore#q=json%2C%20xml&cmpt=q&tz=Etc%2FGMT-2), but has been losing traction due to its verbosity and ambiguity with sequences and plain text nodes. It's still quite popular in enterprises for legacy reasons.

For both XML and JSON, there are **schema specification formats** which describe the data model. These models specify e.g. which parameters are required and which are optional, minimal and maximal values, etc. These specifications can be really useful for *code generation* when multiple 
parties produce and consume the same messages.

Data exchange can be mixed and matched if necessary. It is not a critical choice by itself, but some languages and frameworks have better support for certain styles and data formats. Choosing a specific format might influence your decisions later on. 

## Monolith vs Microservices

This is a decision that influences technology choices as well as the integration and release cycle. Some people consider microservices the only way forward, but [monoliths are simpler as long as you can manage the complexity](http://martinfowler.com/bliki/MicroservicePremium.html). An MVP is generally not complex enough to warrant a microservices architecture by itself. The question is: will you need one later? Most likely, you just don't know.

An alternative is to [start with a monolith and expand it to a microservices architecture](http://martinfowler.com/bliki/MonolithFirst.html). When complexity becomes a problem, you can gradually split off services from the monolith and rewrite them as microservices. As long as the monolith was designed with stateless behavior in mind, a HTTP proxy can redirect relevant traffic to the new service and the users remain completely unaware of the change. Over time the monolith shrinks and the new architecture takes over. 

## Backend
For reasons mentioned under *Data Exchange*, we will assume that there is a backend providing an API to rich client-side applications. The backend is the area of your web application where most of the business rules reside. As such, it is the area with the most application-specific choices. 

Nearly all web applications use a **server-side web framework** to host their API. **Libraries** perform those tasks that are not covered by the framework. The difference between a framework and a library is that a framework controls the application, and the application controls the libraries. 

In an ideal world, you separate the **application core** (business logic and data models) from the framework. Have a look at the [onion architecture](http://lorifpeterson.com/?p=64). The onion model allows you to change frameworks without touching the core. In reality, most web frameworks make it difficult to do this. For example, Java's Spring framework provides dependency injection and database bindings that are intended to be used throughout your entire application. As a result, most web backends have a core that strongly depends on the framework. If you really don't want this, you have to move away from everything-in-a-box style frameworks and look at framework/library hybrids like Dropbox and Spark

After deciding on the desired structure, you can pick a **language** and a **framework**. Nearly all modern languages have a few battle-tested web frameworks to choose from, and there are many benchmarks and opinions on which is the best. The bottom line is that unless you have very, very strict demands on scalability or response time, all of the popular frameworks can be considered *good enough*.

So how do you choose between all the options? Simple. Choose something that is **modern**, **established** and **familiar** to the developers. 

**Modern** technologies are easier to work with than dated alternatives, especially with the changing nature of the web. Avoid being overly conservative. Going with C++ can easily double your development and maintenance effort, because the available web frameworks are sub-par and too much detail is exposed through the interfaces. The bottlenecks of a web application are nearly always transfer speed (HTTP) and disk IO (database), to the point where the language is hardly even a factor. Instead, aim for something high level like C#, Java, Scala, Python or Node.js. Free and open source technologies have the benefit of larger communities, but may be less focused on enterprise-level support. 

Choose a framework that is well **established**. A production-ready app requires a production-ready framework. Look for the following signs:

- At least version 1.0 (according to [semantic versioning](http://semver.org/))
- Used by at least two well-known companies
- Backed by a company (no single-developer projects)
- Upwards or stable history in [Google Trends](https://www.google.com/trends/)
- At least one [benchmark](https://www.techempower.com/benchmarks/) to compare it to other frameworks
- Good [presence](http://redmonk.com/sogrady/2012/09/12/language-rankings-9-12/) on Google and StackOverflow

Finally, choose whatever is the most **familiar**. There are many good options. When in doubt, follow your own experience or that of the other developers. Choosing something that is already known in your group is a great way to boost development speeds. If you still have multiple options, choose whatever is easiest to hire for. 

## Data storage
At some point your application likely needs to persist its data. Here are your options.

- SQL database
- NoSQL database
- Filesystem

Obviously, the file system is typically used for files that are already in an external file format, such as documents, binaries, images. Databases are used to store metadata and customized user input.

For SQL databases, the most versatile and expressive modern database is [PostgreSQL](https://www.postgresql.org/). In performance it is faster or comparable to its competition, so you need a good reason to choose any other. As a bonus, it also supports JSON columns and sharding across multiple database servers, which allows shifting to a more NoSQL approach within SQL. 

There are benchmarks ([here](https://www.arangodb.com/2015/10/benchmark-postgresql-mongodb-arangodb/) and [here](http://www.enterprisedb.com/postgres-plus-edb-blog/marc-linster/postgres-outperforms-mongodb-and-ushers-new-developer-reality)) showing that the modern variety of SQL is faster than the currently popular NoSQL databases. SQL also has a habit of being easier to manage thanks to the fixed schema. Just like programming languages, dynamic databases are faster to set up but statically typed databases are safer and easier to maintain. As it stands, there are only a few reasons to choose a NoSQL database:

1. Your data is inherently unstructured
2. Your data is more about storing individual things than the relations between the things
3. Your queries are highly graph-centered and *can't* be performed efficiently in SQL
4. You are making a small, pure-Javascript application and JSON is easier to dela with
5. You need to scale to many, many servers and cannot do that with SQL

The rule of thumb is: it's much easier to pick NoSQL for the wrong reasons, than it is to pick PostgreSQL for the wrong reasons.

## Frontend

The state of frontend Javascript frameworks has been subject to a lot of ridicule over the past few years.

#### TODO funny quotes

As of 2016, client-side web frameworks are volatile, but stabilizing. In theory you have hundreds of options, but only a few of them are sufficiently **modern** and **established**.

- [Angular 2](http://learnangular2.com/)
- [EmberJS](http://emberjs.com/)
- [Aurelia](http://aurelia.io/)
- [React](https://facebook.github.io/react/docs/why-react.html) + [starter kit](https://github.com/kriasoft/react-starter-kit)

Both **Angular 2** and **Ember** take the everything-in-a-box approach and dictate the way you write your application. They use their own style of templates and controllers. Angular 2 has less boilerplate as it makes more decisions for you.

**Aurelia** takes an approach similar to Angular 2, but has a more hands-off approach. It lets you write all aspects of the MVC in regular standards-compliant code. This has a great benfit in that you don't need to learn much when using this framework. The drawback is that the framework is new and while there are plenty of support options, the company behind it is less established.

**React** takes a minimalist approach which is very clean and easy to learn. On the flipside, React is not a complete framework so it requires additional choices and library management. There are several *starter kits* available that make these choices for you. If you use react, make sure you do so with legal scrutiny. React has a [patent clause](https://news.ycombinator.com/item?id=11270213) that poses restrictions on its usage. If you work for a large company, they may disqualify it for that reason.

Note that **AngularJS** is absent in this list. It has been replaced by *Angular 2* and is effectively obsolete. Even though it is well established, choosing it means setting yourself up for a big migration in the not-too-distant future.

#### Comparisons
Since all modern frontend frameworks use Javascript and they are all rather new, the **familiarity** aspect plays a lesser role. The following resources can be used to further weigh the options.

- [TodoMVC](http://todomvc.com/) (the same app implemented with different frameworks)
- [Technology radar](https://www.thoughtworks.com/radar/languages-and-frameworks) (shows how established and future-proof technologies are)
- [Framework benchmarks](http://www.stefankrause.net/wp/?p=191) (if you have scalability concerns)
- Some nice comparisons on Youtube: [here](https://www.youtube.com/watch?v=2rD_HuTuXfg) and [here](https://www.youtube.com/watch?v=6I_GwgoGm1w)

#### Browser support
The above frameworks support all modern, [evergreen browsers](http://eisenbergeffect.bluespire.com/evergreen-browsers/). Many frameworks and libraries that don't work in old browsers can be made to work through [polyfills](https://en.wikipedia.org/wiki/Polyfill), which come at a performance cost. If supporting old browsers (e.g. IE6) is a *must*, you need to do specific research and perhaps even choose obsolete technologies. 

The best way to go about it is avoid having to support old browsers. This sounds drastic but it's true. Old browsers are minefields of potential problems. You likely don't need IE6 support to be successful, and choosing to do it anyway will slow you down significantly. If at all possible, use [feature detection](https://en.wikipedia.org/wiki/Feature_detection_(web_development)) to implement a fallback page, telling the user their browser is not supported and how they can install a better one.

#### Alternatives to JavaScript
So far, we have not yet mentioned that Angular 2 uses [TypeScript](https://www.typescriptlang.org/), a typed precursor for JavaScript.  In fact, any of the above frameworks also work with TypeScript. It is definitely an option worth checking out if you have a significant amount of logic in the frontend. The generated JavaScript code is very readable, so you can always ditch it if you need to.

There are other alternative languages, such as [CoffeeScript](http://coffeescript.org/) and [ScalaJS](https://www.scala-js.org/). These are technologically mature, but do have smaller communities. Now that the major players are adopting TypeScript, CoffeeScript is losing popularity. ScalaJS is worth a look, but only really useful if your backend is also written in Scala.

#### Style sheets
Frameworks tend to stay clear of the visual presentation, and leave it up to [cascading style sheets](https://en.wikipedia.org/wiki/Cascading_Style_Sheets). For CSS, it is advisable to use a precursor like [SASS](http://sass-lang.com/) or [LESS](http://lesscss.org/) to enhance the readability and flexibility of style rules. Much like TypeScript, there is no real downside to using these precursors because the generated CSS can be used directly if the need ever arises.

The many do's and dont's of CSS are beyond the scope of this article. Look up some tutorials in general and take a close look at [flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/), it may save you some headaches.

#### A note on HTML5
HTML5 is the latest HTML standard. When people use the term, they often mean *rich client* which implies you are using a client-side MVC framework. When you are actually using HTML5 features, make sure you check the [compatibility list](http://caniuse.com/#search=html5) and you set the right *DOCTYPE*. That's all there is to it.

#### Package managers
Most frontend projects are packaged using [Node.js](https://nodejs.org/en/) and its package manager [npm](https://www.npmjs.com/). Build dependencies are managed in the file *package.json*.

Some like to use [bower](https://bower.io/) for dependency management, separating the build dependencies from the deployed dependencies. Note that [*npm* can do everything that bower can](https://www.quora.com/Why-use-Bower-when-there-is-npm), so save yourself the effort.

#### Build systems
Building and distributing a frontend app is usually done with tools like [gulp](http://gulpjs.com/), [grunt](http://gruntjs.com/) or [Webpack](https://webpack.github.io/). Gulp and Grunt allow the most customization, whereas webpack is the best all-in-one solution. Webpack also has the benefit of nice hot-reload features, which need to be configured by hand in gulp/grunt. Choose whichever works for you. 

#### Folder structure
Client-side frameworks often make the mistake of organizing folders based on file type. Folders named *scripts*, *styles*, *templates* are still a common sight. While it doesn't really hurt, it causes developers to have to jump around a lot in the project while working on one page. 

A better way to do it is to structure your code according to *features*. This has the added benefit that someone new to your project can relate code to the UI more easily. With the advent of *web components* (more on which later), frameworks are finally picking up this trend and putting files that are changed together in the same place. 

## Version control
Version control allows you to roll back code to a previous version, view changes and work with other developers in the same code base. If at all possible, use [git](https://git-scm.com/) for version control. The entire open source community is using it and its a gold standard at this point. It takes some learning on the developer's part, but that problem has been solved. Good [interactive tutorials](http://learngitbranching.js.org/) are available to teach it to people, and [Sourcetree](https://www.sourcetreeapp.com/) is a free client for those who prefer a UI over the command line. With proper build systems, you can avoid checking binaries and large files into version control. 

[Subversion](https://subversion.apache.org/) (SVN) is still a popular choice. While inferior to git in many ways, it still takes the crown as the easiest to understand and use. If you have non-technical stakeholders who absolutely need to use version control, consider using SVN. Then again, one might wonder why non-technical stakeholders need access to the source code history at all!

## Deployment infrastructure
Most of your deployment decisions depend on the scope and scale of your application. All we can do is provide some pointers.

- [Jenkins](https://jenkins.io/) is great for building and scheduling jobs. Version 2 has nice improvements in the scripting department.
- **Containers** (e.g. [Docker](https://www.docker.com/)) are great if you have to deal with a lot of server configuration.
- Hosted **cloud servers** are easier to deal with than dedicated hardware, but not always faster and cheaper. Make sure you to compare performance before commiting to one solution.