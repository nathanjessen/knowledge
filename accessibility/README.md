# Accessibility

## Tips

- Hide content using the hidden attibute. Provide a fallback in CSS for browsers that don't support it. `[hidden] { display: none; }`
- Always place an alt attribute on an `<img>` element. If it is purely decorative or doesn't add valuable information, leave the alt attribute empty.
- Don't start an alt attribute with "Picture/Image/Graphic of" because screen readers do that by default.
- Structure headings correctly since screen readers provide a way of moving from one heading to another.
- Use landmark elements to help mark sections `<article>, <nav>, <aside>, <section>, <main>, <footer>, <header>` because screen readers allow user to jump between these landmarks. Use `<header role="banner">` and `<footer role="contentinfo">` for older browsers.
- Group form elements using `<fieldset>` but only if you have multiple form elements that gorm a group and a corresponding label for that group such as something that fits in a `<legend>`.

  ```html
  <form>
    <fieldset>
      <legend>T-Shirt size</legend>
      <input type="radio" id="s" name="shirtsize" />
      <label for="s">S</label>  
      <input type="radio" id="m" name="shirtsize" />
      <label for="m">M</label>  
      <input type="radio" id="l" name="shirtsize" />
      <label for="l">L</label>   
    </fieldset>
  </form>
  ```

- Provide an `aria-label` to navigation elements to help differentiating different navigations. Screen readers will announce "site navigation landmark, list of four items, home link.” for the first and "about page navigation landmark, list of four items, introduction same page link.”

  ```html
  <nav role="navigation" aria-label="Site">
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/about">About</a></li>
      <li><a href="/blog">Blog</a></li>
      <li><a href="/contact">Contact</a></li>
    </ul>
  </nav>

  <nav role="navigation" aria-label="About page">
    <ul>
      <li><a href="#intro">Introduction</a></li>
      <li><a href="#what-I-do">What I do</a></li>
      <li><a href="#testimonials">Testimonials</a></li>
      <li><a href="#get-a-quote">Get a quote</a></li>
    </ul>
  </nav>
  ```


## Color Contrast

- [Add Colors To Your Palette With Color Mixing](https://www.viget.com/articles/add-colors-to-your-palette-with-color-mixing)
- [Color Contrast for Better Readability](https://www.viget.com/articles/color-contrast)

## Additional Resources

* [The A11Y Project](http://a11yproject.com/) - Collection of resources
* [The Accessibility Cheatsheet](https://bitsofco.de/the-accessibility-cheatsheet/) - Article
* [How to Meet WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref/) - Reference
* [Interactive WCAG 2.0](http://code.viget.com/interactive-wcag/#responsibility=&level=aa) - Reference
* [MIND Patterns - Accessibility Patterns for the Web](https://ebay.gitbooks.io/mindpatterns/content/) - Patterns
* [Marco's Accessibility Blog](https://www.marcozehe.de/) - Blog
* [Accessibility Guidelines](http://accessibility.voxmedia.com/) - Checklist
* [GoogleChrome/accessibility-developer-tools](https://github.com/GoogleChrome/accessibility-developer-tools) - Library
* [Acce{CSS}](http://lukyvj.github.io/accecss/) - Sass Mixin
* [Frend](https://frend.co/) - Components
* [ARIA Examples](http://heydonworks.com/practical_aria_examples/) - Article
* [Using ARIA to enhance SVG accessibility](https://www.paciellogroup.com/blog/2013/12/using-aria-enhance-svg-accessibility/) - Article
* [How to Make Accessible Web Components — a Brief Guide](https://www.sitepoint.com/accessible-web-components/) - Article
* [Accesslint.js](https://github.com/accesslint/accesslint.js) - Tool
* [addyosmani/a11y](https://github.com/addyosmani/a11y) - Audit tooling
* [tota11y](http://khan.github.io/tota11y/) - Toolkit
* [Accessibility Developer Tools](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb) - Chrome Extension
* [ChromeLens](http://chromelens.xyz/) - Chrome Extension
* [ChromeVox](https://chrome.google.com/webstore/detail/chromevox/kgejglhpjiefppelpmljglcjbhoiplfn) - Chrome Extension
* [ally.js](https://allyjs.io/)
* [Accessible floating labels](http://allthingssmitty.com/2016/09/25/accessible-floating-labels/)
* [Accessibility Inspector](https://docs.google.com/document/d/1bj9Dc3_DnezF-IeNg51LEG2zfGtxD3YKP5t7SBB_-Dk/edit) - Inside Chrome Dev Tools
* [Tenon](https://tenon.io/) - Pay Service
* [High Contrast](https://chrome.google.com/webstore/detail/high-contrast/djcfdncoelnlbldjfhinnjlhdjlikmph?hl=en) - Chrome Extension
* [Wave](http://wave.webaim.org/) - Evaluation Tool
* [Jaws](http://www.freedomscientific.com/Products/Blindness/JAWS) - Screen Reader
* [NVDA](http://www.nvaccess.org/) - Screen Reader
* [Ways to Make a UI Accessibile](https://medium.com/fed-or-dead/ways-to-make-a-ui-accessible-part-i-84b5088acfb7#.66rzyjpvg)
* [Aria Landmarks Example](https://w3c.github.io/aria-practices/examples/landmarks/index.html)
