---
layout: post
title: "run project in jetty with maven"
date: 2012-11-16 19:47
comments: true
categories: maven, jetty, pom.xml 
---
add to *pom.xml* under *\<plugins\>* 
```xml
<plugin>
	<groupId>org.mortbay.jetty</groupId>
	<artifactId>maven-jetty-plugin</artifactId>
</plugin>
```
and run
```bash
mvn jetty:run
```
