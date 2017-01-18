# CSS

## Tips

- Consider how you and others will maintain the code for the long term
- Make small refactors as you go along
- Use visual regression testing to tell you if something has changed unexpectedly ([PhantomCSS](https://github.com/Huddle/PhantomCSS))
- Maintain a consistent approach using an agreed upon code style, linting, and code reviews
- Set up a good architecture
- Encourage others to contribute

## Cheat Sheets

- [CSS Vocabulary](http://apps.workflower.fi/vocabs/css/en)
- [CSS 3, Media Queries Cheat Sheet](http://mac-blog.org.ua/css-3-media-queries-cheat-sheet/)
- [CSS Properties Index](https://meiert.com/en/indices/css-properties/)
- [CSS 3 selectors explained](http://www.456bereastreet.com/archive/200601/css_3_selectors_explained/)

## Tricks

**1\. Use empty-cells to style table empty cells:**

Surprisingly the browser support is quite good and extends back to IE8.
Convenient to give less visual predominance to empty cells.

```CSS
table {
  empty-cells: hide;
}
```

**2\. border-radius can be made non-symmetric:**

In short you can define the horizontal and vertical radius independently.
This gives room for interesting shapes. The left part of the slash is the horizontal radius, the right part is the vertical radius.

```CSS
.custom-round {
  border-radius: 15px 15px 15px 10px / 5px 5px 20px 5px;
}
```

**3\. Use pseudo-elements to style the first letter and line:**

No need to resort to another element to wrap the first letter or line of a `<p>` to style them differently:

```CSS
p::first-letter {
font-size: 2rem;
}

p::first-line {
font-weight: 600;
}
```
