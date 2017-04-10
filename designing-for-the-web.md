# Designing for the web

The word is in. Someone has formulated a master plan to conquer the market. Their first step is to reach as many users as possible, for as small an effort as possible. They have chosen the most portable and most widespread platform in the world: the web.

Eager to start on a greenfield project, you accept a bag of money and get started. Here are the requirements:

The site should work in all browsers, including Safari, Opera and IE6.

It should work on all devices, including PCs, iPhones, Blackberries, smartwatches and this new VR headset on Kickstarter.
It should have a rich client with HTML5, form validation and UX.
It should have reusable a REST API on the server.
It should have a database with reliable backups and historic traceability.
It should be fast, completely secure and always available.
It should use microservices, continuous integration and this thing called Docker.
Full of energy, you get started.

## Project lifecycle
Like in every other software project, selecting the right web technologies starts with asking the right questions. Do you understand the problem? Is the proposed solution a good one? Which requirements are crucial, important, desirable or superfluous?

### Understand the problem

Quite often, companies make technological assumptions early in the project to come up with good cost/time estimations. That's normal. It definitely helps if you know what those assumptions were so you can gain insight from your technical point of view.

You could use the following checklist, and add questions of your own.

-   What was the problem that led to the decision of building a website?
-   Who are the users?
-   What do they need?
-   Who are the other stakeholders?
-   What exactly did they ask for?
-   Is a website indeed the right solution?
-   Is there no existing tool that can do what you need?
-   What is the cost and merit of the proposal?

If you raise any doubt with these questions, don't skip over them. Use the [5 Whys] or similar techniques. You want to build something that lasts, and to do that you need to figure out what is important, and what is not. Which brings us to the process.

  [5 Whys]: https://en.wikipedia.org/wiki/5_Whys

### Choose a development process

If there is no process in place yet, great! You can create one. The goal of a process is to coordinate the team, track the progress towards your goal and to minimize risk.

You probably want to choose some sort of [Agile] framework like [Scrum] or [Kanban]. Decide which one is best for you. Although [Waterfall] is often frowned upon, it can be the best approach if applied correctly. More important than the framework is a correct approach. You may be a faster and more agile coder than anyone else, but if you're going in a random direction that's not very helpful.

Many greenfield projects start off with a small budget and have to prove their value. If they can't, the project gets cancelled. Each project functions like a start-up, and the unfortunate truth is that [90% of startups fail]. By far the biggest cause of failure is a lack of [product-market fit]. No matter how much effort went into the business case, you only really know it's good when the users come in, stay in, and start generating value. I find that this applies to almost every business application in existence. To obtain added value as soon as possible, consider the following development phases.

1.  Conceptualization
2.  Prototype
3.  Minimal viable product (MVP)
4.  Iterative growth

The rationale is as follows. Conceptualization means understanding a problem and its proposed solution. You should also look for any competing products. Launching alternatives to existing products is risky. If you do, make sure you do at least one thing [10x better] than anybody else.

A prototype is a hacky, ugly, barely-there version of the software. The purpose of a prototype is to validate the core business case with real users. A prototype can be made with pen and paper, wireframing tools, or actual code. If you choose code, you should write it as fast as possible, without maintenance or performance in mind. That way, it can be built many times faster than a production-ready MVP.

Prototypes are meant to be discarded after they serve their purpose. It was not built with maintenance in mind, and those who tried building an MVP on top of a prototype will tell you it was a nightmare. Keep in mind that the real value of the prototype was to validate the business case and to gain information, not to develop the product. If you have any doubt that the prototype will be discarded, don't make one and skip to the MVP.

The MVP is a properly designed and fully implemented solution. It should have at least one feature that solves a problem for a real user, making it viable. If there is any feature that you could omit without destroying the viability, you should. A minimal product is easier, faster and cheaper to build, allows an early launch and enables more input from real users.

