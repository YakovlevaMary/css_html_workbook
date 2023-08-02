# CSS and HTML workbook
This repository was created to reflect the main points of the theory of web development self-study.
> HTML and CSS are not programming languages! HTML - Hypertext Markup Language (язык гипертекстовой разметки). CSS - Cascading Style Sheets (каскадные таблицы стилей).
## 🎀 Table of contents
- [CSS rules](#css-rules)
- [Flow and block model](#flow-and-block-model)
- [Padding and margin shortcut](#padding-and-margin-shortcut)
- [Borders](#borders)
- [Shadows](#shadows)
- [Introduction to JS](#introduction-to-js)
- [Useful links](#useful-links)

## CSS rules
Several classes should be written inside the value of one class attribute separated by a space:  

```bash
<div class="first second"></div>
```

For example, general properties can be specified by a rule on the <code>text</code> class, and unique properties can be specified by an individual <code>special-text</code> class.  

```bash
<p class="text">Composition of the day:</p>
```
```bash
<p class="text special-text">Bonobo, Rhye - Break Apart</p>
```
```bash
.text {
   font-size: 20px;
}
.special-text {
     font-size: 32px;
     color: #FEEB78;
}
```
Through a space, you can specify any number of classes.

## Flow and block model 
Document flow (data flow) in HTML is the order in which elements are displayed on the page. In the usual form, all blocks are displayed in the order in which they are written inside the HTML document.
The browser reads the file code from top to bottom and renders the page in the same way. Therefore, the elements are said to follow each other in a flow.  
Every HTML element has a default display value, depending on what type of element it is.  
There are two display values: **block** and **inline**.
![block_and_inline_elements.png](media/pictures/block_and_inline_elements.png)
### Block-level Elements
A block-level element always starts on a new line, and the browsers automatically add some space (a margin) before and after the element.  
A block-level element always takes up the full width available (stretches out to the left and right as far as it can).  
For example, the <code>div</code>, <code>section</code>, <code>header</code>, <code>h1</code> - <code>h6</code> and <code>p</code> tags, when flowing, take up the entire width of their parent by default. Such elements are conventionally called *block elements*.  
Example:  
<kbd>![block_elements_example.png](media/pictures/block_elements_example.png)</kbd>  
Here are the block-level elements in HTML:
![block_elements_tags.png](media/pictures/block_elements_tags.png)  

Note, that the picture is not a block element, it is displayed with its original dimensions and can go beyond the parent block.

### Inline Elements
An inline element does not start on a new line. It only takes up as much width as necessary.  
If they are in a row, then by default they are all on the same line. They cannot be given a width or height - they ignore sizing through styles.
Example (this is a \<span\> element inside a paragraph):  
<kbd>![inline_elements_example.png](media/pictures/inline_elements_example.png)</kbd>  
Here are the inline elements in HTML:
![inline_elements_tags.png](media/pictures/inline_elements_tags.png)   

### Inline-block Elements
What to do when blocks with certain sizes should follow each other horizontally and not occupy the entire line? You can set the elements of the combined type - block-line.  
On the one hand, they do not take up the entire horizontal, on the other hand, allows to set a width and height on the element via CSS. For example, this is how <img> elements behave. 
The type is overridden by the display property:  

<code>display:block;</code> - *makes the element of block type*  

<code>display: inline;</code> - *makes the element of inline type*  

<code>display: inline-block;</code> - *makes the element of inline-block type*  

![different_types_of_elements.png](media/pictures/different_types_of_elements.png)   
Compared to <code>display: inline</code>, the major difference is that <code>display: inline-block</code> allows to set a width and height on the element.  
Also, with <code>display: inline-block</code>, the top and bottom margins/paddings are respected, but with <code>display: inline</code> they are not.  
Compared to <code>display: block</code>, the major difference is that <code>display: inline-block</code> does not add a line-break after the element, so the element can sit next to other elements.

So, the cards fit in a line, but not close, although the indents between them were not set. You can remove the unexpected gap by assigning some class to the parent element and setting its <code>font-size: 0</code> property in the file.

### Centering elements: margin: auto
The special value <code>auto</code> works with the centering of block elements. It automatically sets the maximum possible horizontal offset. Setting the <code>margin-left</code> and <code>margin-right</code> properties to <code>auto</code> will get the maximum padding on both sides, and the element will be centered on its parent.  
![element_centering.png](media/pictures/element_centering.png)   

**An example using a shortcut**  
Let's put the element in the center of the screen, giving its left anf right margins a value of <code>auto</code>. Let's do this with just one property, the margins above and below can be set to 0:  
```bash
margin: 0 auto;
```

### Centering elements: display: flex
Let's look at a way to automatically center an element. For the <code>display</code> property, in addition to <code>block</code>, <code>inline</code>, and <code>inline-block</code>, there is a special <code>flex</code> value:
```bash
display:flex;
```
![display_flex_property.png](media/pictures/display_flex_property.png)   
An element with this property becomes a flex container. For example, inside it <code>margin: auto</code> works not only horizontally.
## Padding and margin shortcut

<b>Margin</b> is the space around the element's border outside.  
Unlike outer margins, <b>padding</b> is located inside the element and creates free space between the border and the content. The word "padding" is taken from tailors and means a shoulder pad - a pad between the fabric of the jacket and the shoulder.

The model of any element looks like this:

-content with dimensions width (ширина) and height (высота);

-margins (внешние отступы, поля);

-padding (внутренние отступы);

-borders (границы).

![padding_margin_edges.png](media/pictures/padding_margin_edges.png)

When they say “element 200 by 300”, they mean the size of the content up to and including the border, margin is not included here.


![padding_margin_shortcut.png](media/pictures/padding_margin_shortcut.png)

Placement direction - ***clockwise***, starting from the top.  
*with 4 values*: each side has its own value  
```bash
padding: 20px 15px 30px 15px;
```
*with 3 values*: top - 10px, sides - 20px, bottom - 30px  
```bash
padding: 10px 20px 30px;
```
*with 2 values*: top and bottom - 10px, sides - 20px  
```bash
padding: 10px 20px;
```
*with 1 value*: 10px on all sides  
```bash
padding: 10px;
```
This approach works for both margin and padding.

## Borders
Element borders are located between margin and padding. In styles, borders are defined by the properties of the border group:  
<code>border-color: #000;</code> - *цвет границы*  
<code>border-width: 1px;</code> - *толщина границы в px*  
<code>border-style: solid</code> - *начертание границы (see picture)*  
![border_styles.png](media/pictures/border_style.png)
Instead of writing the three properties separately, developers use the short form. The color, width and style values are indicated inside one short property (shortcut) separated by a space:  

<code>border: 3px solid #000;</code> - *3px solid black border (непрерывная граница черного цвета толщиной 3px)*  

The box-sizing property determines the behavior of borders and padding. By default, the <code>box-sizing: content-box</code> rule applies to all elements, borders, and padding expand the element.  
By setting <code>box-sizing: border-box</code>, you change the way the element's dimensions are calculated: borders and padding are drawn inward. The total width will be equal to the <code>width</code> value. Pretty intuitive behavior, so normal practice is to set it for all elements on the page at once.
![box_sizing.png](media/pictures/box_sizing.png)

In order not to type <code>box-sizing</code> manually for all elements, you should use the universal selector <code>\*</code>. It passes properties directly to every element on the page. Since <code>\*</code> is a very general selector, it must be specified at the very beginning of the CSS file.
## Shadows
Shadow is a useful design tool. The <code>box-shadow</code> property is responsible for its creation.
The property tells the browser on which side of the element the shadow should be drawn, whether to make it larger or smaller, and in what color. In code it looks like this:
```bash
div {
     box-shadow: -2px 2px 5px #FD6969;
  }
```
It means that shadow is shifted 2px to the left, 2px down, blur radius is equal to 5px, shadow color is reddish (#FD6969).  

A sequence of values that describe the shadow:
1. ***horizontal shift*** (a negative value places the shadow to the left of the element, a positive value to the right);  
2. ***vertical shift*** (a negative value places the shadow above the element, a positive value below it);  
3. ***blur radius*** (the larger the value, the wider and paler the shadow);  
4. ***color*** (specified in the same way as the color of the text or background).
   
Sometimes the shadow doesn't need to be moved, just blurring is enough. In this case, the first two values are 0.

A shadow can be created not only for the borders of an element, but also for text. In this case, the <code>text-shadow</code> property is used. It works in a similar way.

## Introduction to JS
#### ✔️ alert
Using the <code>alert()</code> directive, you can display a modal window with some text on the user's screen.
```bash
alert("Message")
```
Due to the fact that the window is modal, work with the browser interface and pages will be blocked. This is inconvenient. A modal window for the user is a window that blocks his work with the browser until he closes this window.

This is the fastest and easiest way to say something to the user, but such a window cannot be styled in any way, which means it is better to use it only for interface prototyping. In the final version of the web page, it is not desirable to use such modal dialogs.
#### ✔️ console.log
Perhaps one of the most used commands in JavaScript is <code>console.log</code>:
```bash
console.log('Useful information');
```
Using the <code>console.log</code> command, you can print information to the browser console. Only developers will be able to see this information, it will be hidden from ordinary users.
#### ✔️ let
The <code>let</code> directive declares a block-scoped variable with the ability to initialize it with a value.
```bash
let pages;
pages = 358; 
```
```bash
let pages = 358; 
```
```bash
let pages = 666;
pages = pages + 5;
```
#### ✔️ Math.random()
To generate random numbers, there is the <code>Math.random()</code> command. It returns a random number between 0 and 1, including zero and not including 1. Math.random() generates a number between 0 and 0.99999999999. So Math.random() * 10 generates numbers from 0 to 9.9999999999.
```bash
let randomNumber = Math.random();
console.log(randomNumber);        // for example, 0.9752705074780903 
```
```bash
let randomNumber = Math.random() * 10;
console.log(randomNumber);       // for example, 5.3575687
```
## Useful links
| **DESCRIPTION** | **LINK** |
|:---------:|:---------:|
| HTML tags list| [https://www.w3schools.com/tags/default.asp](https://www.w3schools.com/tags/default.asp)| 
| HTML color names| [https://www.w3schools.com/tags/ref_colornames.asp](https://www.w3schools.com/tags/ref_colornames.asp) |
| CSS color names| [https://doka.guide/css/web-colors/#nazvanie-cveta](https://doka.guide/css/web-colors/#nazvanie-cveta) | 
| Web gradients| [https://webgradients.com/](https://webgradients.com/) | 


[Back to content](#-table-of-contents)
