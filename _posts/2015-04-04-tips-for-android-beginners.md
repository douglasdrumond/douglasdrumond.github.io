---
layout: post
title: "Tips for Android beginners"
date: "2015-04-04"
categories: ""
tags: [""]
author: "Douglas Drumond"
background: /assets/images/cover.jpg
---

A while ago someone asked on
[Quora](https://www.quora.com/What-would-be-the-best-path-for-learning-Android-app-development-I-have-a-good-knowledge-of-Java-but-no-understanding-of-XML/)
how to learn Android development. The person had knowledge of Java, but none of
XML. I suppose the fear of XML came from the fact that is well known that
Android uses a lot of XML. I started with a quick clarification on XML syntax
and that's the only required knowledge of XML. The parsing is done
automatically by the Android system or the build tools. Unless, of course, the
person is writing a XML parser or using one (e.g., parsing a response from
a server).

Here is my answer:

If you're afraid of XML because layouts and resources are specified in XML in
Android, here's everything you need to know:

* Syntax is a lot similar to HTML.
* Everything is case-sensitive: `<application>` is different from
  `<Application>`, so pay attention (most of Android tags are camel cased, but
  `<fragment>` is all lower, for example).
* Attributes must be quoted `<⋯ android:background="#FFFFFF">` and not 
`<⋯ android:background=#FFFFFF>`
* Tags can't be interleaved: `<aaa><bbb></bbb></aaa>` is valid,
  `<aaa><bbb></aaa></bbb>` is not.
* Tags must be closed: `<aaa>` needs `</aaa>`
* or it must be single tag: `<aaa />`
* Namespaces in attributes come before colon: `<⋯ android:id="⋯">` (this is
  using attribute id from android namespace

Of course, if you're developing a parser, or you're writing XML extensively,
you need a lot more. This is just to get started in Android. Now you're set to
go.

There are a lot of books teaching Android. I learned back in 2010 from this
book: 
<a href="http://www.amazon.com.br/gp/product/1118102274/ref=as_li_qf_sp_asin_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1118102274&linkCode=as2&tag=caflin-20">Professional Android 4 Application Development</a><img src="http://ir-br.amazon-adsystem.com/e/ir?t=caflin-20&l=as2&o=33&a=1118102274" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />
(although it was Android 2 that time) and also
from experimenting on. Some people find this book a little terse, I prefer
books like that, that goes straight to the point instead of wasting paper and
my time telling a lot of things unrelated or just to make the text dumb proof.
Recently I got a copy of 
<a href="http://www.amazon.com.br/gp/product/0321804333/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0321804333&linkCode=as2&tag=caflin-20">Android Programming: The Big Nerd Ranch Guide</a><img src="http://ir-br.amazon-adsystem.com/e/ir?t=caflin-20&l=as2&o=33&a=0321804333" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />
and it's nice too. If you manage to finish the book, congratulations.

Later you can read <a
href="http://www.amazon.com.br/gp/product/B00BJOO6YW/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00BJOO6YW&linkCode=as2&tag=caflin-20">Android
Design Patterns: Interaction Design Solutions for Developers</a><img
src="http://ir-br.amazon-adsystem.com/e/ir?t=caflin-20&l=as2&o=33&a=B00BJOO6YW"
width="1" height="1" border="0" alt="" style="border:none !important;
margin:0px !important;" /> for interaction design and <a
href="http://www.amazon.com.br/gp/product/0321886739/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0321886739&linkCode=as2&tag=caflin-20">Android
User Interface Design: Turning Ideas and Sketches Into Beautifully Designed
Apps</a><img
src="http://ir-br.amazon-adsystem.com/e/ir?t=caflin-20&l=as2&o=33&a=0321886739"
width="1" height="1" border="0" alt="" style="border:none !important;
margin:0px !important;" /> for UI.

But if you don't want to spend any money, don't worry. The best source is still
[Android Developers](http://developer.android.com/) site. Start here: [Getting
Started](https://developer.android.com/training/index.html) and also read here:
[Introduction to Android](https://developer.android.com/guide/index.html).  You
need nothing else. 

When stuck, Google it. Don't be the person that asks for help in the forums without searching before. If you're stuck, look into Android developers group, Stack Overflow, Android developers Google+ community, your local group (for instance, in Brazil we have androidbrasil-dev and Stack Overflow in Portuguese). A note about Stack Overflow: don't just copy an answer, try to understand it. If you're still stuck, post your question, but tell which paths you already tried, be polite, patient and write in good English. I'm tired of reading “idk wat to do, app crash, help me” and I can bet most of other readers are tired too.

And, the most useful advice in this answer: practice, practice, practice.

_Note: When I wrote this answer on Quora, [Android
Fundamentals](https://www.udacity.com/course/ud853) course on Udacity wasn't
available. But I cannot write about Android resources nowadays without
recommending it, it's quite nice._
