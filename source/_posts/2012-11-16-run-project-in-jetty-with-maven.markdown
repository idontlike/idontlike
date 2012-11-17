---
layout: post
title: "run project in jetty with maven"
date: 2012-11-16 19:47
comments: true
categories: maven, jetty 
---
add to pom.xml under /<plugins/> 
```
<plugin>
	<groupId>org.mortbay.jetty</groupId>
    	<artifactId>maven-jetty-plugin</artifactId>
</plugin>
```
and run
> mvn jetty:run
