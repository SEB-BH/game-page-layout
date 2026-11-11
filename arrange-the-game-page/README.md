<h1>
  <span class="headline">Website Layout and Animation</span>
  <span class="subhead">Arrange Related Items</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to arrange and space a group of elements with Flexbox.

## Give the tiles room for their content

The tile buttons currently fit their short labels. In this interface, we want larger areas that could hold a picture or symbol. Below your existing rules in `css/style.css`, add:

```css
.tile {
  width: 7rem;
  min-height: 7rem;
}
```

`min-height` gives each tile a minimum height while allowing it to grow if its content needs more room. Giving content room to grow is also useful for product cards and buttons with longer labels.

## Put one container in charge of the layout

Our buttons already sit beside each other when there is room. However, the small spaces between them come from whitespace in the HTML. We want CSS to control their arrangement and spacing.

In the HTML, `.board` contains the four tile buttons. Make that **parent** a flex container:

```css
.board {
  display: flex;
}
```

Its direct children are now **flex items**, arranged in a row by default. The parent controls how those children are laid out.

This parent-and-children pattern also works for a row of navigation links or a group of form buttons. A class name does not activate Flexbox; `display: flex` does.

## Separate the items consistently

The tiles are crowded together. Inside the existing `.board` rule, add:

```css
gap: 0.75rem;
```

`gap` creates consistent space **between** the flex items. We can change the spacing in one place, even if we add more items later.

## Position the group in the available space

On a wide window, there is unused space after the tiles. To place the group in the middle of its row, add this inside `.board`:

```css
justify-content: center;
```

`justify-content` positions items along the **main axis**: the direction in which the items are arranged. Our items form a row, so this moves them horizontally. If the items fill the whole row, there is no spare space to distribute.

To make the container's area easier to see, give `.board` a background and some inner space:

```css
background-color: #dbeafe;
padding: 1rem;
```

The background shows the full container. Notice the difference: `padding` separates the tiles from the container's edges; `gap` separates one tile from the next.

## Prepare a group that can change direction

The status message and restart button should stack in a narrow window and sit beside each other when there is more room. We can use Flexbox for this group too.

Add a new rule for their parent:

```css
.controls {
  display: flex;
}
```

The message and button move into a row. For our starting layout, change the direction by adding this inside `.controls`:

```css
flex-direction: column;
```

Now the items stack vertically. Add space between them:

```css
gap: 0.5rem;
```

The button stretches across the column by default. This can make a useful full-width action on a small screen. We will control its alignment when we change this group into a row.

> 🧠 Each flex container arranges its own direct children. Making `.controls` a flex container does not change the layout of `.board`.

## 🎓 You Do

On a wide window, change the board's `justify-content` to `space-between`. Compare how the first and last tiles move towards the edges as the spare space is placed between the tiles. Restore `center` afterwards.
