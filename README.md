advancedGrid
============

A Grid-System for the LessCSS preprocessor with multiple options that other systems lack of.
****
How to use
----
### 1. Setting it up
1. Simply drop the grid.less file to your other less-Files.
2. Import it in your less-Stylesheet that will get compiled.
3. Apply the functions on your elements!

### 2. Rows
You will want to choose a row when building a wrapper element that is not floated.
For Example: The container of your website should be a row since it does not require to be floated. Furthermore there is a clearfix applied on it to prevent floatet elements (likely children of the row) from unwanted behaviour. The Clearfix used is the [Micro-Clearfix by Nicolas Gallagher](http://nicolasgallagher.com/micro-clearfix-hack/).

Its basic syntax is: 
``` css
.row(usedColumns,ColumnsInTotal,totalMarginInPercent);
```

**Note: the margin will default to 2%, which means 1% to each side. The Columns in total will default to 12.**

#### Examples:

If your container would have its id set to  "container" like 
```html 
<div id="container"></div>
```
You have to do the following in your less-File:
``` css
#container {
	.row(12);
}
```
	
Since this grid consists of 12 columns per default, your container will be styled to have a width of 98% and a margin of 1% to each, left and right.
If you want the element to have other proportions you can set the other - optional - parameters.
``` css 
#container {
	.row(3,12,0)
} 
```
This will give the element a width of 25% an no margin.

### 3. Column
You will want to use the column function when setting widths of Elements that need to be floated. For example if you want to add a Sidebar, or even two on your page.

Its basic syntax is: 
``` css 
.column(usedColumns,ColumnsInTotal,floatDirection,totalMarginInPercent); 
``` 

Again, only the first value is required. All the others are optional.

**Note: the margin will default to 2%, which means 1% to each side. The Columns in total will default to 12. The floatDirection will default to left.**

#### Examples:
		
##### Basic Scenario
If you want to set up a simple two-Column page, you only need to create two elements.

``` html
<sidebar></sidebar>
<main></main>
```

In your CSS-Code you need to do the following, to have a 2-Column-Sidebar and a 10 Column Main-Content

``` css
sidebar {
	.column(2);
}
main {
	.column(10);
}
```
##### Advanced Scenarios
If you would like to have a Sidebar that is a quarter of your page and a Content that is three quarters of your page you would do the following in your CSS:

``` css
sidebar {
	.column(1,4);
}
main {
	.column(3,4);
}
```
##### Even more Advanced Scenarios
If you would like to have a Sidebar without any margin that is 2 fifths of the page and a Content that is 3 fifths of the page and floated right you would do the following:

``` css
sidebar {
	.column(2,5,left,0);
}
main {
	.column(3,5,right);
}
```
### 4. Further functions
#### Push & Pull
With push and pull you can set a specific margin to either left (push) or right (pull).

The Basic Syntax is: 
``` css
.push(columnsUsed,columnsInTotal); 
``` 
(pull works exactly the same)

**Note: both parameters are optional. columnsUsed will default to one and columnsInTotal will default to 12.**

##### Example
If you want an element to have a margin of 2 eighths to the left, you would do this:

``` css
#anyElement {
	.push(2,8);
}
``` 
#### Width
If you want - for any reason - to reset the width at a later point in your code, you can do this with the width function.
You do wonder why this is needed? Well, you dont want to rewrite everything the .column-Function sets. Furthermore, the width has to be serverd as !important when overwriting.

Its Basic Syntax is: 
``` css
.width(usedColumns,ColumnsInTotal,totalMarginInPercent);
```

You might also wonder why there is a totalMargin set. This is because the margin has to be substrated from the width. And since you can set a custom margin in the column function, you have to be able to do this over here. 
 		
