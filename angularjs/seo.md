# SEO

- Serve pre-rendered version to the crawler or use server-side rendering
- Google crawls JS but requires everything that manipulates a URL to be a link
- Content that took longer than 4 seconds to render or content that would not render until an event was fired by a link not in an "a" container, did not get indexed by Google
- Provide a sitemap.xml file with all canonical URLs and submit to Google’s Search Console
- Allow your AngularJS to be rendered by Google without pre-rendering and see what happens. Do use the HTML5 history API to update the visible URL in the browser without using a #! if you can possibly avoid it, and provide a sitemap.xml file with all canonical URLs and submit to Google’s Search Console
- Don’t build anything new in Angular 1.x. Switch to Angular 2.0. Angular 2.0 works on the front end a lot more like React with regards to how it allows for server side rendering
- The classic advice has always been to make your content accessible to search engines by avoiding JavaScript only views
- Build HTML pages (static pages) in HTML and not Angular
- Use [PhantomJS](http://phantomjs.org/) to download a page, run the JS, and spit out the HTML into a temporary file. [sptting-out-the-html-pages](https://www.yearofmoo.com/2012/11/angularjs-and-seo.html#sptting-out-the-html-pages)
- Create a sitemap for the website. Within your website, use the hashbang or HTML5 URLS to point to the content--Google and Bing are smart enough to figure out that they're AJAX-generated pages. [example](https://github.com/yearofmoo-articles/AngularJS-SEO-Article/blob/master/sitemap.xml)

## Crawling Hashbang URLs

Many search engines will recognize the `#!` in a url and automatically request a new URL by replacing it with `
?_escaped_fragment_=` and our parameter included on the end:

**Recognizes**

```
http://builtvisible.com/#!/1/2/3/products/content
```

**Requests**

```
http://builtvisible.com/?_escaped_fragment_=/1/2/3/products/content
```

- Ensure that HTML pre-fetching is running on your web server
- If you’re able to pre-render your site as HTML the only other thing you’ve got to be able to do before testing is make sure requests containing the escaped fragment parameter are routed to your HTML cache directory on your webserver

**.htaccess**

[example](https://github.com/yearofmoo-articles/AngularJS-SEO-Article/blob/master/.htaccess)

or

**NGINX**
```
server {
  # ... your config for your server daemon
  # listen 80;
  # server_name  localhost;
  # root   /path/to/root/
  # index  index.html;
  if ($args ~ "_escaped_fragment_=/?(.+)") {
    set $path $1;
    rewrite ^ /snapshots/$path;
  }
}
```

## Meta fragment

```html
<meta name="fragment" content="!">
```

This website doesn’t use hashbangs in the URL structure, so the the “meta fragment” declaration made in the <head> is an instruction to search engines to request the URL with the ?escaped_fragment_= parameter.

Hashbangs *are* stupid. Don’t use them. Not if you don’t have to. Use Angular’s $location service to construct URLs without the #! via the HTML5 History API and save yourself a lifetime of misery.


# Angular 1.x

Prior to Angular 2 (assuming you were using AngularJS) if you were hoping to have something that a search engine could understand, you’d have to follow the guidelines discussed here to fetch the output HTML and display that to a crawler instead of JS templates with no data.

With Angular 2 we can render entire pages on the server, with different data inserted based on the page, and therefore solve our no-data headaches. We do this with dependency injection

## Hashbangs or HTML5 History URLs?

If you use hashbang URLs then all you need to do is instruct AngularJS to use them instead of regular hash values. Google will now recognize the URL and then do what it has to do to fetch the HTML version

```JavaScript
angular.module('HashBangURLs', []).config(['$locationProvider', function($location) {
  $location.hashPrefix('!');
}]);
//then add this module as a dependency within your primary module(s).
```

If you wish not to use hashbang URLs but still inform Google that your website contains AJAX content then include this meta tag within the head tag of the file being accessed at the given URL.

```HTML
<meta name="fragment" content="!" />
```

Then configure AngularJS to use HTML5 URLs when handling URLs and routes:

```JavaScript
//get the module from creating an angular module
angular.module('HTML5ModeURLs', []).config(['$routeProvider', function($route) {
  $route.html5Mode(true);
}]);
```

Then whichever method you choose can be installed via module:

```JavaScript
//get the module from creating an angular module
var App = angular.module('App', ['HashBangURLs']);
//or
var App = angular.module('App', ['HTML5ModeURLs']);
```

Suggestion is to stick to using hashbang URLs since you can mix both non-AJAX pages (like basic forms and so on) to work with non-hashbang HTTP URLs (like registration pages, forms, etc...).


## Resources

- [SEO for Universal Angular 2.0](https://builtvisible.com/universal-angular-2-server-side-rendering-seo-crawl-friendliness/)
- [Universal (isomorphic) javascript support for Angular2](https://github.com/devCrossNet/universal) - for rendering app on server side
- [The Basics of JavaScript Framework SEO in AngularJS](https://builtvisible.com/javascript-framework-seo/)
- [How do I create an HTML snapshot?](https://developers.google.com/webmasters/ajax-crawling/docs/html-snapshot)
- [AngularJS and SEO](https://www.yearofmoo.com/2012/11/angularjs-and-seo.html)
- [AngularJS SEO Article demonstration code](https://github.com/yearofmoo-articles/AngularJS-SEO-Article)
- [ng2-meta](https://github.com/vinaygopinath/ng2-meta) - Dynamic meta tags and SEO in Angular2
