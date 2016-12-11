---
layout: post
title: Should methods be defined on value or pointer?
---

This post points to an important distinction about methods defined on value or pointer in Golang

-----

> pointer receivers are identical to the situation in Java, although in Java the pointers are hidden under the covers; it's Go's value receivers that are unusual.

The distinction is clearly described [here](https://golang.org/doc/faq#methods_on_values_or_pointers)