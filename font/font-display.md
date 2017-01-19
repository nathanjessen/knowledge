# Font Display

Gives us the same power found in browser features such as the [Font Loading API](https://drafts.csswg.org/css-font-loading) and third party scripts such as [Bram Stein's Font Face Observer](https://github.com/bramstein/fontfaceobserver). Helps to prevent us from having to write JS to override some browser behavior and adding additional HTTP requests.

## Font download timeline

1. The first period is the font block period. During this period, if the font face is not loaded, any element attempting to use it must instead render with an invisible fallback font face. If the font face successfully loads during the block period, the font face is then used normally.
1. The font swap period occurs immediately after the font block period. During this period, if the font face is not loaded, any element attempting to use it must instead render with a fallback font face. If the font face successfully loads during the swap period, the font face is then used normally.
1. The font failure period occurs immediately after the font swap period. If the font face is not yet loaded when this period starts, it’s marked as a failed load, causing normal font fallback. Otherwise, the font face is used normally.

## Usage

- Used inside of a `@font-face` declaration for custom fonts.
- Most of the time you'll want to go with `swap`.
- If you have fonts on the page that you'd like to have load, but could ultimately do without, consider going with fallback or optional.

```CSS
@font-face {
  font-family: "Open Sans Regular";
  font-weight: 400;
  font-style: normal;
  src: url("fonts/OpenSans-Regular-BasicLatin.woff2") format("woff2");
  font-display: swap;
}
```

It supports a range of values: `auto | block | swap | fallback | optional`.

** auto **

auto uses whatever font display strategy the user-agent uses. Most browsers currently have a default strategy similar to block

** block **

block gives the font face a short block period (3s is recommended in most cases) and an infinite swap period. In other words, the browser draws "invisible" text at first if the font is not loaded, but swaps the font face in as soon as it loads. To do this the browser creates an anonymous font face with metrics similar to the selected font but with all glyphs containing no "ink." This value should only be used if rendering text in a particular typeface is required for the page to be useable.

** swap **

swap gives the font face a zero second block period and an infinite swap period. This means the browser draws text immediately with a fallback if the font face isn’t loaded, but swaps the font face in as soon as it loads. Similar to block, this value should only be used when rendering text in a particular font is important for the page, but rendering in any font will still get a correct message across. Logo text is a good candidate for swap since displaying a company’s name using a reasonable fallback will get the message across but you’d eventually use the official typeface.

** fallback **

fallback gives the font face an extremely small block period (100ms or less is recommended in most cases) and a short swap period (three seconds is recommended in most cases). In other words, the font face is rendered with a fallback at first if it’s not loaded, but the font is swapped as soon as it loads. However, if too much time passes, the fallback will be used for the rest of the page’s lifetime. fallback is a good candidate for things like body text where you’d like the user to start reading as soon as possible and don’t want to disturb their experience by shifting text around as a new font loads in.

** optional **

optional gives the font face an extremely small block period (100ms or less is recommended in most cases) and a zero second swap period. Similar to fallback, this is a good choice for when the downloading font is more of a “nice to have” but not critical to the experience. The optional value leaves it up to the browser to decide whether to initiate the font download, which it may choose not to do or it may do it as a low priority depending on what it thinks would be best for the user. This can be beneficial in situations where the user is on a weak connection and pulling down a font may not be the best use of resources.

## References

- [font-display for the Masses](https://css-tricks.com/font-display-masses/)
- [Controlling Font Performance with font-display](https://developers.google.com/web/updates/2016/02/font-display)
