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

## Resources

- [Web fonts](https://meowni.ca/posts/web-fonts/)
