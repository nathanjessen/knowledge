# Print

Intended for paged material and for documents viewed on screen in print preview mode. A member of the [@media](https://developer.mozilla.org/en-US/docs/Web/CSS/@media) CSS at-rule.

```
@media print {

}
```

## Resources

- [I Totally Forgot About Print Stylesheets](https://uxdesign.cc/i-totally-forgot-about-print-style-sheets-f1e6604cfd6#.96a8vruuv)
- [Gutenberg](https://github.com/BafS/Gutenberg)
- [Hartija](https://github.com/vladocar/Hartija---CSS-Print-Framework)

## Tips

- In DevTools, show the console drawer `Esc`, open the rendering pane, check Emulate CSS Media and select Print
- It's ok to use absolute units like `cm`, `mm`, `in`, `pt` or `pc`
- Create page specific rules with the `@page` rule

  ```
  @media print {
    @page {
      margin: 1cm;
    }
  }
  ```

- Control how page switches are handled using [CSS Pages](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Pages)
- Remove unnecessary content with `display: none;`. For instance, maybe everything but the `<main>` element should be hidden.

  ```
  body > *:not(main) {
    display: none;
  }
  ```

- Display links target next to its text

  ```
  a[href]:after {
    content: " (" attr(href) ")";
  }
  ```

  Or only links that start with http and don't contain mywebsite.com in its value.

  ```
  a[href^="http"]:not([href*="mywebsite.com"]):after {
    content: " (" attr(href) ")";
  }
  ```

- Reveal abbreviations

  ```
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  ```
