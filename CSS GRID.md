# A Complete Guide to Grid

CSS Grid Layout (aka “Grid”), is a two-dimensional grid-based layout system that aims to do nothing less than completely change the way we design grid-based user interfaces. CSS has always been used to lay out our web pages, but it’s never done a very good job of it. First, we used tables, then floats, positioning and inline-block, but all of these methods were essentially hacks and left out a lot of important functionality (vertical centering, for instance). Flexbox helped out, but it’s intended for simpler one-dimensional layouts, not complex two-dimensional ones (Flexbox and Grid actually work very well together). Grid is the very first CSS module created specifically to solve the layout problems we’ve all been hacking our way around for as long as we’ve been making websites.

There are two primary things that inspired me to create this guide. The first is Rachel Andrew’s awesome book, Get Ready for CSS Grid Layout. It’s a thorough, clear introduction to Grid and is the basis of this entire article. I highly encourage you to buy it and read it. My other big inspiration is Chris Coyier’s “A Complete Guide to Flexbox” which has been my go-to resource for everything flexbox. It’s helped a ton of people, evident by the fact that it’s the top result when you Google “flexbox.” You’ll notice many similarities between his post and mine, because why not steal from the best?

My intention with this guide is to present the Grid concepts as they exist in the very latest version of the specification. So I won’t be covering the out of date Internet Explorer syntax, and I’ll do my best to update this guide regularly as the spec matures.


## Basics and browser support
As of March 2017, most browsers shipped native, unprefixed support for CSS Grid: Chrome (including on Android), Firefox, Safari (including on iOS), and Opera. Internet Explorer 10 and 11 on the other hand support it, but it’s an old implementation with an outdated syntax. The time to build with grid is now!

