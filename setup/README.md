<h1>
  <span class="headline">Website Layout and Animation</span>
  <span class="subhead">Setup</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to create an HTML page and connect a CSS file.

## Create a place to work

We need one HTML file for the content and one CSS file for its appearance. In your lessons directory, run these commands in Git Bash or your Mac terminal:

```bash
mkdir game-page-layout
cd game-page-layout
mkdir css
touch index.html css/style.css
code .
```

In `index.html`, type `!` and press **Tab** to create the HTML boilerplate. Change the text inside `<title>` to `Pattern Match`.

The browser also needs to know where our CSS lives. Inside `<head>`, add:

```html
<link rel="stylesheet" href="./css/style.css">
```

## Give visitors a starting point

A page should explain what it is and what someone can do there. Inside `<body>`, add a main content area with a heading and instructions:

```html
<main class="page">
  <h1>Pattern Match</h1>
  <p>
    In the finished game, choose two tiles to look for a matching pair.
    Match every pair before you run out of moves.
    Use Restart game to begin again.
  </p>
</main>
```

We will keep adding content **inside** this `<main>`. Its `page` class will let us control the width of the whole content area.

## Keep related content together

Our example needs a status message and a restart action. Below the instructions, before `</main>`, add:

```html
<div class="controls">
  <p id="message">Game status: Ready to play.</p>
  <button class="reset-button" type="button">Restart game</button>
</div>
```

The `<div>` groups these related elements so we can arrange them together. On another website, this group might hold a search result count and a filter button.

Below the controls, still inside `<main>`, add the tiles:

```html
<h2>Game board</h2>
<div class="board">
  <button class="tile" type="button">Tile 1</button>
  <button class="tile" type="button">Tile 2</button>
  <button class="tile" type="button">Tile 3</button>
  <button class="tile" type="button">Tile 4</button>
</div>
```

We use real buttons for actions. They already support keyboard focus, which we will explore later. The buttons will need JavaScript before they can change the game.

## Confirm the stylesheet is connected

In `css/style.css`, give the page a readable starting appearance:

```css
body {
  font-family: system-ui, sans-serif;
  background-color: #f1f5f9;
  color: #0f172a;
}
```

`system-ui` uses the device's system font. The dark text and light background give us a clear starting point.

Open `index.html` in your browser. You should see the content on a pale background. If the background has not changed, check the stylesheet path before continuing.

> 🧠 Later snippets sometimes show only a new property. Add it between the braces of the rule named in the instructions, keeping the other properties. Save and refresh after each change so you can see its effect.
