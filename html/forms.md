# Forms

## CSS Validation

```CSS
[type="checkbox"] + label {
  font-weight: normal;
}

[type="checkbox"]:checked + label {
  font-weight: bold;
}

[required]:valid + span {
  color: green;
}

[required]:invalid + span {
  color: red;
}
```