After the MVP, the groundwork is done and the stage is set. The product is ready for iterative growth. Conceptualize new features, judge their added value, build the features and validate them against real users. Try to formulate objective metrics to determine whether or not a feature has merit. If it does not, be ruthless and remove them from the product. After all, they have a maintenance cost but bring no added value.

  [Agile]: https://en.wikipedia.org/wiki/Agile_software_development
  [Scrum]: https://en.wikipedia.org/wiki/Scrum_(software_development)
  [Kanban]: https://en.wikipedia.org/wiki/Kanban_(development)
  [Waterfall]: https://en.wikipedia.org/wiki/Waterfall_model
  [90% of startups fail]: http://fortune.com/2014/09/25/why-startups-fail-according-to-their-founders/
  [product-market fit]: https://en.wikipedia.org/wiki/Product/market_fit
  [10x better]: http://erickimphotography.com/blog/2014/12/29/the-10x-principle-the-only-difference-between-success-and-failure-as-a-photographer/

### Analyze the requirements

Now that you know what you are building, it's time to take another look at the requirements. Start with an empty page and write down those things that actually apply to your product. All the requirements above should automatically translate into meaningful trade-offs. Since it's rather hard to generalize, here are some examples:

-   Are the users technically capable to update their browsers? If not, support IE6 but consider dropping the rich client. If so, limit yourself to evergreen browsers, use feature detection and show a friendly notice if the user is too far behind the curve.
-   Will you go bankrupt if the website is hacked? Yes: hire a security expert for advice.
-   Will people die if the website goes down? No: 99% uptime is probably good enough. Perhaps you can tolerate additional downtime at night.

Technological choices are a means to an end. When a customer asks for an HTML5 application, they mean an interactive web application. You can use HTML5 features to achieve that goal, but it's not mandatory. Other technical terms like REST and microservices should also be left out of the requirements, unless the users include software engineers and systems administrators.

## Product architecture
Once you reach the MVP phase, your decisions affect the long-term value and maintainability of the product. This is where you need sustainable technology choices - but sustainable web technologies are hard to find! This is where a “design for change” mentality will prove its worth.

> A good architecture maximizes the number of decisions not made. - Robert "Uncle Bob" Martin

> To make decisions revocable you need to design for flexibility. - Martin Fowler

It sounds counter-intuitive. Isn't the job of an architect to make decisions and get them right the first time? Wouldn't no architecture be the best architecture?

The point is that no matter how good you are, you *will* get it wrong some of the time and some requirements *will* change. The goal is not to prevent architectural changes but to make them as easy as possible. That is why I argue against big, all-inclusive technology stacks. If you gather your tools yourself, you have more freedom to change direction when needed. Focus on the decisions you need to make now, those that cannot sensibly be delayed.

### Anatomy of a web application
Almost every web application has a backend and a frontend. The backend is a server that provides data and (optionally) views to the frontend. The frontend renders these views in a browser.

The view typically consists of HTML for layout, CSS for presentation and JS for behavior. There are exceptions. In fact, there are so many alternatives that it warrants a section in and of itself. At the system level, it is sufficient to remember that the browser receives a view from the server and somehow renders it into a web page.

In a static web application, data is embedded in the view by the server and fully rendered to HTML before it is sent to the client. Each time you want new data, you refresh the page. Very little client-side scripting is necessary to display the page. Static web pages are good in scenarios where the browser is slow or the data doesn't change much. An example of this is your yearly tax report. That said, most use cases for a static website can also be implemented dynamically, which offers several advantages.

Dynamic web applications send the view and data to the client separately. The browser combines the two with scripting and generates the complete HTML. While this requires slightly more processing on the client side, it has many advantages:

-   Reduced server load thanks to client-side rendering
-   Separation of data and presentation
-   The same data can be used in multiple views
-   The browser does not need to refresh when requesting/submitting data
-   Requests are smaller and faster

The choice between static and dynamic web pages may rule out certain technologies. It is therefore a choice that you should make consciously. Today, dynamic web pages are the gold standard. Nearly all modern technologies are aimed at dynamic content and their communities are much larger. You need a really good reason to choose a static application. If you have an example of such a reason, please put it here!

### Monolith vs Microservices
This decision affects technology choices as well as the integration and release cycle. Some people consider microservices the only way forward, but [monoliths are simpler as long as you can manage the complexity]. An MVP is generally not complex enough to warrant a microservices architecture by itself. The question is: will you need one later? Most likely, you just don't know.

