<h1>
  <span class="headline">Website Layout and Animation</span>
  <span class="subhead">Fit Different Screens</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to use wrapping and a media query to adapt a layout to its available width.

## Let crowded items move onto another line

Make the browser window narrower. Flex items try to stay on one line by default, so our tiles can shrink and become crowded. Let them move onto more lines by adding this inside the existing `.board` rule:

```css
flex-wrap: wrap;
```

Resize again. The tiles use their intended width and move onto new rows when they need to. The existing `gap` also separates the rows. Wrapping is useful for tags, groups of controls, and card collections.

> 💡 Wrapping does not guarantee a fixed number of columns. If a game depends on exact row and column positions, its board will need a layout that preserves those positions.

## Use the available width on phones

Check that `<head>` in `index.html` contains this line from the boilerplate. Add it only if it is missing:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This tells mobile browsers to use the device's width for the page. Without it, a phone may lay out a much wider page and shrink the result, making text appear tiny.

## Use extra room when it becomes available

Our controls stack comfortably in a narrow window. In a wider window, there is enough room for the message and restart button to share one row.

A **media query** applies CSS only when a condition is true. At the bottom of the stylesheet, add:

```css
@media (min-width: 600px) {
  .controls {
    flex-direction: row;
  }
}
```

Read the condition as: **when the viewport is at least 600px wide**. Inside it, we select `.controls` and change its direction. Below that width, the original column rule still applies.

The value `600px` is our **breakpoint**. Choose a breakpoint based on when your content has enough space, rather than treating it as a fixed definition of a phone or tablet.

## Place the controls at opposite ends

Widen the window. The button now sits beside the message, with unused space after them. Inside the `.controls` rule **within the media query**, add:

```css
justify-content: space-between;
```

The spare space goes between the two items. This is a common pattern for a heading with an action button, or a logo with navigation links.

The button may also stretch to the height of the row. To line up the centres of the two items instead, add this to that same rule:

```css
align-items: center;
```

`align-items` works across the direction of the items, called the **cross axis**. The two alignment properties depend on the direction:

| Direction | `justify-content` works along | `align-items` works across |
| --- | --- | --- |
| `row` | Horizontal direction | Vertical direction |
| `column` | Vertical direction | Horizontal direction |

> 🧠 Keep the media query after the starting `.controls` rule. Both rules select `.controls` in the same way, so when both apply, the later value wins.

## 🎓 You Do

Test the page in narrow and wide browser viewports. Temporarily change the breakpoint to `700px` and notice where the controls switch direction. Restore `600px` before continuing.
