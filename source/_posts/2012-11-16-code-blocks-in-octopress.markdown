---
layout: post
title: "insert code blocks in octopress"
date: 2012-11-16 19:55
comments: true
categories: [octopress,markdown,code highlighting]
---
### How to insert code blocks in Octopress. Quick tutorial with examples.
<!-- more -->
*Example:*
		no higlighted code block (4 spaces ident or tab) (<pre> element in html)
==>
	no higlighted code block (4 spaces ident or tab) (<pre> element in html)

***
*Example:*
	``` 
	no highliting, with numbers
	:)
	```
==>

``` 
no highliting, with numbers
:)
```

***
*Syntax:*
	``` [language] [title] [url] [link text]
	code snippet
	```
*Example*
	```java Some Title http://fictive_url There is a link
	int a = 5;
	```
===>
```java Some Title http://fictive_url There is a link
int a = 5;
System.out.println("That's it");
```

[MORE](http://octopress.org/docs/blogging/code/)