An alternative is to [start with a monolith and expand it to a microservices architecture later]. When complexity becomes a problem, you can gradually split off services from the monolith and rewrite them as microservices. As long as the monolith was designed with stateless behavior in mind, a HTTP proxy can redirect relevant traffic to the new microservice. Users can remain completely unaware of the change. Over time, the monolith shrinks and the microservices take over.

  [monoliths are simpler as long as you can manage the complexity]: https://martinfowler.com/bliki/MicroservicePremium.html
  [start with a monolith and expand it to a microservices architecture later]: https://martinfowler.com/bliki/MonolithFirst.html

### Backend frameworks
The backend serves your web application and has several responsibilities. The first is your business logic. Second, an API that clients use to fetch data and/or views. In addition, the backend typically needs access to a persistent data store. The first thing to think about is how you want to divide these responsibilities.

In an ideal world, you separate the application core (business logic and data models) from the rest so that it is completely independent. Have a look at the [onion architecture]. The onion model allows you to change your API and persistence modules without touching the core. In reality however, most web frameworks make it difficult to do this. Java's Spring framework provides dependency injection and database bindings that are intended to be used throughout your entire application. As a result, most web backends have a core that strongly depends on the framework. If you want to avoid that, you have to move away from everything-in-a-box style frameworks and look at less invasive options, e.g. Jersey or Dropwizard.

With your desired structure in mind, you then select a language and a framework. Nearly all modern languages have a few battle-tested web frameworks to choose from, and there are many benchmarks and opinions on which is the best. The bottom line is that unless you have very, very strict demands on scalability or response time, all of the popular frameworks can be considered good enough.

So how do you choose between all the options? Three criteria. Choose something that is modern, established and familiar to the developers.

**Modern** technologies are easier to work with than dated alternatives, especially with the changing nature of the web. Avoid being overly conservative. Going with C++ can easily double your development and maintenance effort, because the available web frameworks are sub-par and too much detail is exposed through the interfaces. The bottlenecks of a web application are nearly always transfer speed (HTTP) and disk IO (database), to the point where the language is hardly even a factor. Instead, aim for something high level like C\#, Java, Scala, Python or Node.js. Free and open source technologies have the benefit of larger communities. Closed technologies tend to have the edge when it comes to enterprise-level support.

Choose a framework that is well **established**. A production-ready app requires a production-ready framework. Look for the following signs:

-   At least version 1.0 (according to [semantic versioning])
-   Used by at least two well-known companies
-   Backed by a company (no single-developer projects)
-   Upwards or stable history in [Google Trends]
-   At least one [benchmark] comparing it to other frameworks
-   Good [presence] on GitHub and StackOverflow

