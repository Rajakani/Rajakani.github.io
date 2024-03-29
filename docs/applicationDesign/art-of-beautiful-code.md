---
layout: default
title: 'The art of writing perfect code'
parent: Application Design
nav_order: 1
modifiedDate: 2021-11-04
---
## The Art of writing beautiful code

&quot;*A complex system that works is invariably found to have evolved from a simple system that worked. A complex system designed from scratch never works and cannot be patched up to make it work. You have to start over with a working simple system* &quot; - Gall's Law

The above quote is from the book [Systemantics](https://www.amazon.in/gp/product/B00AK1BIDM/ref=as_li_tl?ie=UTF8&camp=3638&creative=24630&creativeASIN=B00AK1BIDM&linkCode=as2&tag=adyarcafe-21&linkId=c59100aa2917a653ce6d12b31f9de5ff) published in 1975 which is still relevant for any Systems Design.

<!-- more -->

### How to start writing beautiful code

Before start writing any piece of code, brainstorm more about the business terminologies to start with Class design. Discuss as much as use cases of the class and how the code could be reused for that. We don't need to implement all those scenarios upfront as this may fall under YAGNI, but still think about the modularity and extensibility of the code.

Once all the business terminologies are listed out and decide which one will become the behaviors and which one will be the properties, then write the abstract class first, Interfaces are a good choice though.
If you feel something may get change in future or may vary for different types, those are candidates to become a new sub-class.

Never write any implementation code first, write the behaviors and just add a method name inside it, if possible with the input and output parameters filled. Once you have the methods defined, its easier to read through the implementations. Here your are not writing any code, just the block names.

>I once had a Agile Coach who is a strong advisor of writing fewer lines of code per method, say five lines maximum.
I couldn't believe what he said, I didn't accept what he said, Then I look at his code and notice how simple it was.
