# Mathy Margins

## Overview

Mathy Margins is a small CSS “framework” (set of utilitiy classes and custom properties) that handles inline layout within a block container. You can use it to easily create layout breakouts, edge-to-edge content, and more.

[Demo](https://codepen.io/noleli/pen/bGyWJaY)

Each direct child of a container with the class `mm-container` becomes a row, and each row has a maximum width (defaults to `50rem`) and can be justified to the start, center (default), or end of the container. In addition to a maximum width, a row also has a configurable gutter (default `16px`) and outset (default 0). The gutter is the margin against the edge of the conatiner, and the outset is how far beyond the specified maximum row width the row extends.

By default, an item occupies an entire row, but you can limit its width. If you do, an item can also be aligned to the start, center, or end of a row.

## API

### Classes for containers

- `mm-container`: makes this element a conatiner and all direct children into rows/items.\
  Rows default to being justified center within the conatiner and items default to being justified center within a row.
- `mm-rows-start`: justifies rows to conatiner start
- `mm-rows-end`: justifies rows to container end
- `mm-items-start`: justifies items to row start
- `mm-items-end`: justifies items to row end

### Custom properties for containers

- `--mm-default-row-max-size`: sets the maximum row size (default `50rem`)
- `--mm-default-gutter`: sets the default start and end gutter (default `16px`)
- `--mm-default-gutter-start`: sets the default start gutter (default `16px`)
- `--mm-default-gutter-end`: sets the default end gutter (default `16px`)

### Classes for rows/items

- `mm-row-start`: justifies this row to container start
- `mm-row-end`: justifies this row to container end
- `mm-row-center`: justifies this row to container center
- `mm-item-start`: justifies this item to row start
- `mm-item-end`: justifies this item to row end
- `mm-item-center`: justifies this item to row center

### Custom properties for rows/items

- `--mm-row-max-size`: sets the maximum size of this row
- `--mm-gutter`: sets the start and end gutter for this row
- `--mm-gutter-start`: sets the start gutter for this row
- `--mm-gutter-end`: sets the end gutter for this row
- `--mm-outset`: sets the start and end outset for this row
- `--mm-outset-start`: sets the start outset for this row
- `--mm-outset-end`: sets the end outset for this row
- `--mm-item-max-size`: sets the maximum size of this item
- `--mm-row-size`: returns the current size of this row.\
  **This is intended to be read only** so you can size items relative to current row size (in addition to max row size). For example,\
  `--mm-item-max-size: calc(var(--mm-row-size) / 3);`\
  will set an item size to 1/3 the row size.

### Utility classes

- `mm-breakout`: add to a row/item to make it break out. Configurable with `--mm-breakout-frac` (default .04), which is the fraction of the max row size to break out by.
- `mm-edge-to-edge`: add to a row/item to make it go edge to edge in the container

## Notes/known issues

- When setting values for gutters and outsets to 0, you must include a unit. `0px` instead of `0`.
- Until we get [`calc-size()`](https://github.com/w3c/csswg-drafts/blob/main/css-values-5/calc-size-explainer.md) at some point in the future, it will unfortunately not be possible to set item sizes to keywords like `fit-content`. (In fact `calc-size()` and being able to use `justify-items` and `justify-self` in block layouts will greatly improve much about this project.)
