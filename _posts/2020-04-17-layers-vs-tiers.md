---
title: layers vs. tiers
layout: article
---

A while ago, I was doing a technical interview over video call. The interview had been smooth so far until the interviewer asked about web application architectures. 

“Can you tell me what is 3-tier architecture?”

“3-tier architecture is when the code is split into 3 groups: presentation layer, data layer and the business layer. For example. MVC is an example of 3-tier architecture”

The interviewer cut me short immediately.

“MVC is not an example of 3-tier architecture”.

Luckily, they were a good interviewer and they went on to explain what it was.

Fast forward to this year and I decided to *finally* understand what exactly is the difference between a tier and a layer. And just like every software developer who has a question, I turned to Stack Overflow.

A layer is a **logical** organisation of code and can include the business layer, the data layer and the presentation layer. MVC can be classified as a 3-layer architecture because the code is logically split into 3: Model, View and Controller.

A tier is the **physical** deployment of a layer e.g a server, a computer.

Therefore, if all your code is hosted on one server, that can be described as 1-tier.

Let’s take the example of a modern application today that has an API, a React frontend and a database. These 3 layers will probably be split and run separately on 3 physical servers. Therefore, this is a 3-tier architecture.

There you have it: layers are logical; tiers are physical. Hopefully, this question doesn’t bite you like it bit me and if it does, the interviewer comes through.


