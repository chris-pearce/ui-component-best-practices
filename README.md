# UI Component Best Practices <!-- omit in toc -->

A bunch of best practices to help achieve User Interface (UI) components, or
presentational components, that are:

- accessible
- consumable
- portable
- reusable
- and robust.

## Table of Contents <!-- omit in toc -->

- [Caveats](#caveats)
- [The tl;dr Version](#the-tldr-version)
- [Components Cannot Apply External Spacing](#components-cannot-apply-external-spacing)
  - [The Rule](#the-rule)
  - [Why?](#why)
    - [Why `margin` Specifically?](#why-margin-specifically)
  - [The Exception(s)](#the-exceptions)
  - [More Reading](#more-reading)

## Caveats

1. This checklist is aimed at components that are part of an organisation's
   component library or wider design system where the design is known.
2. All code snippets are from the [React library](https://reactjs.org/).
   However, this checklist is library/framework-agnostic. Meaning it can apply
   to any component architecture, including [Web
   Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components).

## The tl;dr Version

- [ ] Components cannot apply external spacing.

## Components Cannot Apply External Spacing

### The Rule

The root element of a component must not use the `margin` property.

### Why?

Consider these components being rendered in a view layer:

```jsx
<Search />
<SearchResults />
<Pagination />
<Downloads />
```

There needs to be `40px` of space between each component. We can easily achieve
this by adding `margin-bottom: 40px;` to each of the component's root element.
However, doing that would be short sighted as it now means all
components come with rendering concerns outside of themselves. What happens when
the `<Pagination>` component is used to paginate a different component that has
different spacing requirements, or none at all? What happens when the
`<Pagination>` component is conditionally rendered based on how much data is
displayed in the `<SearchResults>` component?

Whenever a component has baked in external spacing capabilities they become dependent on particular
component configurations which goes against one of the fundamental principls of
UI component development, which is:

> All components are 100% self-contained making them **reusable** and **portable**

When a component only needs to worry about its own spacing concerns, in other
words, only the spacing happening within itself (its content, padding, and border areas, see the
next section for more context) then they can be completely context agnostic all
the while not giving a damn where they're placed in a component tree.

#### Why `margin` Specifically?

In CSS, all elements are rectangular boxes that adhere to the [CSS Box
Model](https://www.w3.org/TR/css-box-3/#box-model). Each box is made up of the
following four areas: **_margin_**, **_border_**, **_padding_**, and
**_content_**. If you open up a browser's developer tools you can see a visual
representation of this. For example, in Firefox:

<img src="images/Firefox&#32;dev&#32;tools&#32;box&#32;model.png" width="326" />

The [**Introduction to the CSS basic box model** MDN web
doc](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
has this to say:

>The **margin** area, bounded by the margin edge, extends the border area to
include an empty area used to separate the element from its neighbors.

The key part being: _"used to separate the element from its neighbors"_ because
it's the `margin` property that is used to create space between components. As
the CSS `background` properties do not apply to the margin area, meaning it's
always transparent, we can say that this space is "external" to a component.

### The Exception(s)

1. Does not apply to layout components.
2. Does not apply to sepecific component compositions such as forms.

### More Reading

- [Handling spacing in a UI component
  library](https://medium.com/fed-or-dead/handling-spacing-in-a-ui-component-library-70f3b22ec89)
- [Everything You Need To Know About CSS
  Margins](https://www.smashingmagazine.com/2019/07/margins-in-css/)
- [CSS Box Model Module Level 3](https://www.w3.org/TR/css-box-3/)
