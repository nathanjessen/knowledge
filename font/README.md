# Font

Our goal should be to optimize the time it takes for a page to load and render. Web fonts require additional HTTP requests and the process is render blocking. To mitigate some of the risk of a slow font download, most browsers implement a timeout after which a fallback font will be used. However, implementation in browsers vary and some don't have a timeout at all.

**"Flash of Invisible Text" (FOIT)**

When a browser loads a font, text that is styled to use that typeface is hidden until the font is loaded. There is no delay for system fonts but custom fonts require time to be requested and downloaded.

**"Flash of Un-styled Content" (FOUC)**

Chrome stops waiting for a web font after 3 seconds. Instead of showing you invisible ink, it paints the text in your fallback font. When your web font is finally downloaded, it then re-paints the already displayed text with the new font.

## Methods to Improve Performance

1. Font Face Observer
1. Font Loading API
1. Font Display Property

## Font Stacks

| Wordpress          | Medium             | Ghost              | Github             |
| ------------------ | ------------------ | ------------------ | ------------------ |
| -apple-system      | -apple-system      | -apple-system      | -apple-system      |
| BlinkMacSystemFont | BlinkMacSystemFont | BlinkMacSystemFont | BlinkMacSystemFont |
| "Segoe UI"         | "Segoe UI"         | "Segoe UI"         | "Segoe UI"         |
| Roboto             | Roboto             | Roboto             | Roboto             |
| Oxygen-Sans        | Oxygen             | Oxygen             | Helvetica          |
| Ubuntu             | Ubuntu             | Ubuntu             | Arial              |
| Cantarell          | Cantarell          | Cantarell          | sans-serif         |
| "Helvetica Neue"   | "Open Sans"        | "Fira Sans"        ||
| sans-serif         | "Helvetica Neue"   | "Droid Sans"       ||
|                    | sans-serif         | "Helvetica Neue"   ||
|                    |                    | sans-serif         ||

**Sample Font Stacks**

```CSS
:root {
  --font-stack-wordpress: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
  --font-stack-medium: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  --font-stack-ghost: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
  --font-stack-github: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

body {
  font-family: var(--font-stack-wordpress);
}
```

## Resources

- [Web fonts](https://meowni.ca/posts/web-fonts/)
- [The New System Font Stack?](https://bitsofco.de/the-new-system-font-stack/)
