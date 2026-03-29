---
title: "basic"
draft: false
---

tag : #css #frontend
# CSS Basics

- Together decleartion and selector are called **ruleset**

## The Cascade

Cascade refers to the process by which the browser determines which styles should be applied to an element when there are multiple conflicting style rules. 

-  The cascade considers six criteria in the following order to resolve the difference:-
  1. *Stylesheet origin* — Where the styles come from. Your styles are applied in conjunction with the browser’s default styles.
  2. *Inline styles* — Whether a declaration is applied to an element via the HTML style attribute or a CSS selector.
  3. *Layer* — Styles can be defined in layers, each with a different priority.
  4. *Selector specificity* — Which selectors take precedence over which.
  5. *Scope proximity* — Whether the styles are scoped to a portion of the DOM.
  6. *Source order* — Order in which styles are declared in the stylesheet


### Source Order

- The final step to resolving the cascade is Source Order,sometimes referred to as order of appearance 

- This selector targs an element that matches both criteria a `<a>` tag with class of .featured 

```css
a.featured{
  background-color:red;
}
```

- **Cascaded Value** A cascaded value is a value for a particular property applied to an element as a result of the cascade

## Inheritance

- The cascade frequently conflated with the concept of inheritance  
- Properties that can inherited
   - `color, font, font-family, font-size, font-weight, font-variant,font-style, line-height, letter-spacing, text-align, text-indent, text-transform,white-space, and word-spacing.`


## Important Concepts

- Sometimes you want to undo any styles on the current stage of your css file, you can use:
  `{property:initial;}`
    - This css `initial` value will set your initial value of that property to default.







