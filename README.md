# What the Flexbox?!

![WTF](https://i.imgur.com/4n3DeMi.png)

By default, when the parent container is set to `display: flex`, each child gets turned into a flex item.

We've got two axis: the main axis and the cross axis.

## flex-direction: row

```
flex-direction: row;
main axis --> X from LEFT to RIGHT
cross axis --> Y from TOP to BOTTOM

items on the horizontal (main) axis are laid out from left to right
```

When `flex-direction: row`, each flex item has its width determined by its own content (i.e. each flex item will be as wide as its content is). The height of each child, however, matches that of the container (each child stretches as high as the container). This is b/c by default `align-items: stretch` within `.container`.

![](./screenshots/1.jpg)

The above layout corresponds to the following styles:

```css
.container {
  display:flex;
  border: 10px solid goldenrod;
  height: 100vh;
}
```

When removing the fixed height, the container is as tall as its content (like a regular div):

![](./screenshots/2.jpg)

## flex-direction: column

```
flex-direction: column;
main axis --> Y from TOP to BOTTOM
cross axis --> X from LEFT to RIGHT
```

When `flex-direction: column`, each flex item has its height determined by its content whereas it will be as wide as the container element is. In this case, our `container` element will behave like a block element does.

![](./screenshots/3.jpg)

```css
.container {
  border: 10px solid goldenrod;
  display: flex;
  flex-direction: column;
}
```

## Reversing the direction of the main axis

And yes, the direction is important b/c you can then reverse it:

```
flex-direction: row-reverse;
main axis --> X from RIGHT to LEFT
```

![](./screenshots/4.jpg)

```
flex-direction: column-reverse;
main axis --> Y from BOTTOM to TOP
```

![](./screenshots/5.jpg)

## Setting the width of the flex items (children of container)

```css
.container {
  border: 10px solid goldenrod;
  display: flex;
}

.box {
  width: 300px;
}
```

The nature of flexbox is that it's gonna try to work with the widths that you give it, but if it just doesn't work out it's gonna evenly distribute the available space.

![](./screenshots/6.jpg)

^ Clearly the width of the screen is not 3000px (300px * 10 elements).

## Wrap

![](./screenshots/7.jpg)

```css
.container {
  border: 10px solid goldenrod;
  display: flex;
  flex-wrap: wrap; /* <-- */
}

.box {
  width: 300px;
}
```

If we now set the container to `100vh` the remaining vertical space gets evenly distributed among the children (flex items). We are not giving each child a fixed height, it's being set automatically based on the container height.

![](./screenshots/8.jpg)

```css
.container {
  border: 10px solid goldenrod;
  display: flex;
  flex-wrap: wrap;
  height: 100vh; /* <-- */
}

.box {
  width: 300px;
}
```

## Reversing the cross axis

![](./screenshots/9.jpg)

```css
.container {
  border: 10px solid goldenrod;
  display: flex;
  flex-wrap: wrap-reverse; /* <-- */
  height: 100vh;
}

.box {
  width: 300px;
}
```

For a `flex-direction: row`, setting `flex-wrap: wrap-reverse` makes the cross axis go from bottom to top (instead of laying out flex items from top to bottom).

My items are still starting at the left hand side, from left to right (b/c of `flex-direction: row`) but they start at the bottom and work their way up.

## flex: 1

![](./screenshots/10.jpg)

Take all the space available and evenly distribute it among the flex items (children).

This property you set on the children, not on the container.

## Changing the order of the flex items

![](./screenshots/11.jpg)

By default all items are set to `order: 0` meaning that if you give any item an `order: 1` will be place after all of the default ordered items.

The `order` property also takes negative integer values.

## Alignment

* Along the main axis with `justify-content`
* Along the cross axis with `align-items` (the container must have some sort of height defined)
* Split the extra space on the cross axis with `align-content` (the container must be wrapping items)

Particularly interesting use case: `align-items: baseline`

![](./screenshots/12.jpg)

## `align-items: center` vs `align-content: center`

`align-items: center` handles the cross position of the flex items:

![](./screenshots/13.jpg)

`align-content: center` handles the extra space, not the items:

![](./screenshots/14.jpg)

## Defaults:

```css
/* Container */
flex-direction: row
flex-wrap: nowrap;
justify-content: flex-start;
align-items: stretch;
align-content: stretch;

/* Children */
order: 0;
```
