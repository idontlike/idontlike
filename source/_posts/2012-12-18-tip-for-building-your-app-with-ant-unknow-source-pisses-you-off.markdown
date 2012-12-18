---
layout: post
title: "Tip for building your app with ant (Unknow Source pisses you off? - turn debug flag on)"
date: 2012-12-18 21:29
comments: true
categories: [ant,javac,spring]
---

Sometimes small things makes a big difference. 

I suggest to add (if you have no) `debug="true"` to your `javac` command in ant.

<!-- more -->
Otherwise exception stacktrace will piss you off with something like `com.idontlike.fuck(Unknown Source)`. You want line numbers instead of `Unknow Source`. Doesn't you?

By the way. After this small change you can know param names in Methods by reflection. Spring implemented ParameterNameDiscoverer for you that do the stuff. Debug flag should be turned on for this feature.

So if you have method `public privet(String name, Integer bu)`,
`parameterNameDiscoverer.getParameterNames(method)` will return [name,bu]. Can be usefull.

It looks that debug flag doesn't have perfomace overhead (only on startup load). (http://stackoverflow.com/a/218194/510089)