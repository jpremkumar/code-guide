**HTML Coding Practices**
----------------------------------------

The goal is to write well-structured and standards-compliant markup. The guidelines described here provide a brief introduction to HTML coding practices; 

**1. Write Standards-Compliant Markup**
----------------------------------
The code that follows has multiple errors, including using the intro ID attribute value multiple times when it should be a unique value, closing the p and strong elements in the wrong order within the first paragraph, and not closing the p element at all in the second paragraph.


**Bad Code**

```html
<p id="intro">New items on the menu today include <strong>caramel apple cider and breakfast crepes</p>.</strong>
<p id="intro">The caramel apple cider is delicious.

```
**Good Code**
```html
<p class="intro">New items on the menu today include <strong>caramel apple cider and breakfast crepes</strong>.</p>
<p class="intro">The caramel apple cider is delicious.</p>
```
**2. Blank Lines and Indentation**
----------------------------------

Do not add blank lines without a reason.

For readability, add blank lines to separate large or logical code blocks.

For readability, add two spaces of indentation. Do not use the tab key.

Do not use unnecessary blank lines and indentation. It is not necessary to indent every element:


**3. Make Use of Semantic Elements**
----------------------------------

Here the HTML doesn’t use the proper heading and paragraph elements; instead, it uses meaningless elements to style and group content.

**Bad Code**

```html
<span class="heading"><strong>Welcome Back</span></strong>
<br><br>
It has been a while. What have you been up to lately?
<br><br>
```

**Good Code**
```html
<h1>Welcome Back</h1>
<p>It has been a while. What have you been up to lately?</p>

```

**4. Keep the Syntax Organized**
----------------------------------
These include the following:

* Use lowercase letters within element names, attributes, and values
* Indent nested elements
* Strictly use double quotes, not single or completely omitted quotes
* Remove the forward slash at the end of self-closing elements
* Omit the values on Boolean attributes


**Bad Code**

```html
<Aside>
<h3>Chicago</h3>
<H5 HIDDEN='HIDDEN'>City in Illinois</H5>
<img src=chicago.jpg alt="Chicago, the third most populous city in the United States" />
<ul>
<li>234 square miles</li>
<li>2.715 million residents</li>
</ul>
</ASIDE>

```

**Good Code**
```html
<aside>
  <h3>Chicago</h3>
  <h5 hidden>City in Illinois</h5>
  <img src="chicago.jpg" alt="Chicago, the third most populous city in the United States">
  <ul>
    <li>234 square miles</li>
    <li>2.715 million residents</li>
  </ul>
</aside>

```

**5. Use Practical ID & Class Values**
----------------------------------

The HTML here assumes that the alert message will be red. However, should the style of the alert change to orange the class name of red will no longer make sense and will likely cause confusion.

**Bad Code**

```html
<p class="red">Error! Please try again.</p>
```

**Good Code**
```html
<p class="alert">Error! Please try again.</p>

```


**6. Use the Alternative Text Attribute on Images**
----------------------------------

Images should always include the alt attribute. Screen readers and other accessibility software rely on the alt attribute to provide context for images.

**Bad Code**

```html
<img src="puppy.jpg">

```

**Good Code**
```html
<img src="puppy.jpg" alt="A beautiful, two-year-old hound mix puppy">

```

**7. Separate Content from Style**
----------------------------------

Never, ever, use inline styles within HTML. Doing so creates pages that take longer to load, are difficult to maintain, and cause headaches for designers and developers. Instead, use external style sheets, using classes to target elements and apply styles as necessary.

**Bad Code**

```html
<p style="color: #393; font-size: 24px;">Thank you!</p>

```

**Good Code**
```html
<p class="alert-success">Thank you!</p>

```

**8. Avoid a Case of “Divitis”**
----------------------------------

We need to do our best to keep our code lean and to reduce markup, tying multiple styles to a single element where possible. Additionally, we should use the HTML5 structural elements where suitable.

**Bad Code**

```html
<div class="container">
  <div class="article">
    <div class="headline">Headlines Across the World</div>
  </div>
</div>

```

**Good Code**
```html
<div class="container">
  <article>
    <h1>Headlines Across the World</h1>
  </article>
</div>

```


**CSS Coding Practices**
----------------------------------------



**1. Organize Code with Comments”**
----------------------------------

