# User Experience

## Google Heart Framework

- [Measuring the User Experience on a Large Scale: User-Centered Metrics for Web Applications](https://research.google.com/pubs/pub36299.html)
- [How Google Improves User Experience with the HEART Framework](http://www.appcues.com/blog/google-improves-user-experience-with-heart-framework/)

## Confirmation Design

- Users disregard confirmations when bombarded by them
- Confirmations shouldn't be used for actions that are inconsequential or easily reversed
- Present the action as a question in the header
- Explain the outcome of the action in the body
- Restate the action in the confirmation button
- Avoid Ambiguous questions like “Are you sure?”
- Avoid Non-descriptive body copy
- Avoid Yes/No actions
- Avoid “Cancel”. It's confusing. It may be confused with the intended action of canceling a service instead of dismissing the confirmation dialog.

```html
<header><h1>Delete location?</h1></header>
<section>
  <p>Deleting a location will permanently remove it from your network.</p>
</section>
<footer>
  <button type="reset" name="keep" class="button">No, Keep Location</button>
  <button type="submit" name="delete" class="button button-primary">Yes, Delete Location</button>
</footer>
```

** Source: ** [Designing Confirmation](https://uxdesign.cc/designing-confirmation-278d159723e#.rafzk5p6v)
