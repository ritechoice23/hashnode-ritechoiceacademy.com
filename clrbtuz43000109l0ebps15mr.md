---
title: "How and best way to group HTML tags"
datePublished: Sat Jan 13 2024 08:50:51 GMT+0000 (Coordinated Universal Time)
cuid: clrbtuz43000109l0ebps15mr
slug: how-and-best-way-to-group-html-tags
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/4hbJ-eymZ1o/upload/8d5fcdefc9d3dba826c9c8612ada103b.jpeg
tags: web-development, html, html5

---

Let's say you are working on a web page and you want to group a bunch `<p></p>` tags together, no need to panic HTML provides some tags to the group for such purposes and is often referred to as container tags.

Take a look at the code below, you will notice we have two `<p></p>` tags of which on a good day we may need to group them maybe for styling purposes or SEO optimization.

```xml
 <h1>MY PROFILE</h1>
<p>
    Hi there, I am;
</p>
<p>
    BABATUNDE EBENEZER DARAMOLA @ritechoice23
</p>
```

To group them, we can use `<div></div>`.

```xml
<h1>MY PROFILE</h1>
<div>
    <p>
        Hi there, I am;
    </p>
    <p>
        BABATUNDE EBENEZER DARAMOLA @ritechoice23
    </p>
</div>
```

`div` is the generic container element and is mostly used when we don't have a dedicated container tag for what you want to group.

For instance, if some elements are in the footer of your web page and you want to group them, there is a dedicated container tag for such case `<footer></footer>`

We have more of these tags `section`, `article`, `header`, `aside`, `main`, `footer`, `nav`

A simple example of the use of semantic element

```xml
<section>
  <header>
    <h1>Title</h1>
  </header>
  <article>
    <p>Article content</p>
  </article>
  <footer>
    <p>page footer</p>
  </footer>
</section>
```

You can read more about semantic elements on [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Semantics#semantic_elements)