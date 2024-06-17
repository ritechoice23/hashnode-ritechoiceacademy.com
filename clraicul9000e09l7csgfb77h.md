---
title: "Working with text in HTML"
datePublished: Fri Jan 12 2024 10:41:03 GMT+0000 (Coordinated Universal Time)
cuid: clraicul9000e09l7csgfb77h
slug: working-with-text-in-html
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/cckf4TsHAuw/upload/675685375f4d4dc6116485a4f1061cb2.jpeg
tags: web-development, html, html5

---

To create a web page, you will have to write out text in the document, there is a way to structure this in HTML via tags made available for us.

Let's take a look at some popular ones you will often work with.

### **Paragraphs and Headings:**

To create a paragraph, you just need to wrap your text in a `p` tag

```xml
<p>This is just a paragraph</P>
```

To give a heading in your text you will use a `h` and it ranges from 1 to 6 depending on the level of the heading, just like you would do if you were working with a word processor software.

```xml
<h1>Heading 1</h1>    
<h2>Heading 2</h2> 
<h3>Heading 3</h3> 
<h4>Heading 4</h4> 
<h5>Heading 5</h5> 
<h6>Heading 6</h6> 
```

## Example

create a web page to display the profile, have a heading of my profile and a paragraph of my bio.

```xml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Profile</title>
</head>
<body>
    <h1>My Profile</h1>
    <h1>@Ritechoice23</h1>
    <p>
        Bio: I am a web developer with more that 10 years of experience with
        with languages like PHP, LARAVEL, JAVASCRIPT, REACT JS, VUE JS, PYTHON and more.
     </p>
</body>
</html>
```

This is just a starting point working with text in HTML more coming.