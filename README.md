# CSS and HTML workbook
This repository was created to reflect the main points of the theory of web development self-study.
## 🎀 Table of contents
- [Flow and block model](#flow-and-block-model)
- [Padding and margin shortcut](#padding-and-margin-shortcut)
- [Borders](#borders)


## Flow and block model 
Document flow (data flow) in HTML is the order in which elements are displayed on the page. In the usual form, all blocks are displayed in the order in which they are written inside the HTML document.
The browser reads the file code from top to bottom and renders the page in the same way. Therefore, the elements are said to follow each other in a flow.

The <code>div</code>, <code>section</code>, <code>header</code>, <code>h1</code> - <code>h6</code> and <code>p</code> tags, when flowing, take up the entire width of their parent by default. Such elements are conventionally called *block elements*.  
The picture is not a block element, it is displayed with its original dimensions and can go beyond the parent block.

<b>Margin</b> is the space around the element's border outside.  
Unlike outer margins, <b>padding</b> is located inside the element and creates free space between the border and the content. The word "padding" is taken from tailors and means a shoulder pad - a pad between the fabric of the jacket and the shoulder.

The model of any element looks like this:

-content with dimensions width (ширина) and height (высота);

-margins (внешние отступы, поля);

-padding (внутренние отступы);

-borders (границы).

![padding_margin_edges.png](media/pictures/padding_margin_edges.png)

When they say “element 200 by 300”, they mean the size of the content up to and including the border, margin is not included here.


## Padding and margin shortcut
![padding_margin_shortcut.png](media/pictures/padding_margin_shortcut.png)

Placement direction - ***clockwise***, starting from the top.  
*with 4 values*: each side has its own value  
<code>padding: 20px 15px 30px 15px;</code>  
*with 3 values*: top - 10px, sides - 20px, bottom - 30px  
<code>padding: 10px 20px 30px; </code>  
*with 2 values*: top and bottom - 10px, sides - 20px  
<code>padding: 10px 20px;</code>  
*with 1 value*: 10px on all sides  
<code>padding: 10px; </code>  
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