Finally, choose whatever is the most '''familiar'

  [onion architecture]: http://lorifpeterson.com/?p=64
  [semantic versioning]: http://semver.org/
  [Google Trends]: https://www.google.com/trends/
  [benchmark]: https://www.techempower.com/benchmarks/
  [presence]: http://redmonk.com/sogrady/2017/03/17/language-rankings-1-17/

### Data exchange
On the web, clients talk to the server by sending HTTP requests to URLs. URLs conform to a certain architectural style. Requests and responses may contain data in some data format.

The most common architectural style is [REST], which uses the path section of URLs to access named resources through a stateless interface. Some standards for REST are defined in the [Open API Specification]. This specification recommends [Swagger], a tool that can generate interactive documentation, client and server code from an API description.

If REST does not suffice, other options are [SOAP] and [WebSocket]. One example where REST is not ideal is controlling physical machinery where the server is inherently stateful. Modeling state transitions (which are generally verbs) on top of REST can be cumbersome; RPC-style websockets are much more convenient in that situation.

You can also choose a data format. Since the client is generally written in JavaScript, [JSON] is most common and easiest format to deal with. For certain types of data, you might choose plain text. XML also has a [great past], but has been losing traction due to its verbosity and parsing ambiguities (sequences vs plain text nodes, empty nodes). It's still quite popular in enterprises for legacy reasons.

For both XML and JSON, there are schema specification formats which describe the data model. These models specify e.g. which parameters are required and which are optional, minimal and maximal values, etc. These specifications can be really useful for code generation when multiple parties produce and consume the same messages.

Data exchange can be mixed and matched if necessary. It is not a critical choice by itself, but some languages and frameworks have better support for certain styles and data formats. Choosing a specific format might influence your decisions later on.

  [REST]: https://en.wikipedia.org/wiki/Representational_state_transfer
  [Open API Specification]: https://github.com/OAI/OpenAPI-Specification
  [Swagger]: http://swagger.io/
  [SOAP]: https://en.wikipedia.org/wiki/SOAP
  [WebSocket]: https://en.wikipedia.org/wiki/WebSocket
  [JSON]: http://www.json.org/
  [great past]: https://www.google.com/trends/explore?date=all&q=json,xml

### Data storage
At some point your application likely needs to persist its data. Here are your options.

-   SQL database
-   NoSQL database
-   Filesystem

Obviously, the file system is typically used for files that are already in an external file format, such as documents, binaries, images. Databases are used to store metadata and customized user input.

For SQL, the most versatile and expressive modern database is [PostgreSQL]. Postgres is open soruce, has more features and offers better performance than its competitors. You need a good reason to choose any other SQL database at this point. As a bonus, it also supports JSON columns and sharding across multiple database servers, which allows shifting to a more NoSQL approach within SQL.

There are benchmarks ([here] and [here][1]) showing that the modern variety of SQL is faster than the currently popular NoSQL databases. SQL also has a habit of being easier to manage thanks to the fixed schema. Just like programming languages, dynamic databases are faster to set up but statically typed databases are safer and easier to maintain. As it stands, there are only a few reasons to choose a NoSQL database:

1.  Your data is inherently unstructured
2.  Your data is more about storing individual things than the relations between the things
3.  Your queries are highly graph-centered and can't be performed efficiently in SQL
4.  You are making a small, pure-Javascript application: JSON is easier to deal with than ORMs
5.  You need to scale to many, many servers and cannot do that with SQL

The rule of thumb is that usually, either choice will work. But it's much easier to pick NoSQL for the wrong reasons, than it is to pick PostgreSQL for the wrong reasons.

  [PostgreSQL]: https://www.postgresql.org/
  [here]: https://www.arangodb.com/2015/10/benchmark-postgresql-mongodb-arangodb/
  [1]: https://www.enterprisedb.com/postgres-plus-edb-blog/marc-linster/postgres-outperforms-mongodb-and-ushers-new-developer-reality

### Frontend frameworks
The state of frontend JavaScript frameworks has been subject to a lot of ridicule over the past few years. Among the critiques are the articles on [JavaScript Fatigue], [this website] and a [JavaScript drinking game].

The community is also an excellent source of mildly suppressed irritation.

```
There are no best practices. There's just different clumps of tech that other people have settled on using.
```

```
You are in the room of web apps.
make web app
You need to select a platform first to make a web app. You see doors named Unity, GameMaker, NW.js, Electron, Cordova, and Browser.
make web app --browser
Some languages appear. You see Javascript, Coffescript, Typescript, Clojurescript, Dart, asm.js. Type “more” if you want the list of all the 127 available languages
make web app --browser --javascript
Do you mean ES5 or ES6?
make web app --browser --javascript-es6
Welcome to the room of transpilers. You see Babel, Traceur or you can hope that the browser already supports the features that you’ll use. Type “more” for a list of transpilers and read the book “Transpiler Tools aka Necronomicon”
make web app --browser --javascript-es6 --babel
You arrive in the corridor of Tasks. You see a Grunt in a corner, a Gulp in the other. A Babelify attacks you, Webpacks gather all around. In a nearby room you hear Browserify screaming and fighting with Require.js. In your inventory you have “transpile on save”.
exit
You can’t exit because seven rooms ago you chose “npm install node-jsx” and it is not currently compatible with the latest implementation of exit.
Ctrl + C
A Yeoman glows in an alcove nearby. In your hand you have npm but your project.json is broken. On the floor you also see Gruntfile, .jshintrc, .babelrc and tsconfig.json. You hear a Broccoli and a Jasmine howling in the distance.
rm -rf /
```

  [JavaScript Fatigue]: https://medium.com/@ericclemmons/javascript-fatigue-48d4011b6fc4#.79383u2f9
  [this website]: http://www.isaacchansky.me/days-since-last-new-js-framework/
  [JavaScript drinking game]: https://twitter.com/ironshay/status/370525864523743232

#### State-of-the-art

It's not all bad news. As of 2017, client-side web frameworks are volatile, but stabilizing. In theory you have hundreds of options, but only a few of them are sufficiently modern and established.

-   [Angular 2]
-   [EmberJS]
-   [Aurelia]
-   [React] + [starter kit]

Both Angular 2 and Ember take the everything-in-a-box approach and dictate the way you write your application. They use their own style of templates and controllers. Angular 2 has less boilerplate as it makes more decisions for you.

Aurelia takes an approach similar to Angular 2, but has a more hands-off approach. It lets you write all aspects of the MVC in regular standards-compliant code. This has a great benfit in that you don't need to learn much when using this framework. The drawback is that the framework is new and while there are plenty of support options, the company behind it is less established.

React takes a minimalist approach which is very clean and easy to learn. On the flipside, React is not a complete framework so it requires additional choices and library management. There are several starter kits available that make these choices for you. If you use react, make sure you do so with legal scrutiny. React has a [patent clause] that poses restrictions on its usage. If you work for a large company, they may disqualify it for that reason.

Note that AngularJS is absent from this list. It has been replaced by Angular 2 and is effectively obsolete. Even though it is well established, choosing it means setting yourself up for a big migration in the not-too-distant future.

#### Comparisons

Since all modern frontend frameworks share Javascript as their target language, the familiarity aspect plays a less important role compared to backend frameworks. The following resources can be used to further weigh the options.

-   [TodoMVC] (the same app implemented with different frameworks)
-   [State of JS] (various categories, based on large scale developer surveys)
-   [Technology radar] (shows how established and future-proof technologies are)
-   [Framework benchmarks] (if you have scalability concerns)
-   [Additional benchmarks]
-   Some nice comparisons on Youtube: [here] and [here][1]

  [Angular 2]: http://learnangular2.com/
  [EmberJS]: http://emberjs.com/
  [Aurelia]: http://aurelia.io/
  [React]: https://facebook.github.io/react/tutorial/tutorial.html
  [starter kit]: https://github.com/kriasoft/react-starter-kit
  [patent clause]: https://news.ycombinator.com/item?id=11270213
  [TodoMVC]: http://todomvc.com/
  [State of JS]: http://stateofjs.com/2016/introduction/
  [Technology radar]: https://www.thoughtworks.com/radar/languages-and-frameworks
  [Framework benchmarks]: http://www.stefankrause.net/wp/?p=191
  [Additional benchmarks]: https://auth0.com/blog/more-benchmarks-virtual-dom-vs-angular-12-vs-mithril-js-vs-the-rest/
  [here]: https://www.youtube.com/watch?v=2rD_HuTuXfg
  [1]: https://www.youtube.com/watch?v=6I_GwgoGm1w

#### Browser support

The above frameworks support all modern, [evergreen browsers]. Many frameworks and libraries that don't work in old browsers can be made to work through [polyfills], which come at a performance cost. If supporting old browsers (e.g. IE6) is a must, you need to do specific research and perhaps even choose obsolete technologies.

For information on browser features, I recommend [caniuse.com].

The best way to go about it is avoid having to support old browsers. This sounds drastic but it's true. Old browsers are minefields of potential problems. You likely don't need IE6 support to be successful. If at all possible, use [feature detection] to implement a fallback page, telling the user their browser is not supported and how they can install a better one.

#### Alternatives to JavaScript

So far, we have not yet mentioned that Angular 2 uses TypeScript, a typed precursor for JavaScript. In fact, any of the above frameworks also work with [TypeScript]. It is definitely an option worth checking out if you have a significant amount of logic in the frontend. The generated JavaScript code is very readable, so you can always ditch it if you need to.

There are other alternative languages, such as [CoffeeScript] and [ScalaJS]. These are technologically mature, but do have smaller communities. Now that the major players are adopting TypeScript, CoffeeScript is losing popularity. ScalaJS is worth a look, but only really useful if your backend is also written in Scala.

#### Style sheets

Visual details such as margins, colors and fonts are written in [cascading style sheets]. For CSS, it is advisable to use a precursor like [SASS] or [LESS] to enhance the readability and flexibility of style rules. Much like TypeScript, there is no real downside to using these precursors because the generated CSS can be used directly if the need ever arises.

You may also benefit from a theme such as [Bootstrap], [Material Design] or [Material Design Lite]. They provide a sane, consistent layout for building your app.

The many do's and don'ts of CSS are beyond the scope of this article. One piece of advice: use [flexbox], it will save you some headaches.

#### HTML5

Similar to the term “Web 2.0”, people often use “HTML5” as a buzzword to describe an interactive client, built with a modern frontend framework.

The truth is, HTML5 is just the latest HTML standard. Essentially, it's a bag of convenience methods to simplify layouts. The most powerful new feature is the canvas element. If you are using HTML5 features, make sure you check the [compatibility list] and set the right DOCTYPE. That's all there is to it.

#### Testing

How you write unit tests, depends on which framework you are using. Look for the relevant documentation elsewhere. 

For end-to-end tests, there is a library called [Selenium]. It is a fair amount of work to get it up and running, but it works excellently for use case tests. For Unix machines, use Chrome with [Xvfb] in favor of [PhantomJs], which is known to cause compatibility problems.

An honorable metion is [Cucumber.js], which can help for readability and use-case documentation. 

  [Selenium]: https://en.wikipedia.org/wiki/Selenium_(software)
  [Cucumber.js]: https://github.com/cucumber/cucumber-js
  [Xvfb]: http://elementalselenium.com/tips/38-headless
  [PhantomJs]: http://phantomjs.org/

#### Package managers

Most frontend projects are packaged using [Node.js] and its package manager [npm]. Build dependencies are managed in the file package.json. Some like to use [bower] for dependency management, separating the build dependencies from the deployed dependencies. Note that [npm can do everything that bower can], so save yourself the effort.

In the area of new contenders, [yarn] has been gaining popularity lately. I haven't worked with it yet - if you know more about it, please share your experiences!

#### Build systems

Building and distributing a frontend app is usually done with tools like [gulp], [grunt] or [Webpack]. Gulp and Grunt allow the most customization, whereas webpack is the best all-in-one solution. Webpack also has the benefit of nice hot-reload features, which need to be configured by hand in gulp/grunt. Choose whichever works for you.

#### Folder structure

Client-side frameworks often make the mistake of organizing folders based on file type. Folders named scripts, styles, templates are still a common sight. While it doesn't really hurt, it causes developers to have to jump around a lot in the project while working on one page. A better way to do it is to structure your code according to features. This has the added benefit that someone new to your project can relate code to the UI more easily. With the advent of web components (see Futurology), frameworks are finally picking up this trend and putting related files together in the same place.

  [evergreen browsers]: http://eisenbergeffect.bluespire.com/evergreen-browsers/
  [polyfills]: https://en.wikipedia.org/wiki/Polyfill
  [caniuse.com]: http://caniuse.com/#feat=flexbox
  [feature detection]: https://en.wikipedia.org/wiki/Feature_detection_(web_development)
  [TypeScript]: https://www.typescriptlang.org/
  [CoffeeScript]: http://coffeescript.org/
  [ScalaJS]: https://www.scala-js.org/
  [cascading style sheets]: https://en.wikipedia.org/wiki/Cascading_Style_Sheets
  [SASS]: http://sass-lang.com/
  [LESS]: http://lesscss.org/
  [Bootstrap]: https://v4-alpha.getbootstrap.com/
  [Material Design]: https://material.io/guidelines/
  [Material Design Lite]: https://getmdl.io/
  [flexbox]: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
  [compatibility list]: http://caniuse.com/#search=html5
  [Node.js]: https://nodejs.org/en/
  [npm]: https://www.npmjs.com/
  [bower]: https://bower.io/
  [npm can do everything that bower can]: https://www.quora.com/Why-use-Bower-when-there-is-npm
  [yarn]: https://yarnpkg.com/en/
  [gulp]: http://gulpjs.com/
  [grunt]: http://gruntjs.com/
  [Webpack]: https://webpack.github.io/

### Deployment infrastructure
Most of your deployment decisions depend on the scope and scale of your application. All we can do is provide some pointers.

-   [Jenkins] is great for building and scheduling jobs. Version 2 has nice improvements in the scripting department.
-   Containers (e.g. [Docker]) are great if you have to deal with a lot of server configuration.
-   Hosted cloud servers are easier to deal with than dedicated hardware, but not always faster and cheaper. Make sure you to compare performance before commiting to one solution. Some options are Azure, Cloud Foundation and Amazon Web Services.
-   In the category “other things to think about”, [12factor] has a nice methodology for deploying and distributing web projects.

  [Jenkins]: https://jenkins.io/
  [Docker]: https://www.docker.com/
  [12factor]: https://12factor.net/

### Version control
Version control allows you to roll back code to a previous version, view changes and work with other developers in the same code base. If at all possible, use [git] for version control. The entire open source community is using it and its a gold standard at this point. It takes some learning on the developer's part, but that problem has been solved. Good [interactive tutorials] are available to teach it to people, and [Sourcetree] is a free client for those who prefer a UI over the command line. With proper package managers and [.gitignore] files, you can avoid checking large files into version control.

[Subversion (SVN)] is still a popular choice. While inferior to git in many ways, it still takes the crown as the easiest to understand and use. If you have non-technical stakeholders who absolutely need to use version control, consider using SVN. Then again, one might wonder why non-technical stakeholders need access to the source code history at all!

  [git]: https://git-scm.com/
  [interactive tutorials]: http://learngitbranching.js.org/
  [Sourcetree]: https://www.sourcetreeapp.com/
  [.gitignore]: https://github.com/github/gitignore
  [Subversion (SVN)]: https://subversion.apache.org/

### Documentation

Documentation is a guide for other people, who want to understand your code and write some themselves. Ideally, you want as little documentation as possible to sufficiently answer the why-question. If you can avoid writing documentation by cleaning up your code, do it! Good naming conventions can often [replace comments entirely]. The same goes for docstrings. Generated documentation can help for external interfaces, e.g. [Swagger] APIs. Unit tests can provide examples for internal APIs; end-to-end tests with [Cucumber.js] can help reduce the need for separate business requirements.

Good commit messages can help keep track of changes. Make sure you add a link to an issue tracker such as [Jira] or [Trello]. The issue tracker can provide further information about the intent of your change.

Even when the code quality is excellent and your tickets are perfectly written, there is still some information you want to store separately. For example, your workflow, responsibilities, contact persons, architecture and design decisions. If you are rigorous about this, it will lighten the mental load for developers and simultaneously solve problems when a key person is unavailable. 

To store documentation, people tend to use separate Office documents or a wiki. The downside of Office documents is that they do not work well with version control. They are also hard to search through once you get a number of them, often leading to duplicate, conflicting and out-of-date information. Wikis work better because their pages can point to each other. Each page can stay small and self-contained, which makes them much easier to update. Wikis also have search engines that allow you to search for an existing page before writing a new one. [MediaWiki] and [Confluence] are popular choices for wikis.

Sometimes, customers or end users want additional documentation in the form of user manuals. This may be a sign that your application's user experience can be improved. Perhaps the UI is not clear enough, or you can add a webpage with instructions. Writing a separate manual may help, but it is a lot of work to update and distribute.

  [replace comments entirely]: http://blog.pragmaticengineer.com/a-comment-is-an-invitation-for-refactoring/
  [MediaWiki]: https://www.mediawiki.org/wiki/MediaWiki
  [Confluence]: https://www.atlassian.com/software/confluence
  [Jira]: https://www.atlassian.com/software/jira
  [Trello]: https://trello.com/

## Implementation

You have made the necessary architectural choices and are now ready for the next phase: installing and configuring all the tools, designing the features and implementing the solution.

This guide can't hold your hand forever. If you have any question about web technologies, chances are someone has already posted them on StackOverflow. In fact, even if you know the answer, it's still good to go there and see what other people think. The web is a moving target, and you do yourself a disservice by assuming you already know the answer!
