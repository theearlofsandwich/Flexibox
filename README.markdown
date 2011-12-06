Flexibox - A flexible grid system using Compass
===============================================

Introduction
------------

Want your designers to work to your grid system?
Want to stop the "I've just budged this panel over because it looks better" conversations?

Well you can always dream. But in the meantime there's Flexibox.

Flexibox takes the principles of the popular Blueprint grid system and bolts on some
useful functionality to get round the 'not-quite-a-grid' designs we often get.

Flexibox allows you to use a grid where possible, add margins to match your design without
compromising the grid and add padding without breaking your grid sizes.

You can even use an image to automatically create grid panels.


Requirements
------------

[Compass](http://compass-style.org/)


Usage
-----

Include _flexibox.scss in your compass project.

    @import "flexibox";

### Available classes

.clearfix - Apply to parent elements to clear floats correctly.

.fbox-spacer - Add to an `<hr>` to create a break between vertical columns. Includes a small amount of space.

.fbox-nospacer - Add to an `<hr>` to create a break between vertical columns. Breaks without any space.


### fbox-container

Create a centered container to hold the grid. This defaults to 950px wide, 24 columns with
10px gutter.

    @include fbox-container();

Optional parameters:

- $show-grid: true or false - creates a viewable grid in Firefox/Safari as a background.
- $width: Width of container in pixels.
- $columns: Number of columns
- $gutter: Width of gutter (column margins) in pixels
- $pad-sides: true or false - If pad-sides is true, include the padding width in $width (so 970px rather than 950px)

    @include fbox-container($show-grid: true, $width: 950px, $columns: 24, $gutter: 10px);

### fbox-grid

Create a grid column. The goal is always to fit into the grid, so margins, padding, prepend, append
will always end at a valid grid position.

    @include fbox-grid($columns);

Required parameter:

- $size: Number of columns to span.

Optional parameters:

- $padding: Padding in pixels. Pads inside column a bit like old box model.
- $margin: Margin to apply to column. Applies inside column as well so does not break out from grid.
Use normal $margin css shorthand.
- $margin-left: Left margin in pixels (overrides $margin left hand setting)
- $margin-right: Just a right margin (overrides $margin right hand setting)
- $height: A fixed height in pixels.
- $append: Append a number of spans after the column.
- $prepend: Prepend a number of spans before the column.
- $last: Remove any right hand margin for columns that reach the right hand side of the container.

    @include fbox-grid(5);
    @include fbox-grid(24, $last: true);
    @include fbox-grid(7, $prepend: 1, $append: 2, $margin: 0 10px, $padding: 5px) ;

### fbox-flex

Creates a floated column that does not respect the grid.

    @include fbox-flex($size);

Required parameter:

- $size: A width and optionally height in pixels to span. Use css shorthand.

Optional parameters:

- $padding: Padding in pixels. Pads inside column a bit like old box model.
- $margin: Margin to apply to column. Applies inside column as well so does not break out from grid.
Use normal $margin css shorthand.
- $margin-left: Left margin in pixels (overrides $margin left hand setting)
- $margin-right: Just a right margin (overrides $margin right hand setting)
- $width: A width in pixels (overrides $size)
- $height: A height in pixels (overrides $size)

    @include fbox-flex(200px);
    @include fbox-flex(200px 150px);
    @include fbox-flex(200px, $margin: 10px 5px 15px 15px);

### fbox-grid-image

Use an image to create a column automatically based on the image dimensions. Handy for panels.
Automatically adds the image in as the background.
Respects the grid so will add margin as necessary to reach the next grid column.
The image must reside in the images directory specified in your Compass config file.

    @include fbox-grid-image("image.jpg");
    @include fbox-grid-image("image.jpg", $padding: 10px);

Required parameter:

- $image: An image filename.

Optional parameters:

- $padding: Padding in pixels. Pads inside column a bit like old box model.
- $fixed-height: true or false. If set to true will set the column height to the image height.
- $append: Append a number of spans after the column.
- $prepend: Prepend a number of spans before the column.
- $last: Remove any right hand margin for columns that reach the right hand side of the container.

### fbox-image

Use an image to create a floated column that does not respect the grid.
Automatically adds the image in as the background.

    @include fbox-image("image.jpg");

Required parameter:

- $image: An image filename.

Optional parameters:

- $padding: Padding in pixels. Pads inside column a bit like old box model.
- $margin: Margin to apply to column. Applies margin OUTSIDE the image.
Use normal $margin css shorthand.
- $margin-left: Left margin in pixels (overrides $margin left hand setting)
- $margin-right: Just a right margin (overrides $margin right hand setting)
- $fixed-height: true or false. If set to true will set the column height to the image height.

    @include fbox-image("image.jpg");
