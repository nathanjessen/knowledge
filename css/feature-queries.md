---
layout: default
title: Feature Queries
parent: CSS
---

- [W3 Spec](http://www.w3.org/TR/css3-conditional/#at-supports)
- [Browser Support](http://caniuse.com/#feat=css-featurequeries)

## Usage

The Feature Query looks a lot like a Media Query definition and it accepts `or`, `and`, and `not` statements.

The Feature Query tests the property and value so both need to be provided. In most cases, you only need to test for one or the other but both should be provided.

```CSS
@supports (display: grid) {
  /* Code that will only run if CSS Grid is supported by the browser */
}
```

## Benefits

- No longer have to rely on [Modernizr](https://modernizr.com/) to detect feature support.
- Begin using features earlier.

## Best Practices

**DO NOT write code like this**

```CSS
@supports not (display: grid) {
    /* code for older browsers */
}
@supports (display: grid) {
    /* code for newer browsers */
}
```

**DO write code like this**

```CSS
/* fallback code for older browsers */

@supports (display: grid) {
    /* code for newer browsers. including overrides of the code above, if needed */
}
```


## More Examples

```CSS
@supports (initial-letter: 4) or (-webkit-initial-letter: 4) {
  p::first-letter {
     -webkit-initial-letter: 4;
     initial-letter: 4;
     color: #FE742F;
     font-weight: bold;
     margin-right: 0.5em;
  }
}
```

In this example, we test to see if the property is supported and apply the rules only if it is supported. The value for this property doesn't really matter but must be provided.
