---
layout: post
title: "spring transactional pitfall"
date: 2012-11-23 15:09
comments: true
categories: [spring, jpa, hibernate, transactional] 
---

I saw such code written by experienced programmers:

``` java
@Transactional
public void doInsert(..) throws DaoLayerException{
	try {
		//insert..
		//update..
		//whatsoever..
	} catch (Exception e) {
		throw new DaoLayerException(e);
	} 
}
```
<!-- more -->
What's wrong with this code? May be nothing wrong. 
But usually (sometimes) people doesn't know that the transaction is not rolled back in the case of
an exception.
This happens because by the default `Transactional` annotation rolled back only in the case of `RuntimeException`.

It is very dangerous pitfall, cause consistenсy of a data can suffer, unpredictable things can happen (except the case you сonscientiously cover a code with `unit-tests`). Even so the pitfall is easy to fall into :).  

By the way, the solution is:
```java
@Transactional(rollbackFor=Exception.class)
```

I googled and had found good article about [transaction pitfalls](http://www.ibm.com/developerworks/java/library/j-ts1/index.html). It is a bit old, but looks rellevant to present reality.

The rule of thumb from the article about read only access to database: DON'T USE
```java
@Transactional(readOnly = true) //don't use it
```
Just don't put Transactional annotation at all
