<h1>
  <span class="headline">Website Layout and Animation</span>
  <span class="subhead">Size the Content</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to create a content area that has predictable spacing and a limited width.

## Choose the space around the content

The browser supplies a small margin around `<body>`. We want to choose our own spacing. In the existing `body` rule, add:

```css
margin: 0;
```

The content now sits against the edges. To give it breathing room, add a new rule below `body`:

```css
.page {
  padding: 1rem;
}
```

**Padding** creates space inside the element. `1rem` is the font size of the root `<html>` element, commonly 16px. It gives us a useful unit for spacing that can follow a user's preferred text size.

> 💡 `rem` does not automatically get smaller when the browser window gets narrower. It follows the root text size.

## Keep padding inside the chosen width

We want the content area to use the available width. Add this inside the existing `.page` rule:

```css
width: 100%;
```

Now notice the extra horizontal space: the page can overflow the window. By default, a regular element's declared width covers its **content**; padding is added outside that width. We have asked for 100% of the available width, plus padding on both sides.

To make the declared width include padding and borders, add this rule at the top of the stylesheet:

```css
* {
  box-sizing: border-box;
}
```

The `*` selects every element. With `border-box`, our 100% width includes the padding, so it fits again. This is a useful starting rule for websites because it makes sizing easier to predict. Margins still sit outside the box.

## Limit wide content without blocking small screens

On a wide window, our content can spread much farther than it needs to. Add this inside `.page`:

```css
max-width: 48rem;
```

The page still uses `width: 100%`, but it stops growing at `48rem`. This combination is useful for forms, articles, and other content that should fit a small window while staying comfortable to read on a large one.

Once the maximum width is reached, the content sits on the left. To share the unused space between both sides, add:

```css
margin: 0 auto;
```

Here, `0` sets the top and bottom margins. `auto` shares the remaining horizontal space between the left and right margins. It centers the **container**; it does not center the text inside it.

## 🎓 You Do

Temporarily change `max-width` to `32rem` and resize the browser. Notice how the content stops growing sooner, then restore `48rem`.
