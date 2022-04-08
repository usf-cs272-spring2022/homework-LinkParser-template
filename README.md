LinkParser
=================================================

![Points](../../blob/badges/points.svg)

For this homework, you will get all of the links from a snippet of well-formed (validating) HTML. Specifically, your code must return a list of HTTP or HTTPS URLs (or links) from the HTML `a` anchor tag `href` attribute. Your code can assume the `href` attribute value will always be included within opening `"` and closing `"` quotation marks. However, your code should *not* include links in the `href` attribute of the `link` or other tags. 

A method is provided that will make sure URLs are in a semi-consistent properly-encoded form. Your code must figure out how to deal with relative vs absolute links, however. See below for more.

## Hints ##

Below are some resources that may help with this homework assignment:

  - [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML)
  - [W3C Markup Validation](https://validator.w3.org/)
  - [Regular Expressions 101](https://regex101.com/)

#### Anchor Tags

You will need to be familiar with the anchor tag `<a>` for this assignment. Some resources include:

  - [MDN - The Anchor element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)
  - [MDN - What is a URL](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL)
  - [The Java Tutorials - Creating a URL](https://docs.oracle.com/javase/tutorial/networking/urls/creatingUrls.html)

The anchor tag is used to create links on web pages. For example:

```html
<a href="https://www.cs.usfca.edu/">USF CS</a>
```

The above code will generate the link <a href="https://www.cs.usfca.edu/">USF CS</a>, where the link text is `USF CS` and the link destination is `https://www.cs.usfca.edu/`. The link will always be placed in the `href` attribute of the `a` anchor tag, but not all `a` anchor tags will have this attribute. For example, this is a valid `a` anchor tag without the `href` attribute:

```html
<a name="home" class="bookmark">Home</a>
```

And, the `href` attribute may appear in other tags. For example, this is a valid `link` tag to include a style sheet:

```html
<link rel="stylesheet" type="text/css" href="style.css">
```

Since the `href` attribute above does not appear in an `<a>` anchor tag, it should NOT be parsed by your code.

#### Relative and Absolute Links

Many URLs on webpages are relative (i.e. specified relative to the current webpage URL). Your code will need to convert those relative URLs into an absolute URL. For this, your code may use the `java.net.URL` class. For example, consider the following:

```java
URL base = new URL("http://www.cs.usfca.edu/~sjengle/cs212/");
URL absolute = new URL(base, "../index.html");

// outputs http://www.cs.usfca.edu/~sjengle/index.html
System.out.println(absolute);
```

This works even if the provided string was already absolute. For example:

```java
URL base = new URL("http://www.cs.usfca.edu/~sjengle/cs212/");
URL absolute = new URL(base, "http://www.example.com/");

// outputs http://www.example.com/
System.out.println(absolute);
```

Because of this, you do not need to test if a link was relative or absolute. Your code can **always use the above** approach to process links.

## Requirements ##

See the Javadoc and `TODO` comments in the template code in the `src/main/java` directory for additional details. You must pass the tests provided in the `src/test/java` directory. Do not modify any of the files in the `src/test` directory.

See the [Homework Guides](https://usf-cs272-spring2022.github.io/guides/homework/) for additional details on homework requirements and submission.
