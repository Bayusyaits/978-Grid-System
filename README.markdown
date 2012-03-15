978 Grid System
===============

This repository contains a collection of design templates and code to quickly get you up and running 
with the 978 (and companion) grid systems. As we get free time, we will continue to improve this 
collection over time. We encourage you to contribute as well.

The 978 and companion grid systems are brought to you by [Brothers Roloff](http://www.brothersroloff.com/).  
Learn more about 978 for web design: <http://978.gs/>

#### Additional Contributors 

- [Janne Passi](http://www.passiripatti.com/) - OmniGraffle
- [Eduardo Perez](http://www.eperez.net/) - Photoshop Actions
- [Pieter van Leeuwen](http://www.acato.nl/) - Fireworks


CSS Usage
---------

Note from the author: We do NOT encourage the use of CSS frameworks. HTML, when written correctly, 
should semantically describe your CONTENT [as much that is realistically feasible]. Mucking up your 
markup with classes for layout/grid is not considered best practice. 

With that being said, however, CSS frameworks can make rapid prototyping a breeze. They can let 
someone of any skill-set quickly mock up a basic look and feel of a website. In some ways, it may 
even be faster than doing it in Photoshop.

Therefore, we are providing this framework for rapid prototype use (and for those not comfortable 
writing their own CSS). We still strongly encourage you to write your own CSS on your own projects.

### Include the CSS framework in your page ###

	<link rel="stylesheet" href="978.css">

Note: Do not include the "demo-files" CSS, as it is for demonstration purposes only.


### Wrap your layout in a container element ###

	<div class="layout-978">


### Add rows and columns to achieve your desired layout ###

978 is a 12 column grid system. Therefore, you can add as many columns to a row as long as they 
total the number 12. Be sure to total the appropriate number of columns when using the companion 
grid systems CSS.

	<div class="row">
		<div class="col2">138px</div>
		<div class="col10">810px</div>
		<div class="row-end">&nbsp;</div>
	</div>

Don't forget to add a "row-end" element immediately after your last column of a row. Placing the 
ending element here will allow you to apply a background image or color to each row separately and 
it will grow/repeat vertically to the height of your longest column.

Use with SASS / Compass
---------

To use with SASS or Compass, first import one of the supplied styles. Copy the needed sass/scss file to your stylesheet directory and import it:

	@import "978gs";

### Layouts

By default, it compiles the 978px layout, but you can switch to the other layouts by declaring the **$layoutwidth** before the import.

	$layoutwidth : 1378;
	@import "978gs";

### Grid Mixin

You can assign the grid mixin to the css by including `grid($column_width,$first)` where `$column_width` is the number of columns you'd like to use and `$first` is a boolean whether the assigned block is the first column or not. Here's an example:

	.first {
		@include grid(1); }
	.second {
		@include grid(2,true); }

will render to :
	
	.first {
		float: left;
		width : 54px;
		margin-left: 30px; }
	.second {
		float: left;
		width: 138px;
		margin-left: 0; }

As you can see, the default value for `$first` is set to `false`, so you can leave it most of the time.

### $printlayout

By default, the imported SASS/SCSS file is not going to print all of those `.col1, .col2, .col3…` class styling. We encouraged you to just stick to the grid mixin. However, if you want to print those styles, you can change the `$printlayout` value before importing:

	$printlayout : true;
	@import "978gs";

..and it will generate all the classes styles.