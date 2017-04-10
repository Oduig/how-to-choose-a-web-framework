# Untangling the Web

*A quickstart guide to making well-founded design choices for web applications.*

- Documentation
- Links

## Motivation

The first public website went online in 1991 at CERN, Switzerland. Since then, the web has come a long way. What used to be a platform for academic information, is now so wide-spread that it has effectively replaced paper.

Traditionally, a website was a place to share and publish static information. You could go there and read it, but it did not do anything. Browser vendors were companies that mostly did their own thing, and offered a platform that worked only for simple use cases. This changed around 2004, when Web 2.0 movement started. Browser vendors and the open source community began creating tools like JQuery, which supported interactive content. The result was social media and all kinds of other collaborative web apps.

While the web was an application platform at that point, there were some things left to be desired. The three languages of the web: HTML, CSS and JavaScript, were clumsy to work with and standards were lacking. It was very hard to do large-scale, professional applications well. In the early 2010s, that changed with the release of Node.JS and AngularJS. Finally, JavaScript had an ecosystem and applications could be developed in a structured way. This made the web a contender to replace desktop and mobile applications entirely.

Today, browsers are updated regularly, differences between vendors are disappearing and our tools are getting more numerous and powerful. Scarcity has turned into abundance: create a new web application in 2017, and you are faced with an uncomfortable number of technological choices. Best practices are nowhere to be found. This guide attempts to fill that gap, telling you how to narrow down your options and how to make choices that will last... as long as possible. 

## Scope

The scope of this guide is limited to custom-built web applications. If you just want a page for your local book club, you are probably better off using a website builder or blogging platform like Wordpress. The assumption is that your website is special and needs to be built by software engineers. You are one of those software engineers. You already know the basic building blocks of the web, and seek help with the alarming number of choices you face. You want technologies that get out of your way and let you focus on delivering business value to yourself or your customers.

This is an opinionated guide. It tells you what options there are, which options are good defaults, and how you can make an informed choice for your particular case. Most existing comparisons between web technologies are narrowly focused on one or two web technologies. In order to make an informed decision, you need to look at many different comparisons and combine their results. In a way, this guide does exactly that. It is a systematic review of other people's work.

The truth is, the web is a moving platform. You can be almost guaranteed that some of your choices will be obsolete in 5 years. The upside is that if you read all of this, you'll know why you made your decision and you'll have already thought about your other options. 

## Table of contents

1. [Designing for the web](./designing-for-the-web.md)
	1. [Project lifecycle](./designing-for-the-web.md#project-lifecycle)
		1. [Understand the problem](./designing-for-the-web.md#understand-the-problem)
		1. [Choose a development process](./designing-for-the-web.md#choose-a-development-process)
		1. [Analyze the requirements](./designing-for-the-web.md#analyze-the-requirements)
	2. [Product architecture](./designing-for-the-web.md#product-architecture)
		1. [Anatomy of a web application](./designing-for-the-web.md#anatomy-of-a-web-application)
		2. [Monolith vs Microservices](./designing-for-the-web.md#monolith-vs-microservices)
		3. [Backend frameworks](./designing-for-the-web.md#backend-frameworks)
		4. [Data exchange](./designing-for-the-web.md#data-exchange)
		5. [Data storage](./designing-for-the-web.md#data-storage)
		6. [Frontend frameworks](./designing-for-the-web.md#frontend-frameworks)
			1. [State-of-the-art](./designing-for-the-web.md#state-of-the-art)
			2. [Comparisons](./designing-for-the-web.md#comparisons)
			3. [Browser support](./designing-for-the-web.md#browser-support)
			4. [Alternatives to JavaScript](./designing-for-the-web.md#alternatives-to-javascript)
			5. [Style sheets](./designing-for-the-web.md#style-sheets)
			6. [HTML5](./designing-for-the-web.md#html5)
			7. [Package managers](./designing-for-the-web.md#package-managers)
			8. [Build systems](./designing-for-the-web.md#build-systems)
			9. [Folder structure](./designing-for-the-web.md#folder-structure)
		7. [Deployment infrastructure](./designing-for-the-web.md#deployment-infrastructure)
		8. [Version control](./designing-for-the-web.md#version-control)
		9. [Documentation](./designing-for-the-web.md#documentation)
	3. [Implementation](./designing-for-the-web.md#implementation)
2. [Courses](./courses.md)
3. [Futurology](./futurology.md)

## Contributing
It's impossible for one person to be an expert on *all* web-related topics. I encourage you to share different views. Feel free to submit pull requests for additions, clarifications, grammar fixes or any sort of change in general that you think would improve the text. If this resonates with a lot of people,
we might even tackle the biggest challenge of them all: keeping a guide on web technology up to date.


## Contact
I am Guido Josquin, a full-stack web engineer at a software consultancy bureau in Eindhoven, The Netherlands. Lately, we see more and more customers asking for experience in web technology and we wanted to expand our knowledge in the area. We hope to use this article as a framework (pun intended) for future web projects and new developers.

Feel free to contact me via GitHub or LinkedIn. 
