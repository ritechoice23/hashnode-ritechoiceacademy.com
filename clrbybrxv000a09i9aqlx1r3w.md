---
title: "Text Formatting in HTML"
datePublished: Sat Jan 13 2024 10:55:53 GMT+0000 (Coordinated Universal Time)
cuid: clrbybrxv000a09i9aqlx1r3w
slug: text-formatting-in-html
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/p9OkL4yW3C8/upload/64040aba466b62636b03f70687972382.jpeg
tags: web-development, html, html5

---

You may want to do some basic formatting in your document without the use of CSS.

### **Bold and Italic Text**

```xml
<body>
    <p>This is <strong>bold</strong> text.</p>
    <p>This is <em>italic</em> text.</p>
</body>
```

* `<strong>`: Represents strong importance or seriousness, typically displayed as bold.
    
* `<em>`: Represents emphasized text, typically displayed as italic.
    

### **Underline Text**

```xml
<body>
    <p>This is <u>underlined</u> text.</p>
</body>
```

`<u>`: Represents underlined text.

### **Strikethrough Text:**

```xml
<body>
    <p>This text is <s>strikethrough</s>.</p>
</body>
```

* `<s>`: Represents strikethrough text.
    

### **Superscript and Subscript:**

```xml
<body>

    <p>This is <sup>superscript</sup> text.</p>
    <p>This is <sub>subscript</sub> text.</p>

</body>
```

* `<sup>`: Represents superscript text.
    
* `<sub>`: Represents subscript text.
    

### **Marked Text:**

```xml
<body>
    <p>This <mark>text</mark> is marked.</p>
</body>
```

* `<mark>`: Represents text that should be marked or highlighted.  
    

### **Quotations:**

```xml
<body>
    <p>He said, <q>This is a short quotation.</q></p>
    <p>This is a <blockquote>block quotation</blockquote> in a paragraph.</p>
</body>
```

* `<q>`: Represents a short inline quotation.
    
* `<blockquote>`: Represents a block-level quotation.
    

### **Line Breaks**

```xml
<body>
<p>This is a bunch of text, <br/> words after br will break to a new line.</p>
</body>
```

`<br>`: Represents a line break, creating a new line within the text.

### **Comments**

Comments are not visible on the webpage but can help add notes to your code.

```xml
<body>
    <!-- This is a comment. Comments are not displayed in the browser. -->
    <p>This is a paragraph with a comment.</p>
</body>
```

Almost all of the above formatting can be achieved with CSS but it is good that you know it in HTML, we will talk more about formatting in a CSS tutorial post