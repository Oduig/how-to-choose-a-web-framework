# How to choose your web technologies

The word is in. Someone has formulated a master plan to conquer the market.
Their first step is to reach as many users as possible,
for as small an effort as possible. They have chosen the most portable and
most widespread platform in the world: *the web*.

Eager to start on a greenfield project, you accept a bag of money and get started.
Here are the requirements:

- The site should work in **all browsers**, including Safari, Opera and IE6.
- It should work on **all devices**, including PCs, iPhones,
  Blackberries, smartwatches and this new VR headset on Kickstarter.
- It should have a **rich client** with **HTML5**, **form validation** and **UX**.
- It should have reusable a **REST API** on the server.
- It should have a database with reliable **backups** and **historic** traceability.
- It should be **fast**, completely **secure** and always **available**.
- It should use **microservices**, **continuous integration** and this thing called **Docker**.

Full of energy, you get started.

## Introduction

This is an opinionated guide on *how to choose your web technologies*. 

The **added value** of this guide is that it does not tell you *what* to choose, it tells you *how* to choose. Most existing comparisons between web technologies are narrowly focused and biased. In order to make an informed decision, you need to look at many of them and combine their results into a reliable conclusion. In a way, this guide is the modern equivalent of a [systematic review](https://en.wikipedia.org/wiki/Systematic_review).

The truth is, the web is a moving platform. You can be almost guaranteed that some of your choices will be obsolete in 5 years. The upside is that if you read all of this, you'll know why you made your decision and you'll have already thought about your migration options.

The **scope** is limited to websites where many of the above concerns are applicable.
If you just want a page for your local book club, you are probably better off using a website builder or blogging platform like Wordpress. The assumption is that your website is special and needs to be custom-built by real
software engineers. You are one of those software engineers. You already know the basic building blocks of the web, and seek help with the alarming number of choices you face before you can deliver your first feature.


## Table of contents

1. [Before you start](./analysis.md)
	1. [Understand the problem](./analysis.md#understand-the-problem)
	2. [Choose a process](./analysis.md#choose-a-process)
	3. [Analyze the requirements](./analysis.md#analyze-the-requirements)
3. [Architecture](./architecture.md)
	1. [Anatomy of a web application](./architecture.md#anatomy-of-a-web-application)
	2. [Data exchange](./architecture.md#data-exchange)
	3. [Monolith vs microservices](./architecture.md#monolith-vs-microservices)
	4. [Backend](./architecture.md#backend)
	5. [Data storage](./architecture.md#data-storage)
	6. [Frontend](./architecture.md#frontend)
	7. [Version control](./architecture.md#version-control)
	7. [Deployment infrastructure](./architecture.md#deployment-infrastructure)
4. [Design and implementation](./design-and-implementation.md)
5. [Education](./education.md)
6. [Futurology](./futurology.md)


## About
I am a full-stack web engineer at a software consultancy bureau in Eindhoven, The Netherlands. Lately, we see more and more customers asking for experience in web technology and we wanted to expand our knowledge in the area. We hope to use this article as a framework (pun intended) for future web projects and new developers.

Feel free to contact me via GitHub, LinkedIn or find me in the [Slack Slashrocket community](https://slashrocket.slack.com/messages/general/) under the name *jodiug*. 

#### Contributing
I am just one voice in a very big crowd, and I cannot be an expert on *all* of the discussed topics. I encourage you to share different views. Feel free to submit pull requests for additions, clarifications, grammar fixes or any sort of change in general that you think would improve the text. If this resonates with a lot of people,
we might even tackle the biggest challenge of them all: keeping a guide on web technology up to date.
