# Futurology

Looking at trends over the last couple of years, we can make some predictions about where the web is going.

## Web components

Most companies today are reinventing the wheel every time they make a new web UI. They roll their own form controls, widgets and layout, embedding them in their pages in a non-reusable fashion. A recent trend is the appearance of [web components]. Web components are small pieces of layout and behavior that can be reused across multiple pages. For example: a [datepicker].

Components provide a very [DRY] way to organize the UI. Once this method becomes a standard, developers could share or even sell their UI controls on online marketplaces. This is a huge benefit for developers as well as drag-and-drop website creation tools.

Although the official standard is still a long way from being used in production, the idea has taken off and is already widely used in the newest generation of frameworks. React for example makes it obligatory to split a page into reusable components. The [Polymer] framework by Google showcases web components as described by the spec, using polyfills to implement the missing browser features. It is not yet suitable for production in my opinion, but it’s a glimpse of things to come.

## Other languages in the browser

Traditionally, people tried to solve limitations in JavaScript by inventing “precursor” languages like TypeScript and CoffeeScript. Precursors always have to be compiled to plain JavaScript, which limits the flexibility of the source language. Browser vendors are about to make this easier with the introduction of [Web Assembly], a high-performance assembly language that can run in the browser.

In time, we can expect languages other than JavaScript to compile to Web Assembly. This will launch a new wave of web frameworks that run the same language in the frontend and backend. Currently, this is only really being done with JavaScript and Node.JS, but soon you might be able to run a full web stack in Python. For typed languages like C\# and Java, existing JavaScript libraries (also compiled to web assembly) likely need to be imported dynamically or hidden behind a typed interface. TypeScript already does this (search for *@types* or *typings*), so we can expect others to follow suit.

On the topic of layout, HTML and CSS seem to be going nowhere soon. Improvements in HTML occur mostly within individual frameworks: they offer extra features such as data binding or a virtual DOM, and generate the resulting HTML on the fly. In the style department, SASS seems to be king as the go-to precursor for CSS.

## Web goes mobile

If you have a website and you need an app, there are several options: write native apps, use Xamarin to cover all platforms, or use a web-to-mobile framework. These frameworks can embed your website in an app, and allow you to access native functionality such as the accelerometer and the phone's contacts. Examples are Cordova, React Native, Ionic and Meteor. Using web technologies on phones is a relatively new thing. As the author, I have not yet tried any of these frameworks and I cannot offer any reliable recommendations. If you can, please do! :-)

  [web components]: http://webcomponents.org/
  [datepicker]: https://github.com/christopheclc/polymer-date-picker
  [DRY]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
  [Polymer]: https://www.polymer-project.org/1.0/
  [Web Assembly]: http://webassembly.org/