CSS files can become quite extensive, spanning hundreds of lines. These large files can make finding and editing our styles nearly impossible. Let’s keep our styles organized in logical groups. 

**Bad Code**

```css
header { ... }
article { ... }
.btn { ... }

```

**Good Code**
```css
/* Primary header */
header { ... }

/* Featured article */
article { ... }

/* Buttons */
.btn { ... }

```


**2. Write CSS Using Multiple Lines & Spaces**
----------------------------------

Doing so makes the code easy to read as well as edit. When all of the code is piled into a single line without spaces, it’s hard to scan and to make changes. 

**Bad Code**

```css
a,.btn{background:#aaa;color:#f60;font-size:18px;padding:6px;}
```

**Good Code**
```css
a,
.btn {
  background: #aaa;
  color: #f60;
  font-size: 18px;
  padding: 6px;
}

```


**3. Use Proper Class Names**
----------------------------------

Class names (or values) should be modular and should pertain to content within an element, not appearance, as much as possible. These values should be written in such a way that they resemble the syntax of the CSS language. Accordingly, class names should be all lowercase and should use hyphen delimiters.

**Bad Code**

```css
.Red_Box { ... }

```

**Good Code**
```css
.alert-message { ... }

```


**4. Build Proficient Selectors**
----------------------------------

Let’s use shorter and primarily direct selectors. Nest them only two to three levels deep, and remove as many location-based qualifying selectors as possible.


**Bad Code**

```css
#aside #featured ul.news li a { ... }
#aside #featured ul.news li a em.special { ... }

```

**Good Code**
```css
.news a { ... }
.news .special { ... }
```

**5. Use Specific Classes When Necessary**
----------------------------------

For example, if an em element is nested within an h1 element inside of an aside element, and all of that is nested within a section element, the selector might look something like aside h1 em. Should the em element ever be moved out of the h1 element the styles will no longer apply. A better, more flexible selector would use a class, such as text-offset, to target the em element.


**Bad Code**

```css
section aside h1 em { ... }

```

**Good Code**
```css
.text-offset { ... }

```

**6. Use Shorthand Properties & Values**
----------------------------------

When we’re only setting one value, though, shorthand alternatives should not be used. If a box only needs a bottom margin, use the margin-bottom property alone. Doing so ensures that other margin values will not be overwritten, and we can easily identify which side the margin is being applied to without much cognitive effort.


**Bad Code**

```css
img {
  margin-top: 5px;
  margin-right: 10px;
  margin-bottom: 5px;
  margin-left: 10px;
}
button {
  padding: 0 0 0 20px;
}

```

**Good Code**
```css
img {
  margin: 5px 10px;
}
button {
  padding-left: 20px;
}

```

**7. Use Shorthand Hexadecimal Color Values**
----------------------------------

When available, use the three-character shorthand hexadecimal color value, and always use lowercase characters within any hexadecimal color value. The idea, again, is to remain consistent, prevent confusion, and embrace the syntax of the language the code is being written in.


**Bad Code**

```css
.module {
  background: #DDDDDD;
  color: #FF6600;
}

```

**Good Code**
```css
.module {
  background: #ddd;
  color: #f60;
}
```


**8. Drop Units from Zero Values**
----------------------------------

One way to easily cut down on the amount of CSS we write is to remove the unit from any zero value. No matter which length unit is being used—pixels, percentages, em, and so forth—zero is always zero. Adding the unit is unnecessary and provides no additional value.


**Bad Code**

```css
div {
  margin: 20px 0px;
  letter-spacing: 0%;
  padding: 0px 5px;
}

```

**Good Code**
```css
div {
  margin: 20px 0;
  letter-spacing: 0;
  padding: 0 5px;
}
```


**9. Modularize Styles for Reuse**
----------------------------------

CSS is built to allow styles to be reused, specifically with the use of classes. For this reason, styles assigned to a class should be modular and available to share across elements as necessary.


**Bad Code**

```css
.news {
  background: #eee;
  border: 1px solid #ccc;
  border-radius: 6px;
}
.events {
  background: #eee;
  border: 1px solid #ccc;
  border-radius: 6px;
}

```

**Good Code**
```css
.feat-box {
  background: #eee;
  border: 1px solid #ccc;
  border-radius: 6px;
}

```
