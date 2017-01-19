# Font Face Observer

[Bram Stein's Font Face Observer](https://github.com/bramstein/fontfaceobserver)

Tracks when fonts are loaded

## Usage

- Style the document first using system fonts
- Use JS to load a custom font
- Add a class to the document to toggle rendering of the custom font
- Set a mark in storage for future page views to simplify JS on future page views

**CSS**

```CSS
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  src: local('Roboto'), local('Roboto-Regular'),
       url('fonts/roboto-v15-latin-regular.woff2') format('woff2'),
       url('fonts/roboto-v15-latin-regular.woff') format('woff');
}

body {
  font-family: "Arial", "Helvetica", sans-serif;
}

.fonts-loaded body {
  font-family: "Roboto", "Arial", "Helvetica", sans-serif;
}
```

**JavaScript in `<head>`**

```JS
/* include loadJS library */

/* check if font was previously used */
if (sessionStorage.getItem('fonts-loaded')) {
  // fonts cached, add class to document
  document.documentElement.classList.add('fonts-loaded');
} else {
  // load script with font observing logic
  loadJS('font.js');
}
```

**JavaScript in `font.js`**

```JS
/* incude Font Face Observer script */

/* observation logic and class addition */
var robotoFamily = new FontFaceObserver('Roboto');

robotoFamily
  .load()
  .then(function() {
    document.documentElement.classList.add('fonts-loaded');
    // set mark on storage for future page views
    sessionStorage.setItem('fonts-loaded', true);
  });
```

## Resources

- [Font loading strategy for static generated sites](https://jeremenichelli.github.io/2016/05/font-loading-strategy-static-generated-sites/)
- [font-strategy-static](https://github.com/jeremenichelli/font-strategy-static/)
