---
layout: post
title: "deploy with ant in eclipse"
date: 2012-11-18 22:02
comments: true
categories: [eclipse, ant]
---
Trying to deploy project with ant in eclipse and getting depressing exception like

`taskdef class org.apache.catalina.ant.DeployTask cannot be found using the classloader AntClassLoader[]`

### The solution: ###

Run as -> Classpath -> add External Jars -> ...\tomcat\lib\catalina-ant.jar



