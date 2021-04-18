# FloatSidebar.js
[![NPM version](https://img.shields.io/npm/v/float-sidebar.svg?style=flat)](https://www.npmjs.org/package/float-sidebar)

> A lightweight (2kb gzipped), zero-dependency, javascript library for creating float sidebars. Based on the finite state machine pattern.

[Demo](https://jsfiddle.net/vursen/cj4erfnj)

The library is based on the finite state machine pattern that led to a more simple and reliable solution. Read more in [the article on medium](https://medium.com/@vursen/state-machine-for-sticky-blocks-70ca0bf4ee97) (in Russian)

## Install

```bash
npm install float-sidebar
```
or
```bash
yarn add float-sidebar
```
or
```html
<script src="./path/to/float-sidebar.min.js"></script>
```

## Usage

```html
<div class="wrapper">
  <div class="content">
    <!-- Content -->
  </div>

  <div class="sidebar">
    <div class="sidebar__inner">
      <!-- Sidebar content -->
    </div>
  </div>
</div>
```

```css
.wrapper {
  display: flex;
  /* Required in case of using an infinite scroll */
  align-items: flex-start;
}

.sidebar {
  /* Required */
  position: relative;

  /* Required. The sidebar element should have a fixed width */
  width: 220px;
}
```

```javascript
import FloatSidebar from 'float-sidebar';

const sidebar  = document.querySelector('.sidebar');
const relative = document.querySelector('.content');

const floatSidebar = FloatSidebar({
  sidebar,
  relative,
  topSpacing: 20,
  bottomSpacing: 20
});

// ...

floatSidebar.forceUpdate();

// ...

floatSidebar.destroy();
```

## Options

#### sidebar

Type: `Element`<br/>
Required

The sidebar element

#### relative

Type: `Element`<br/>
Required

The sidebar relative element, e.g. a main content

#### viewport

Type: `Element`<br/>
Defaults: `window`

The viewport element

#### sidebarInner

Type: `Element`<br/>
Defaults: `first element child of sidebar element`

The sidebar inner element

#### topSpacing

Type: `Integer`<br/>
Defaults: `0`

The space from the top of the viewport. It is used when the sidebar is fixed.

#### bottomSpacing

Type: `Integer`<br/>
Defaults: `0`

The space from the bottom of the viewport. It is used when the sidebar is fixed.

## Instance API

#### forceUpdate()

Recalculates all the dimensions and finally updates the position of the sidebar.

#### destroy()

Deactivates listeners.

## License

FloatSidebar.js is released under the MIT license.

Author Sergey Vinogradov
