# Futurology

Looking at trends over the last couple of years, we can make some predictions about where the web is going.

### Other languages in the browser
Browser vendors are finally aligning their efforts to improve the standards behind JavaScript. Slowly, we are starting to see a more professional environment with modern language features and fewer quirks.

At the same time, there are also a few popular alternatives to JavaScript, like TypeScript and CoffeeScript. There is an inititiative for [asmjs](http://caniuse.com/#feat=asmjs), a high-performance subset of JavaScript used as a compilation target. In time, we can expect more and more languages that can compile to JS.

As for layout, HTML and CSS seem to be fairly static. Developments related to page layout mostly occur within individual frameworks, offering extra features such as data binding or a virtual DOM. In the style department, SASS seems to be king. Some work is being done to improve HTML and CSS, but no big shifts are happening there. 
 
### Web components
Many websites today reinvent the wheel while implementing UIs. They make their own form controls and widgets and embed them in their pages in a not-so-reusable fashion.

A trend in the latest web frameworks is the appearance of [web components](http://webcomponents.org/). Web components are small pieces of layout and behavior that can be reused across multiple pages. They provide a very [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) way to organize layout. A major selling point is that developers could share or sell their UI controls on online marketplaces. This in turn is a huge boon for drag-and-drop website creation tools.

Although the official standard is still a long way from being used in production, the idea has taken off and is already widely used in the newest generation of frameworks. React goes even further, because their version of web components *forces* you to make them reusable.

Further ahead, the [Polymer](https://www.polymer-project.org/1.0/) framework by Google showcases web components as described by the spec, using polyfills to implement the missing browser features. It is not established enough for projects in production, but it's a glimpse of things to come. 