To get started you have to define a container element as a grid with display: grid, set the column and row sizes with grid-template-columns and grid-template-rows, and then place its child elements into the grid with grid-column and grid-row. Similarly to flexbox, the source order of the grid items doesn’t matter. Your CSS can place them in any order, which makes it super easy to rearrange your grid with media queries. Imagine defining the layout of your entire page, and then completely rearranging it to accommodate a different screen width all with only a couple lines of CSS. Grid is one of the most powerful CSS modules ever introduced.
![Capture20](https://user-images.githubusercontent.com/79080942/115446875-7de8e400-a220-11eb-9327-c91ea03e0b0e.PNG)

### Important terminology
Before diving into the concepts of Grid it’s important to understand the terminology. Since the terms involved here are all kinda conceptually similar, it’s easy to confuse them with one another if you don’t first memorize their meanings defined by the Grid specification. But don’t worry, there aren’t many of them.

### Grid Container
The element on which display: grid is applied. It’s the direct parent of all the grid items. In this example container is the grid container.

<div class="container">
  <div class="item item-1"> </div>
  <div class="item item-2"> </div>
  <div class="item item-3"> </div>
</div>

Grid Line
The dividing lines that make up the structure of the grid. They can be either vertical (“column grid lines”) or horizontal (“row grid lines”) and reside on either side of a row or column. Here the yellow line is an example of a column grid line.

Grid Track
The space between two adjacent grid lines. You can think of them like the columns or rows of the grid. Here’s the grid track between the second and third row grid lines.

Grid Area
The total space surrounded by four grid lines. A grid area may be composed of any number of grid cells. Here’s the grid area between row grid lines 1 and 3, and column grid lines 1 and 3.

Grid Item
The children (i.e. direct descendants) of the grid container. Here the item elements are grid items, but sub-item isn’t.

Grid Cell
The space between two adjacent row and two adjacent column grid lines. It’s a single “unit” of the grid. Here’s the grid cell between row grid lines 1 and 2, and column grid lines 2 and 3.

Grid properties
Table of contents
Properties for the Grid container
display
grid-template-columns
grid-template-rows
grid-template-areas
grid-template
grid-column-gap
grid-row-gap
grid-gap
justify-items
align-items
place-items
justify-content
align-content
place-content
grid-auto-columns
grid-auto-rows
grid-auto-flow
grid
Properties for Grid items
grid-column-start
grid-column-end
grid-row-start
grid-row-end
grid-column
grid-row
grid-area
justify-self
align-self
place-self


justify-items
Aligns grid items along the inline (row) axis (as opposed to align-items which aligns along the block (column) axis). This value applies to all grid items inside the container.

Values:

start – aligns items to be flush with the start edge of their cell
end – aligns items to be flush with the end edge of their cell
center – aligns items in the center of their cell
stretch – fills the whole width of the cell (this is the default)
.container {
  justify-items: start | end | center | stretch;
}
Examples:

.container {
  justify-items: start;
}
Example of justify-items set to start
.container {
  justify-items: end;
}
Example of justify-items set to end
.container {
  justify-items: center;
}
Example of justify-items set to center
.container {
  justify-items: stretch;
}
Example of justify-items set to stretch
This behavior can also be set on individual grid items via the justify-self property.

align-items
Aligns grid items along the block (column) axis (as opposed to justify-items which aligns along the inline (row) axis). This value applies to all grid items inside the container.

Values:

start – aligns items to be flush with the start edge of their cell
end – aligns items to be flush with the end edge of their cell
center – aligns items in the center of their cell
stretch – fills the whole height of the cell (this is the default)
.container {
  align-items: start | end | center | stretch;
}
Examples:

.container {
  align-items: start;
}
Example of align-items set to start
.container {
  align-items: end;
}
Example of align-items set to end
.container {
  align-items: center;
}
Example of align-items set to center
.container {
  align-items: stretch;
}
Example of align-items set to stretch
This behavior can also be set on individual grid items via the align-self property.


place-items
place-items sets both the align-items and justify-items properties in a single declaration.

Values:

<align-items> / <justify-items> – The first value sets align-items, the second value justify-items. If the second value is omitted, the first value is assigned to both properties.
All major browsers except Edge support the place-items shorthand property.

For more details, see align-items and justify-items.

justify-content
Sometimes the total size of your grid might be less than the size of its grid container. This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the alignment of the grid within the grid container. This property aligns the grid along the inline (row) axis (as opposed to align-content which aligns the grid along the block (column) axis).

Values:

start – aligns the grid to be flush with the start edge of the grid container
end – aligns the grid to be flush with the end edge of the grid container
center – aligns the grid in the center of the grid container
stretch – resizes the grid items to allow the grid to fill the full width of the grid container
space-around - places an even amount of space between each grid item, with half-sized spaces on the far ends
space-between – places an even amount of space between each grid item, with no space at the far ends
space-evenly – places an even amount of space between each grid item, including the far ends
.container {
  justify-content: start | end | center | stretch | space-around | space-between | space-evenly;    
}
Examples:

.container {
  justify-content: start;
}
Example of justify-content set to start
.container {
  justify-content: end;    
}
Example of justify-content set to end
.container {
  justify-content: center;    
}
Example of justify-content set to center
.container {
  justify-content: stretch;    
}
Example of justify-content set to stretch
.container {
  justify-content: space-around;    
}
Example of justify-content set to space-around
.container {
  justify-content: space-between;    
}
Example of justify-content set to space-between
.container {
  justify-content: space-evenly;    
}
Example of justify-content set to space-evenly
align-content
Sometimes the total size of your grid might be less than the size of its grid container. This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the alignment of the grid within the grid container. This property aligns the grid along the block (column) axis (as opposed to justify-content which aligns the grid along the inline (row) axis).

Values:

start – aligns the grid to be flush with the start edge of the grid container
end – aligns the grid to be flush with the end edge of the grid container
center – aligns the grid in the center of the grid container
stretch – resizes the grid items to allow the grid to fill the full height of the grid container
space-around – places an even amount of space between each grid item, with half-sized spaces on the far ends
space-between – places an even amount of space between each grid item, with no space at the far ends
space-evenly – places an even amount of space between each grid item, including the far ends
.container {
  align-content: start | end | center | stretch | space-around | space-between | space-evenly;    
}
Examples:

.container {
  align-content: start;    
}
Example of align-content set to start
.container {
  align-content: end;    
}
Example of align-content set to end
.container {
  align-content: center;    
}
Example of align-content set to center
.container {
  align-content: stretch;    
}
Example of align-content set to stretch
.container {
  align-content: space-around;    
}
Example of align-content set to space-around
.container {
  align-content: space-between;    
}
Example of align-content set to space-between
.container {
  align-content: space-evenly;    
}
Example of align-content set to space-evenly
place-content
place-content sets both the align-content and justify-content properties in a single declaration.

Values:

<align-content> / <justify-content> – The first value sets align-content, the second value justify-content. If the second value is omitted, the first value is assigned to both properties.
All major browsers except Edge support the place-content shorthand property.

For more details, see align-content and justify-content.

grid-auto-columns
grid-auto-rows
Specifies the size of any auto-generated grid tracks (aka implicit grid tracks). Implicit tracks get created when there are more grid items than cells in the grid or when a grid item is placed outside of the explicit grid. (see The Difference Between Explicit and Implicit Grids)

Values:

<track-size> – can be a length, a percentage, or a fraction of the free space in the grid (using the fr unit)
.container {
  grid-auto-columns: <track-size> ...;
  grid-auto-rows: <track-size> ...;
}
To illustrate how implicit grid tracks get created, think about this:

.container {
  grid-template-columns: 60px 60px;
  grid-template-rows: 90px 90px;
}
Example of 2x2 grid
This creates a 2 x 2 grid.

But now imagine you use grid-column and grid-row to position your grid items like this:

.item-a {
  grid-column: 1 / 2;
  grid-row: 2 / 3;
}
.item-b {
  grid-column: 5 / 6;
  grid-row: 2 / 3;
}
Example of implicit tracks
We told .item-b to start on column line 5 and end at column line 6, but we never defined a column line 5 or 6. Because we referenced lines that don’t exist, implicit tracks with widths of 0 are created to fill in the gaps. We can use grid-auto-columns and grid-auto-rows to specify the widths of these implicit tracks:

.container {
  grid-auto-columns: 60px;
}
grid-auto-columns-rows
grid-auto-flow
If you have grid items that you don’t explicitly place on the grid, the auto-placement algorithm kicks in to automatically place the items. This property controls how the auto-placement algorithm works.

Values:

row – tells the auto-placement algorithm to fill in each row in turn, adding new rows as necessary (default)
column – tells the auto-placement algorithm to fill in each column in turn, adding new columns as necessary
dense – tells the auto-placement algorithm to attempt to fill in holes earlier in the grid if smaller items come up later
.container {
  grid-auto-flow: row | column | row dense | column dense;
}
Note that dense only changes the visual order of your items and might cause them to appear out of order, which is bad for accessibility.

Examples:

Consider this HTML:

<section class="container">
  <div class="item-a">item-a</div>
  <div class="item-b">item-b</div>
  <div class="item-c">item-c</div>
  <div class="item-d">item-d</div>
  <div class="item-e">item-e</div>
</section>
You define a grid with five columns and two rows, and set grid-auto-flow to row (which is also the default):

.container {
  display: grid;
  grid-template-columns: 60px 60px 60px 60px 60px;
  grid-template-rows: 30px 30px;
  grid-auto-flow: row;
}
When placing the items on the grid, you only specify spots for two of them:

.item-a {
  grid-column: 1;
  grid-row: 1 / 3;
}
.item-e {
  grid-column: 5;
  grid-row: 1 / 3;
}
Because we set grid-auto-flow to row, our grid will look like this. Notice how the three items we didn’t place (item-b, item-c and item-d) flow across the available rows:

Example of grid-auto-flow set to row
If we instead set grid-auto-flow to column, item-b, item-c and item-d flow down the columns:

.container {
  display: grid;
  grid-template-columns: 60px 60px 60px 60px 60px;
  grid-template-rows: 30px 30px;
  grid-auto-flow: column;
}
Example of grid-auto-flow set to column
grid
A shorthand for setting all of the following properties in a single declaration: grid-template-rows, grid-template-columns, grid-template-areas, grid-auto-rows, grid-auto-columns, and grid-auto-flow (Note: You can only specify the explicit or the implicit grid properties in a single grid declaration).

Values:

none – sets all sub-properties to their initial values.
<grid-template> – works the same as the grid-template shorthand.
<grid-template-rows> / [ auto-flow && dense? ] <grid-auto-columns>? – sets grid-template-rows to the specified value. If the auto-flow keyword is to the right of the slash, it sets grid-auto-flow to column. If the dense keyword is specified additionally, the auto-placement algorithm uses a “dense” packing algorithm. If grid-auto-columns is omitted, it is set to auto.
[ auto-flow && dense? ] <grid-auto-rows>? / <grid-template-columns> – sets grid-template-columns to the specified value. If the auto-flow keyword is to the left of the slash, it sets grid-auto-flow to row. If the dense keyword is specified additionally, the auto-placement algorithm uses a “dense” packing algorithm. If grid-auto-rows is omitted, it is set to auto.
Examples:

The following two code blocks are equivalent:

.container {
  grid: 100px 300px / 3fr 1fr;
}

.container {
  grid-template-rows: 100px 300px;
  grid-template-columns: 3fr 1fr;
}
The following two code blocks are equivalent:

.container {
  grid: auto-flow / 200px 1fr;
}

.container {
  grid-auto-flow: row;
  grid-template-columns: 200px 1fr;
}
The following two code blocks are equivalent:

.container {
  grid: auto-flow dense 100px / 1fr 2fr;
}

.container {
  grid-auto-flow: row dense;
  grid-auto-rows: 100px;
  grid-template-columns: 1fr 2fr;
}
And the following two code blocks are equivalent:

.container {
  grid: 100px 300px / auto-flow 200px;
}

.container {
  grid-template-rows: 100px 300px;
  grid-auto-flow: column;
  grid-auto-columns: 200px;
}
It also accepts a more complex but quite handy syntax for setting everything at once. You specify grid-template-areas, grid-template-rows and grid-template-columns, and all the other sub-properties are set to their initial values. What you’re doing is specifying the line names and track sizes inline with their respective grid areas. This is easiest to describe with an example:

.container {
  grid: [row1-start] "header header header" 1fr [row1-end]
        [row2-start] "footer footer footer" 25px [row2-end]
        / auto 50px auto;
}
That’s equivalent to this:

.container {
  grid-template-areas: 
    "header header header"
    "footer footer footer";
  grid-template-rows: [row1-start] 1fr [row1-end row2-start] 25px [row2-end];
  grid-template-columns: auto 50px auto;    
}


grid-column-start
grid-column-end
grid-row-start
grid-row-end
Determines a grid item’s location within the grid by referring to specific grid lines. grid-column-start/grid-row-start is the line where the item begins, and grid-column-end/grid-row-end is the line where the item ends.

Values:

<line> – can be a number to refer to a numbered grid line, or a name to refer to a named grid line
span <number> - the item will span across the provided number of grid tracks
span <name> – the item will span across until it hits the next line with the provided name
auto – indicates auto-placement, an automatic span, or a default span of one
.item {
  grid-column-start: <number> | <name> | span <number> | span <name> | auto;
  grid-column-end: <number> | <name> | span <number> | span <name> | auto;
  grid-row-start: <number> | <name> | span <number> | span <name> | auto;
  grid-row-end: <number> | <name> | span <number> | span <name> | auto;
}
Examples:

.item-a {
  grid-column-start: 2;
  grid-column-end: five;
  grid-row-start: row1-start;
  grid-row-end: 3;
}
Example of grid-row/column-start/end
.item-b {
  grid-column-start: 1;
  grid-column-end: span col4-start;
  grid-row-start: 2;
  grid-row-end: span 2;
}
Example of grid-row/column-start/end
If no grid-column-end/grid-row-end is declared, the item will span 1 track by default.

Items can overlap each other. You can use z-index to control their stacking order.

grid-column
grid-row
Shorthand for grid-column-start + grid-column-end, and grid-row-start + grid-row-end, respectively.

Values:

<start-line> / <end-line> – each one accepts all the same values as the longhand version, including span
.item {
  grid-column: <start-line> / <end-line> | <start-line> / span <value>;
  grid-row: <start-line> / <end-line> | <start-line> / span <value>;
}
Example:

.item-c {
  grid-column: 3 / span 2;
  grid-row: third-line / 4;
}
Example of grid-column/grid-row
If no end line value is declared, the item will span 1 track by default.

grid-area
Gives an item a name so that it can be referenced by a template created with the grid-template-areas property. Alternatively, this property can be used as an even shorter shorthand for grid-row-start + grid-column-start + grid-row-end + grid-column-end.

Values:

<name> – a name of your choosing
<row-start> / <column-start> / <row-end> / <column-end> – can be numbers or named lines
.item {
  grid-area: <name> | <row-start> / <column-start> / <row-end> / <column-end>;
}
Examples:

As a way to assign a name to the item:

.item-d {
  grid-area: header;
}
As the short-shorthand for grid-row-start + grid-column-start + grid-row-end + grid-column-end:

.item-d {
  grid-area: 1 / col4-start / last-line / 6;
}
Example of grid-area
justify-self
Aligns a grid item inside a cell along the inline (row) axis (as opposed to align-self which aligns along the block (column) axis). This value applies to a grid item inside a single cell.

Values:

start – aligns the grid item to be flush with the start edge of the cell
end – aligns the grid item to be flush with the end edge of the cell
center – aligns the grid item in the center of the cell
stretch – fills the whole width of the cell (this is the default)
.item {
  justify-self: start | end | center | stretch;
}
Examples:

.item-a {
  justify-self: start;
}
Example of justify-self set to start
.item-a {
  justify-self: end;
}
alt="Example
.item-a {
  justify-self: center;
}
Example of justify-self set to center
.item-a {
  justify-self: stretch;
}
Example of justify-self set to stretch
To set alignment for all the items in a grid, this behavior can also be set on the grid container via the justify-items property.

align-self
Aligns a grid item inside a cell along the block (column) axis (as opposed to justify-self which aligns along the inline (row) axis). This value applies to the content inside a single grid item.

Values:

start – aligns the grid item to be flush with the start edge of the cell
end – aligns the grid item to be flush with the end edge of the cell
center – aligns the grid item in the center of the cell
stretch – fills the whole height of the cell (this is the default)
.item {
  align-self: start | end | center | stretch;
}
Examples:

.item-a {
  align-self: start;
}
Example of align-self set to start
.item-a {
  align-self: end;
}
Example of align-self set to end
.item-a {
  align-self: center;
}
Example of align-self set to center
.item-a {
  align-self: stretch;
}
Example of align-self set to stretch
To align all the items in a grid, this behavior can also be set on the grid container via the align-items property.

place-self
place-self sets both the align-self and justify-self properties in a single declaration.

Values:

auto – The “default” alignment for the layout mode.
<align-self> / <justify-self> – The first value sets align-self, the second value justify-self. If the second value is omitted, the first value is assigned to both properties.
Examples:

.item-a {
  place-self: center;
}
place self set to center
.item-a {
  place-self: center stretch;
}
place set set to center stretch
All major browsers except Edge support the place-self shorthand property.


