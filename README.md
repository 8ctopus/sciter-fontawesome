# sciter fontawesome

Fontawesome 6 support for [sciter.js](https://sciter.com/).

![sciter fontawesome](https://github.com/8ctopus/sciter-fontawesome/raw/master/screenshot.png)

## demo

- git clone the repository
- install packages `npm install`
- install latest sciter sdk `npm run install-sdk`
- start the demo `npm run scapp`

## demo requirements

- A recent version of Node.js `node` (tested with 22 LTS) and its package manager `npm`.
    - On Windows [download](https://nodejs.dev/download/) and run the installer
    - On Linux check the [installation guide](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04#option-2-%E2%80%94-installing-node-js-with-apt-using-a-nodesource-ppa)

## add to your project

### using npm

- install package `npm install sciter-fontawesome`
- include `<style src="node_modules/sciter-fontawesome/src/fontawesome.css" />`

### copy source

- add the `src` dir to your project
- include `<style src="src/fontawesome.css" />`

## known issues

- on linux the fontawesome font cannot be installed [\*](https://sciter.com/forums/topic/css-load-font-on-linux-fails/)

    >> Current Linux implementation does not support this functionality.
    >> GTK/Cairo has no means for that.
    >> Please wait for Sciter 5.X.X.X where I am switching to Skia as a primary backend on Linux.

- [css `@keyframes` are not working since 4.4.8.27](https://sciter.com/forums/topic/css-keyframes-issue/)

## how to convert fontawesome css to work with sciter

- download

    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.css
    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/webfonts/fa-brands-400.ttf
    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/webfonts/fa-regular-400.ttf
    https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/webfonts/fa-solid-900.ttf

- in all `all.css`

    - remove unrecognized `@-webkit-keyframes` properties
    - remove all `:root, :host {...}`
    - replace all `:before` by `::before`
    - remove all `src` from `@font-face` except the `ttf` ones
    - remove `format("truetype")` from `@font-face`
    - comment `unicode-range:...;`
    - finally add to the end of file

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
