<h1>
  <span class="headline">Website Layout and Animation</span>
  <span class="subhead">Make the Page Easy to Use</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to improve text and controls for people using a mouse, keyboard, or assistive technology.

## Make button text match the page

Our page has a chosen font, but buttons can keep the browser's own font styles. To make their text consistent with the surrounding page, add this rule above the width media query:

```css
.tile,
.reset-button {
  font: inherit;
}
```

The comma applies one rule to both classes. `inherit` tells the buttons to use their parent's font settings, including the text size. This pattern is also useful for buttons in forms and toolbars.

## Give an action enough room

The restart button has little space around its label. Give it inner space and a comfortable minimum height with a separate rule:

```css
.reset-button {
  padding: 0.75rem 1rem;
  min-height: 3rem;
}
```

The first padding value is for the top and bottom; the second is for the left and right. Larger controls with space between them are easier to select, especially with touch input.

## Keep labels readable against their backgrounds

If we choose a dark background for a button, we also need a text color that is easy to read on it. Add both properties to the earlier rule shared by `.tile` and `.reset-button`:

```css
background-color: #1e3a5f;
color: #ffffff;
```

**Contrast** describes how distinguishable the text is from its background. For normal text, the WCAG AA minimum ratio is **4.5:1**. Enter both colors into the [WebAIM contrast checker](https://webaim.org/resources/contrastchecker/) instead of relying on appearance alone.

This applies to headings, instructions, error messages, and other website text too. A plain background often makes text easier to keep readable than placing it over an image.

## Show which control the keyboard will use

Press **Tab** to move between the buttons. The control receiving keyboard input has **focus**. Real `<button>` elements support this automatically; a styled `<div>` does not.

Browsers provide a focus indicator. To give ours a clear, consistent appearance, add this rule above the width media query:

```css
button:focus-visible {
  outline: 3px solid #0f172a;
}
```

The `:focus-visible` part selects a button when the browser needs to show its focus, such as during keyboard navigation. The outline marks the whole button.

To separate the outline from the button's edge, add this inside the same rule:

```css
outline-offset: 3px;
```

Move through the controls with Tab again. Keep a visible indicator in your own designs. Once JavaScript is connected, a focused button can also be activated with Enter or Space; our preview has no game actions yet.

## Make information available in words

A green background alone does not tell everyone that an action succeeded. For our game, we can show **You win!** in the message. A booking form could show **Your booking is confirmed.** Keep important information in visible text even when you also use color or sound.

Images need care too. A **screen reader** can speak webpage content aloud. For a meaningful `<img>`, an `alt` attribute gives a text alternative, such as `alt="A bird with its wings raised"`. For a purely decorative `<img>`, use `alt=""` so it can be skipped. We will use a decorative background image in the sprite example.

## 🎓 You Do

Use Tab and Shift+Tab to move forward and backward through every button. Check that the focus indicator stays visible. Then use the contrast checker to confirm that our button text passes the normal-text AA check.
