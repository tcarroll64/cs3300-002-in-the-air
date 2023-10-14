# Basic HTML, CSS, and Bootstrap

### Table of Contents

[Overview](#overview)



[HTML](#html)

    [Elements](#html-elements)

    [Attributes](#html-attributes)

        [Links](#href-attribute)

        [Images](#src-attribute)

    [Headings](#headings)

    [Paragraphs](#paragraphs)

    [Comments](#comments-in-html)

    [Lists](#lists-in-html)

        [Ordered Lists](#html-ordered-lists)

        [Unordered List](#html-unordered-lists)

        [Description List](#html-description-lists)

    [Forms](#html-forms)

    [HTML Online Editor](#html-online-editor)



[CSS](#css)

    [Comments](#css-comment)

    [Classes](#css-classes)

    [Borders](#css-borders)



[Bootstrap](#bootstrap)

    [Containers](#bootstrap-containers)

    [Colors](#bootstrap-colors)

    [Lists](#bootstrap-lists)

    [Dropdowns](#bootstrap-dropdowns)

    [Navigation Menu](#bootstrap-navigation-menu)



[Web Accessibility](#web-accessibility)

    

[Resources](#resources)

    [HTML](#html-resources)

    [CSS](#css-resources)

    [Bootstrap](#bootstrap-resources)

    [Web Accessibility](#web-accessibility-resources)





## Overview

This document will show a brief generalization of HTML, CSS, and Bootstrap basics. The [table of contents](#table-of-contents) serves as an ease to navigate the document based on what sections you specifically want to view. This may not be the only thing you need for HTML, CSS, and Bootstrap for the rest of this semester, but it will have most of the information needed for the semester.





## HTML

HTML is the standard language for making web applications. Most websites you use throughout your day online are based in the HTML language. HTML is a language that uses [elements](#html-elements) and [attributes](#html-attributes) rather than using strict lines of code, unlike C or Java.



#### HTML Elements

Elements are all of the things that are contained in the code which are defined by some start tag, content, and finished with an end tag. Here is an example of a skeleton of an element:

```html
<tagname>Content</tagname>
```

Elements can be nested inside of each other for example when using [classes](#html-classes).





#### HTML Attributes

Attributes are additional information in HTML. Elements can have attributes, but some things such as images and links are attributes themselves.  Attributes are always going to be displayed in the start tag and usually consist of a **name="value"**.

##### 

##### href Attribute

The href attribute is how to define a hyperlink. The tags are going to have **a** within the angle brackets and a name after to mask the link with specified text. Here is an example href attribute:

```html
<a href="https://www.youtube.com/watch?v=3OFj6l2tQ9s"> Mr Beast: 
World's Most Dangerous Trap!</a>
```



##### src Attribute

The src attribute is how you will define an image. The tags are going to have **img** within the angle brackets with a specific pathing to the image. Here is an example a src attribute:

```html
<img src="mr_beast.jpg">
```

You can specify specific widths with the width attribute: **width="pixel-size"** and the height attribute: **height="pixel-size"** where the **pixel-size** is any numerical size you want. You can also add alternate text to the image with the alt attribute: **alt="text"**. All of these additional attributes will proceed the src attribute of the img.





#### Headings

Headings are titles or subtitles that can break up sections of the web application you are working on. These headers are distinctly bold text that is larger than other content on the web app's page. Headers are distinguished in tags by **h#** where the # is any number 1 to 6. Here is an example of headings:

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

As shown there are six levels to the heading sizes and the higher the heading number the smaller the heading is.





#### Paragraphs

A paragraph is any text encased in the angle brackets by a **p**. Any text can be put into a paragraph, and you can include attributes inside of the paragraph such as links and text. Paragraphs are mostly placed in the **body** section of the HTML. Here is a simple paragraph example:

```html
<p>This is a paragraph.</p>
```

Paragraphs can also span multiple lines like this:

```html
<p>
This
is
a
paragraph.
</p>
```

But, when making it span multiple lines, the web app will ignore the white space and place the text into one line unless you use **br** inside of angle brackets to make a break line.





#### Comments

Comments are used to distinguish what parts of the HTML do and are not shown on the web app's page. Comments are useful for documentation if you or someone else is going to look at the HTML code in the future. Comments can be placed anywhere in the code for extra documentation, but are most useful if they have their own designated line. An example of a comment:

```html
<!-- This is a comment -->
```





#### Lists in HTML

Lists in HTML are a way to display a set of related items that can be ordered or unordered. Lists can also have numbered sets of information or not. Most lists will have a [header](#headings) above the list to demonstrate the overall of the items in the list. Every list element will have the tag **li** inside of the angled brackets.



##### HTML Ordered Lists

Ordered lists have a tag of **ol** inside the angled brackets. Each item in the list will be numbered based on its location in the HTML. Here is an example of an ordered list:

```html
<ol>
    <li>This is the first element labeled with the number 1</li>
    <li>This is the second element labeled with the number 2</li>
    <li>This is the third element labeled with the number 3</li>
</ol>
```



##### HTML Unordered Lists

Unordered lists have a tag of **ul** inside the angled brackets. Each item is not numbered but they are bullet-pointed. Here is an example of an unordered list:

```html
<ul>
    <li>This is the first element of the unordered list</li>
    <li>This is the second element of the unordered list</li>
    <li>This is the third element of the unordered list</li>
</ul>
```



##### HTML Description Lists

Description lists have a tag of **dl** inside the angled brackets. Each element in this list will either have the tag **dt** if it is a tag that names a term or **dd** that describes the name of the term. Here is an example of a description list:

```html
<dl>
    <dt>Here is the term of the first item in the list</dt>
    <dd>Here is the description of the first item in the list</dd>
    <dt>Here is the term of the second item in the list</dt>
    <dd>Here is the description of the second item in the list</dd>
</dl>
```





#### HTML Forms

Forms are used to capture user input and send the input to the server. The input can vary from button presses to text inputs. Forms will be tagged with **form** inside of the angled brackets. Here is a skeleton example of a form:

```html
<form>
form elements
</form>
```

##### Forms with a Text Return

The elements inside of the form will either be tagged inside of the angle brackets with **label for="name"** if it is the label of the form or **input** with attributes if it is what you are taking from the user.  Here is a simple example of a form with a text input:

```html
<form>
    <label for="label-name">Text displayed</label><br>
    <input type="text" id="specific-id" name="label-name">
</form>
```

The **type="text"** section is always the same on every text input.



##### Forms with a Button Return

There are radio buttons that can be used in the form that allows the user to select one input from a limited amount of choices. Here is an example of the radio attribute:

```html
<input type="radio" id="specific-id" name="name" 
value="returned-value-in-server">
```



There are checkboxes that you can use in forms where the user can select zero or more options. These are useful for multiple specified inputs. Here is an example of a checkbox attribute:

```html
<input type="checkboxes" id="specific-id" name="name" 
value="returned-value-in-server">
```



There is a submit button that allows the user to submit multiple text returns at once which would be this attribute inside of the form:

```html
<input type="submit" value="Submit">
```

**There is a lot more to forms. If you need more information on forms please refer to the section on forms in the [HTML Resources](#html-resources).**



#### HTML Online Editor

Here is an online editor if you would like to run sections of HTML or an HTML code:

[HTML Online Editor](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_lists_ordered)



## CSS

CSS is the language used to style things in HTML. CSS is used to add things such as specific colors, text alignments, fonts, font sizes, etc. CSS can be used inside of any HTML code. You can force certain elements to change for example:

```html
elementTagName {
    first-attribute-change;
    second-attribute-change;
}
```



#### CSS Classes

Classes are an attribute that help divide sections of the web application's page. The tags that specify are **div** inside of the angled brackets. You can make all of the attributes of that section that you want to distinguish inside of the class's style definition. A class's style definition is distinguished by **.class-name** where class-name can be changed to anything. Here is an example of a class:

```html
<head>
.mrBeast {
    background-color: beige;
    color: black;
}
</head>
<body>
<div class="mrBeast">
    <p>Mr.Beast is the most subscribed YouTuber.</p>
</div>
</body>
```

As shown the class's style is typically in the head of the HTML and the calling of the class is done in the body around other elements. The class is changing attributes of the element shown in the [paragraph](#paragraphs) section.



#### CSS Comments

Comments are not displayed on the web app's page but are used to document code. Typically they will be on the same line as the CSS code in the HTML. Here is an example of CSS comments:

```css
/* comment here */
```



#### CSS Colors

Colors in CSS are predefined when using a named color, but you can also add RGB, HEX, HSL, RGBA, or HSLA values to change colors. Colors can be on anything that is visible on the web app's page from text to background.



##### Specified Color Example

A specified color will be used when the name of the color is put into the style section of the attribute.

```html
<h1 style="color:Red;">...</h1>
```



##### HEX and Other Color Example

The top to bottom are in descending order of RGB, HEX, HSL, RGBA, and HSLA on 5 different headers' backgrounds.

```html
<h1 style="background-color:rgb(255, 99, 71);">...</h1>
<h1 style="background-color:#ff6347;">...</h1>
<h1 style="background-color:hsl(9, 100%, 64%);">...</h1> 
<h1 style="background-color:rgba(255, 99, 71, 0.5);">...</h1>
<h1 style="background-color:hsla(9, 100%, 64%, 0.5);">...</h1>
```



##### Background Colors vs. Text Colors

The colors in the background and text can be the same or different. The only difference is the use of **background-color** to denote the background color or **color** to denote the text color.



#### CSS Borders

Borders are used to border sections in the web app's page. There are dotted, dashed, solid, double, groove, ridge, inset, outset, no border, hidden, and mixed borders. Here is a picture of all borders. ![](C:\Users\JoeMama\AppData\Roaming\marktext\images\2023-10-13-21-27-12-image.png)

Here is an example to put these borders in code: 

```html
p.dotted {border-style: dotted;}
p.dashed {border-style: dashed;}
p.solid {border-style: solid;}
p.double {border-style: double;}
p.groove {border-style: groove;}
p.ridge {border-style: ridge;}
p.inset {border-style: inset;}
p.outset {border-style: outset;}
p.none {border-style: none;}
p.hidden {border-style: hidden;}
p.mix {border-style: dotted dashed solid double;}
```



#### CSS Padding

Padding is the space around contained elements in the HTML. Padding is useful for a defined spacing that can make bordered or contained elements even on the web app's page. Padding can be denoted inside of a class's style definition. Here is a padding example with specific pixel values for the top, right, bottom, and left in that order:

```html
.class {
    padding: 10px 20px 30px 100px;
}
```





### Bootstrap

Bootstrap is another language that incorporates CSS with extra customization in HTML.



#### Bootstrap Containers

Containers allow the easy division of sections throughout the bootstrap page while padding and modifying text layouts.

###### Sizing

![](https://lh5.googleusercontent.com/pD7C3t8Styet6tVHJKuwyagDPCIyS3_BDzrqPRX2tanvcSF5Lmk_lm4mZ_U6OaGpoViPjViSPJzcvXXzBG4F6fDQufy94k8kHcvQ1JRW5ycKaeQ9KyAUYo6MrhAuWa9s8Cx5vZInYVGJ)

Default containers are shown by .container at the top of the chart and are displayed in bootstrap code by <div class=”container”> and the end of the container is designated by </div>. All other containers that have a specified size are used for responsive web pages. A fluid container will span the entire width no matter the size of the screen.



#### Bootstrap Colors

Colors are customization through set bootstrap colors, but can also be changed in the same line code using CSS code so you can pick specific hex colors. You can also determine the color of the background of a container or the entire page, the text, or the navbar. Some colors can have attributes to further the customization of the foreground or background.



##### Body: Default foreground and background

<img src="https://lh5.googleusercontent.com/0I5ZosF7YnSJOW0xVZ7Za7GbyiH0Ljby97PUQK-oFllbbP9272dvavK8COVapn3zL3eNzdAr_kYXrQjd_xO-k7_hNudsL2_m_n0kxA_T2N4j3wVFjFwmcP6YNlUtSgZ_lBzoQ3aTQ8s8" title="" alt="" data-align="center">



##### Secondary: Used for disabled content

<img src="https://lh6.googleusercontent.com/hiNLEPKpypC2CXJ5WwrgQcWQGp6EDBpVB2ZepKnkmNNkBAWEENyp-QJNfhBhTXXwlC1oAxrvXfiihttSjqobnVesSzUekwmxz77dLAkX2arT2n8VFGPWOlEWEJJllm8f8LdFGeRiTbVT" title="" alt="" data-align="center"> 



##### Tertiary: Used for accents

<img src="https://lh4.googleusercontent.com/QLmHU6YwCT5fSejhojOiBYT7DS8yRKSzWGZkmbZRFRGXfdwJiD7nHs41UMa4D-s9TPJhBMSbn_eW3EoOFkd9UT8W_5PQ08r14pSnszaTPv63tHvG8z-KrHrOX2m4gsCzHsCqmdbC6OlO" title="" alt="" data-align="center">



##### Emphasis: Used for high-contrast foregrounds

<img src="https://lh3.googleusercontent.com/YSsw7e89R5Q1X6fsgqF7BI-z4XRrNxEPwrzCc8PuSt61xPE_MAFXL5a877pV_UghJoLrOOOOqO8wgkYtZVFUnFQx7fbfhEANIhQbXCr2DS4i5mAy9VxSmEbNel9UCTZmrtOh0Y2qdjGl" title="" alt="" data-align="center">



##### Border: Used for dividers

<img src="https://lh4.googleusercontent.com/7ZCDZaRe598T60ECXcDPcyhSU3Kjx757I_VZgZLjvFH4gFsD-tjXIwSgWmgBls1R8GsbMlgwspRxoo-KGMFtdAfS0D9ll8lDnDYFUfzRJBUL416KEUtUgkJUI58qfRx4i3O0oroiUc8y" title="" alt="" data-align="center"> 



##### Primary: Main theme color used for focus points and hyperlinks

<img src="https://lh6.googleusercontent.com/Vh560poSKNOdprz73JzrO86LrYtMWHnka5wprzfF6ecp2GSeXz3XmRK9_HUQ6ayLMTTdI9MIVwqky1BwTmL0KJwxDoirOPLunve_BvsSCmwd-PC09qwf5HXPE27JFTjZtly3j2eehul9" title="" alt="" data-align="center">



##### Success: Used for successful or positive actions

<img src="https://lh5.googleusercontent.com/Ez_aHESP-t8iJe1V8bLW_tlj4WMx4rglv3keyRTibv1aZCcHCoh5gb_YHmt-FwY-5p-caT9y0uHKsGFNEtNosl6P5N_1sQJJT9ilhWcQAey-vKrfqWFbqe4UrUy3vQc2qF3QFN3rLlwk" title="" alt="" data-align="center">



##### Danger: Used for errors and destructive actions

<img src="https://lh3.googleusercontent.com/sxAq0g-Qqwt5Hsls7LKMNq4jOXyzu_HoCI-V-dk4Wj9q4m74xa_fzPKP1Mfuxcuuh696IjW3OKr0IkpvhvPivlgvvgqyefGEaej3bESKJMiPOGge5hcbl0i1320eH8UGzRg3lCTg-4ra" title="" alt="" data-align="center">



##### Warning: Used for non-destructive actions

<img src="https://lh3.googleusercontent.com/w7F6xpFOLT1yl1qgcYlGrcULcnRCmvRT1x0T5FxR172_FCpTmqZxrAmzNB5hWP7Xvr5DQsDg8xT6znDv08FIqRsKlbtacT7Kr4faaS7QTC5FiVdnmSBWxf0p74FCWaZsyaoQQJZ8Ag9E" title="" alt="" data-align="center">



##### Info: Used for neutral content and information

<img src="https://lh5.googleusercontent.com/qXb9oqA2FBNPUXvPp-xAUmFmkcdJY7VLXAX9xLwH3TVb8mGXDoFW-pvz3DlUEtko4Bs82Wt5SrT2xVTCjnWtJy52baQIS5FkFO8L_s01VDO0ZvCIpy5Anwwpeji9fBd_E_IAvnTJ50Kg" title="" alt="" data-align="center">



##### Light: Used for low contrast backgrounds and text

<img src="https://lh3.googleusercontent.com/xvrer1nMMGNNQQARodc2RJWbJhpdTyvDJAHr3Px7GR-RqZUI1OuiF4M1HZiKStaQCMBTd-OopsJwcWwtbSxwzi_A5fZ3KvyXOwRgcP6aUlnubEHDgnc0UjpK4PVlwyJCpueGfuqmVpCe" title="" alt="" data-align="center">

*Text in this example is actually black*



##### Dark: Used for high-contrast backgrounds and text

<img src="https://lh5.googleusercontent.com/toSHDzFKM80uQpyPygwb1U_Y8ZzY5-NMQAcHS1m_MQlRjL547248sXNmS10VcNZSqiH1qrNtIrJPd5YLPIzsPPh_ZmtMRe-8O9FD28PkoOC8K4DEaOrvQGZ3mE0DnaM-q5GxM6oIC173" title="" alt="" data-align="center">





#### Bootstrap Lists

Lists are groupings of elements in a grid system. Lists are usually unordered or ordered, but there are other variants of lists.



###### Unordered/ Ordered Lists:

```html
<ul class="list-group">
  <li class="list-group-item">An item</li>
  <li class="list-group-item">A second item</li>
  <li class="list-group-item">A third item</li>
  <li class="list-group-item">A fourth item</li>
  <li class="list-group-item">And a fifth one</li>
</ul>
```

```html
<ol class="list-group">
  <li class="list-group-item">An item</li>
  <li class="list-group-item">A second item</li>
  <li class="list-group-item">A third item</li>
  <li class="list-group-item">A fourth item</li>
  <li class="list-group-item">And a fifth one</li>
</ol>
```

*Unordered (top) and ordered (bottom)*



###### Active Items:

```html
<li class="list-group-item active" aria-current="true">An active 
item</li>
```



###### Disabled Items:

```html
<li class="list-group-item disabled" aria-disabled="true">A disabled 
item</li>
```



###### Links in a list:

```html
  <a href="#" class="list-group-item list-group-item-action active" 
  aria-current="true"> The current link item
  </a>
```



###### Flush: Creates a list that is partitioned without a border

```html
<ul class="list-group list-group-flush">
  <li class="list-group-item">An item</li>
  <li class="list-group-item">The next item</li>
</ul>
```



###### Numbered: Make a list that is numbers 1 and up

```html
<ol class="list-group list-group-numbered">
  <li class="list-group-item">List item numbered 1</li>
  <li class="list-group-item">List item numbered 2</li>
  <li class="list-group-item">List item numbered 3</li>
</ol>
```



###### Horizontal: Makes a list that puts the elements horizontally with varying adaptive sizes

```html
<ul class="list-group list-group-horizontal">
  <li class="list-group-item">An item</li>
  <li class="list-group-item">A second item</li>
  <li class="list-group-item">A third item</li>
</ul>
```

*Sizing is done with list-group-horizontal-size and look at the [containers](#bootstrap-containers) to see the sizing chart.*



###### Badges: Works like a notification counter

```html
<ul class="list-group">
  <li class="list-group-item d-flex justify-content-between
 align-items-center">
    A list item
    <span class="badge bg-primary rounded-pill">14</span>
  </li>
  <li class="list-group-item d-flex justify-content-between 
align-items-center">
    A second list item
    <span class="badge bg-primary 
rounded-pill">2</span>
  </li>
  <li class="list-group-item d-flex justify-content-between 
align-items-center">
    A third list item
    <span class="badge bg-primary rounded-pill">1</span>
  </li>
</ul>
```



###### Coloring Lists:

```html
<ul class="list-group">
  <li class="list-group-item list-group-item-primary">A simple primary 
list group item</li>
  <li class="list-group-item list-group-item-secondary">A simple 
secondary list group item</li>
  <li class="list-group-item list-group-item-success">A simple success 
list group item</li>
  <li class="list-group-item list-group-item-danger">A simple danger 
list group item</li>
  <li class="list-group-item list-group-item-warning">A simple warning 
list group item</li>
  <li class="list-group-item list-group-item-info">A simple info list 
group item</li>
  <li class="list-group-item list-group-item-light">A simple light list 
group item</li>
  <li class="list-group-item list-group-item-dark">A simple dark list 
group item</li>
</ul>
```



#### Bootstrap Dropdowns

Dropdowns are button that has an overlay with links or elements. You can use ARIA meus to make dropdowns more accessible.

 

###### Dropdown with elements:

```html
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button"
 data-bs-toggle="dropdown" aria-expanded="false">
    Dropdown button
  </button>
  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">Action</a></li>
    <li><a class="dropdown-item" href="#">Another action</a></li>
    <li><a class="dropdown-item" href="#">Something else here</a></li>
  </ul>
</div>
```



###### Dropdown with links:

```html
<!-- Example single danger button -->
<div class="btn-group">
  <button type="button" class="btn btn-danger dropdown-toggle" 
data-bs-toggle="dropdown" aria-expanded="false">
    Action
  </button>
  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">Action</a></li>
    <li><a class="dropdown-item" href="#">Another action</a></li>
    <li><a class="dropdown-item" href="#">Something else here</a></li>
    <li><hr class="dropdown-divider"></li>
<!-- This is the line with the link -->
    <li><a class="dropdown-item" href="#">Separated link</a></li>
  </ul>
</div>
```



###### Split Buttons: Works as a button and a dropdown

```html
<div class="btn-group">
  <button class="btn btn-secondary btn-sm" type="button">
    Small split button
  </button>
  <button type="button" class="btn btn-sm btn-secondary 
    dropdown-toggle dropdown-toggle-split" data-bs-toggle="dropdown" 
    aria-expanded="false">
    <span class="visually-hidden">Toggle Dropdown</span>
  </button>
  <ul class="dropdown-menu">
    ...
  </ul>
</div>
```



###### Dark Dropdowns: Dark variants that can match other styles

```html
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button"
 data-bs-toggle="dropdown" aria-expanded="false">Dropdown button
  </button>
  <ul class="dropdown-menu dropdown-menu-dark">
    <li><a class="dropdown-item active" href="#">Action</a></li>
    <li><a class="dropdown-item" href="#">Another action</a></li>
    <li><a class="dropdown-item" href="#">Something else here</a></li>
    <li><hr class="dropdown-divider"></li>
    <li><a class="dropdown-item" href="#">Separated link</a></li>
  </ul>
</div>
```



###### Additional Information:

Dropup can make the drop down open above the dropdown button. Centered makes the overlay of the dropdown button centered on the button. Dropend can make the dropdown overlay appear at the farthest end of the button from the left. Dropstart is the opposite of dropend. Just like lists there is the ability to have active and disabled content in the dropdown overlay.



**If you need more information please refer to the [Bootstrap Resources](#bootstrap-resources).**



#### Bootstrap Buttons

Buttons are a way to receive user input without using forms. These buttons will have specific outputs such as edit, submit, etc. so there is no miscommunication with the user. Here is a basic example of a button:

```html
<button type="button" class="btn">Base class</button>
```



###### Button Tags: Name and create values to determine which button has been pressed

```html
<a class="btn btn-primary" href="#" role="button">Link</a>
<button class="btn btn-primary" type="submit">Button</button>
<input class="btn btn-primary" type="button" value="Input">
<input class="btn btn-primary" type="submit" value="Submit">
<input class="btn btn-primary" type="reset" value="Reset">
```



###### Outline Buttons:

```html
<button type="button" class="btn btn-outline-primary">Primary</button>
<button type="button" class="btn btn-outline-secondary">Secondary</button>
<button type="button" class="btn btn-outline-success">Success</button>
<button type="button" class="btn btn-outline-danger">Danger</button>
<button type="button" class="btn btn-outline-warning">Warning</button>
<button type="button" class="btn btn-outline-info">Info</button>
<button type="button" class="btn btn-outline-light">Light</button>
<button type="button" class="btn btn-outline-dark">Dark</button>
```



###### Block Buttons: Responsive buttons that span the width of the screen

```html
<div class="d-grid gap-2">
  <button class="btn btn-primary" type="button">Button</button>
  <button class="btn btn-primary" type="button">Button</button>
</div>
```



###### Toggle Buttons: Toggleable buttons that return the active state of the button

```html
<p class="d-inline-flex gap-1">
  <button type="button" class="btn btn-primary" 
    data-bs-toggle="button">Toggle button</button>
  <button type="button" class="btn btn-primary active" 
    data-bs-toggle="button" aria-pressed="true">Active toggle button</button>
  <button type="button" class="btn btn-primary" 
disabled data-bs-toggle="button">Disabled toggle button</button>
</p>
```



#### Bootstrap Navigation Menu

Navigation Menus are user-responsive headers to navigate the web page through links, buttons, dropdowns, etc. 

Example of a full navbar:

```html
<nav class="navbar navbar-expand-lg bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" 
    data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" 
    aria-controls="navbarSupportedContent" aria-expanded="false" 
    aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">
Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" role="button" 
            data-bs-toggle="dropdown" aria-expanded="false">
            Dropdown
          </a>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here
</a></li>
          </ul>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" aria-disabled="true">Disabled</a>
        </li>
      </ul>
      <form class="d-flex" role="search">
        <input class="form-control me-2" type="search" 
        placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" 
        type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
```





###### Brand: The name of the Navbar that will send the user back to the home page if pressed

```html
<!-- As a link -->
<nav class="navbar bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
  </div>
</nav>

<!-- As a heading -->
<nav class="navbar bg-body-tertiary">
  <div class="container-fluid">
    <span class="navbar-brand mb-0 h1">Navbar</span>
  </div>
</nav>
```



###### Images with Text: Line 4 creates the image and the text

```html
<nav class="navbar bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">
      <img src="/docs/5.3/assets/brand/bootstrap-logo.svg" alt="Logo" 
        width="30" height="24" class="d-inline-block align-text-top">
      Bootstrap
    </a>
  </div>
</nav>
```



###### Forms: Used to make things like search bars and receive user input

```html
<nav class="navbar bg-body-tertiary">
  <div class="container-fluid">
    <form class="d-flex" role="search">
      <input class="form-control me-2" type="search" placeholder="Search" 
        aria-label="Search">
      <button class="btn btn-outline-success" type="submit">
        Search</button>
    </form>
  </div>
</nav>
```



###### Placements Other than Default:

Always stays on the top regardless of scrolling

```html
<nav class="navbar fixed-top bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Fixed top</a>
  </div>
</nav>
```



Always stays on the bottom regardless of scrolling

```html
<nav class="navbar fixed-bottom bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Fixed bottom</a>
  </div>
</nav>
```



Always at the top and sticks to the background of the page

```html
<nav class="navbar sticky-top bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Sticky top</a>
  </div>
</nav>
```



Always at the bottom and sticks to the background of the page

```html
<nav class="navbar sticky-bottom bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Sticky bottom</a>
  </div>
</nav>
```



#### Web Accessibility

**Web accessibility** is how web designers make a web application accessible for all users including those with disabilities. It is important because some web apps become completely inaccessible for those with disabilities, and since your web app is a public space then there are legal repercussions from having unequal accessibility for users. **Responsive web design** is the ability to have the ratio/ screen size change and the website still be accessible. This is done by using viewports and responsive images to provide the best experience for users of different screen sizes.

**If you would like to know that you are following lawful guidelines please refer to** [Guidance on Web Accessibility](https://www.ada.gov/resources/web-guidance/).





### Resources

These are all of the resources I used for this documentation broken up by section.



##### HTML Resources

**[Introduction to HTML](https://www.w3schools.com/html/html_intro.asp)**

**[HTML Elements](https://www.w3schools.com/html/html_elements.asp)**

**[HTML Attributes](https://www.w3schools.com/html/html_attributes.asp)**

**[HTML Headings](https://www.w3schools.com/html/html_headings.asp)**

**[HTML Paragraphs](https://www.w3schools.com/html/html_paragraphs.asp)**

**[HTML Comments](https://www.w3schools.com/html/html_comments.asp)**

**[HTML Lists](https://www.w3schools.com/html/html_lists.asp)**

**[HTML Forms](https://www.w3schools.com/html/html_forms.asp)**



##### CSS Resources

**[CSS Overview](https://www.w3schools.com/css/default.asp)**

**[CSS Classes - The Class Attribute](https://www.w3schools.com/html/html_classes.asp)**

**[CSS Colors](https://www.w3schools.com/css/css_colors.asp)**

**[CSS Borders](https://www.w3schools.com/css/css_border.asp)**

**[CSS Padding](https://www.w3schools.com/css/css_padding.asp)**



##### Bootstrap Resources

**[Intro to Bootstrap · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/getting-started/introduction/)**

**[Containers · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/layout/containers/)**

**[Color · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/customize/color/)**

**[List group · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/components/list-group/)**

**[Dropdowns · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/components/dropdowns/)**

**[Navbar · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/components/navbar/)**

**[What is the difference between position:sticky and position:fixed in CSS?](https://www.tutorialspoint.com/what-is-the-difference-between-position-sticky-and-position-fixed-in-css#:~:text=The%20main%20difference%20is%20that,according%20to%20the%20parent%20element).**

**[Buttons · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/components/buttons/)**



##### Web Accessibility Resources

**[Guidance on Web Accessibility](https://www.ada.gov/resources/web-guidance/)**

**[Responsive web design basics](https://web.dev/responsive-web-design-basics/)**

**[HTML Responsive Web Design](https://www.w3schools.com/html/html_responsive.asp)**


