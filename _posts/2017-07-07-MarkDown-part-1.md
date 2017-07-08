---
layout:     post
title:      "Getting Started With Markdown: Part 1"
subtitle:   ""
date:       2017-07-07 12:00:00
author:     "Tara"
header-img: "img/post-bg-01.jpg"

---


# Getting Started With Markdown : Part 1

**Markdown** is a no-frills **markup** (I know) language, which lets text be in the forefront of a document. It was created for converting an easy to read text format directly to HTML.

Like HTML, markdown also uses a simple text-formatting syntax to display content on the web. However, unlike HTML, markdown uses something called "Plaintext", which roughly translates to regular alphabet with a few symbols like asterisks (``*``), underscore (``_``) and tildes (``~``).

Markdown is extensively used, by the likes of Github and Reddit. Github uses Markdown for styling all forms of content on their site, whereas Reddit uses Markdown to display comments. The best thing about markdown is portability, it can be used almost anywhere, be it Emails, Websites or even while publishing a book. 

___

## 1. Bold and Italics

You've probably known this because WhatsApp implements this while formatting bold and italics content. 

To make text bold, you can surround it with (``**``), and to make it italicized, you wrap it in (``_``). 

Hence, ``**bold**`` will become **bold**, and ``_italics_`` will become _italics_.

Similarly, ~~strikethrough~~ can  be achieved using ``~~strikethrough~~``. 

___

## 2. Headings

In HTML, you can specify a heading by using h1 to h6 tags. (The size decreases from h1 to h6) Similarly, in Markdown, a Heading can be specified using ``#`` before a phrase. 

So, ``#Heading 1`` becomes 

# Heading 1

And, ``##Heading 2`` becomes

## Heading 2

Similarly, the H6 tag in HTML corresponds to ``######Header``

---

## 3. Lists

Like HTML, Markdown also supports both unordered and ordered lists. 

To create an unordered list, each item of the list has to be prefaced by (``*``). 

For example, 

```
**How to earn 1 million dollars a month

*Write a book about how to earn 1 million dollars a month

*Promote your book and give a TedX talk.

*????

*Profit
```

becomes,

**How to earn 1 million dollars a month**

* Write a book about how to earn 1 million dollars a month
* Promote your book and give a TedX talk.
* ????
* Profit


An ordered list, surprisingly is prefixed by numbers, instead of asterisk. 

(_Fun fact: Even if the list is ordered using same numbers for every item in the list, Markdown will automatically render the correct order for the list items._)

---

## 4. Links

When it comes to link, Markdown has two kinds to accommodate, **inline** and **reference** link. 

An **inline** link should contain two parts- the text of the link has to be wrapped in brackets (``[]``), and then the link has to be wrapped in parentheses(``()``) immediately following the text. For example, ``[Click here to breach your privacy](www.fb.com)`` would render as [Click here to breach your privacy](www.fb.com).

The second type of link is a **reference** link. Quite literally, this is a reference to another place in the document. (Which can be defined inside the page itself). Think of them as variable names for a link. The following example illustrates reference link.

```
Hey there, [here's a link.][fine link]
[fine link]: github.com
```

Hey there, [here's a link.][fine link]

[fine link]: github.com

It is to be noted that reference links, or rather the definition of hem don't appear in the rendered document. 



That's it for this part. We'll follow up with **Images**, **Code Snippets** and a few more quirks about Markdown in the next post of the series.





