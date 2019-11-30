# Component Quality Checklist

A quality checklist for making your User Interface (UI) or presentational components, be:

- accessible
- consumable
- portable
- reusable
- and robust.

## Table of Contents

- External Spacing
- API Design
    - `children` usage
    - Do not expose `className`
    - Consistent prop names
    - Use prop types
    - Take it easy with booleans

## External Spacing

### The Rule

The root element of a component must not have the `margin` property applied.

### Why?

In CSS, all elements are rectangular boxes that adhere to the [CSS basic box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model) where each box is made up of the following four parts: margin, border, padding, and content. If you inspect any element in your browser's dev tools then you can see a visual representation of this, for example:

Chrome | Firefox
------------ | -------------
 | Content from cell 2


### The Exception(s)

### More Reading

- [Handling spacing in a UI component library](https://medium.com/fed-or-dead/handling-spacing-in-a-ui-component-library-70f3b22ec89)
- [Everything You Need To Know About CSS Margins](https://www.smashingmagazine.com/2019/07/margins-in-css/)
