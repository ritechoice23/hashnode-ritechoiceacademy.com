---
title: "Understanding Link in HTML"
datePublished: Sat Jan 13 2024 09:48:09 GMT+0000 (Coordinated Universal Time)
cuid: clrbvwnz800020al4307n3um4
slug: understanding-link-in-html
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/npxXWgQ33ZQ/upload/aeb919d68a1e28c53248ce96ec91b885.jpeg
tags: web-development, webdev, html5, html-tags

---

Links are used in HTML to connect one web page to another or other resources on the internet.

A link is created using the &lt;a&gt; tag, which stands for anchor.

```xml
<a href="url">link text</a>
```

Within the &lt;a&gt; tag, you specify the destination of the link using the href attribute.

### **Linking to another web page**

The href attribute specifies the URL of the page you want to link to.

```xml
 <a href="/anotherpag.html">another page</a>
 <a href="https://www.google.com">Google.com</a>
```

### **Linking to a section on the page**

But what if you want to link to a specific section of a page? You can do that by adding an anchor tag to the URL.

href attribute specifies the URL of the page we want to link to, followed by a hash symbol (#), and then the ID of the section we want to link to.

```xml
<a href="example.com#hero">Open a section</a>
```

### **Link that opens in a new tab or window**

Next, let's look at how to create links that open in a new tab or window.

To do this, we add the target attribute to the &lt;a&gt; tag, and set it to "\_blank".

```xml
<a href="zionstack.com" target="_bank">Open in new tab</a>
```

### **Linking to Email Addresses**

Finally, let's look at how to create links to email addresses. To create a link to an email address, we use the &lt;a&gt; tag with the href attribute set to "mailto:" followed by the email address.

```xml
<a href="mailto:example@example.com">Send an Email</a>
```

And that's it! We've covered the basics of creating links in HTML.