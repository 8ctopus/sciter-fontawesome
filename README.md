# sciter fontawesome

This is a [sciter.js](https://sciter.com/) fontawesome support.

![sciter fontawesome](screenshot.png)

## get started

- git clone the repository
- run `install.bat` to download the latest sciter binaries and library
- start `scapp.exe`
- to refresh the app after changes to the html/css click `F5`

## debug app

- start `inspector.exe`
- inside the `scapp.exe` window click `CTRL + SHIFT + I` to connect to the inspector
- click `CTRL + SHIFT + left click` to inspect an element
- note: the clock component forces the DOM to refresh every second, remove the component if you want to inspect in peace.

## install

- add the `src` dir to your project
- then in your code include `<style src="src/fontawesome.css" />`

# how to get it to work

Download in respective directories `css` and `fonts`:

    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.css
    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/webfonts/fa-brands-400.ttf
    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/webfonts/fa-regular-400.ttf
    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/webfonts/fa-solid-900.ttf

In `all.css`

- remove unrecognized `@-webkit-keyframes` properties
- replace all `:before` by `::before`
- remove all `src` from `@font-face` except the ttf ones
- remove `format("truetype")` from `@font-face`
- add to the end of file

```css
// reset ux-master.css default vertical flow
button {
  flow: horizontal;
}

// reset master-base.css properties on first and last child
button > :first-child {
  margin-top: 0;
}

button > :last-child {
  margin-bottom: 0;
}

// fix icons vertical alignment in button
button > i {
  vertical-align: middle;
}

// improve icon position in button
button > i:first-child {
  margin-right: 0.5em;
}

button > i:last-child {
  margin-left: 0.5em;
}
```
