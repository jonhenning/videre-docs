# Guiding Principles 

## Overview
In the past 15 years as a consultant I have had the privilege of working for many different clients in an variety of industries.  Most of that time has been spend working on web technologies.  Having the benefit of some years under my belt, I have grown to have a few opinions on what is the best way to architect the solutions I work on.  One solution I tend to push is allowing for content updates to not be a developer task.  This allows a separation of responsibilities and frees the developer up to do what developers do best- code. 

While there are many decent open-source solutions to building a Content Management System (CMS), I have yet to find one that keeps what is important to my standards at the forefront.  Recently, a client and I came to an agreement that it would be beneficial to both parties to build a CMS and make it open-source.  There are still some details to work through, but hopefully our git repository will soon be made public for all to enjoy.


## Guiding Principles in Developing Our CMS
Undertaking a project such as building a CMS needs to have a vision for what it will become, otherwise, the solution has a tendency to get side-tracked not accomplish its main goals.    The following outlines the main principles that should guide our decisions in building our CMS.

### 1.Keep code simple where possible
There is a time and a place for offering maximum scalability.  This is usually not a good starting point.  The reason is that coding for scale usually comes with a price tag of complexity.  With that complexity comes a price tag of built in dependencies, that once established, are hard to pull away from- especially with an open-source project.

### 2.Keep Things Clean
Of course, clean, is usually in the eye of the beholder.  Some developers use the phrase the code “smells” when they are unhappy with the way a certain code block turned out.  Ideally, all code we write would be perfect and elegant the first go at it, but unfortunately, that is not reality.  In the code that is written for the CMS, if a code section doesn’t “smell” right, but is functional, it should be noted with a comment for later attention. 

### 3.Let BootStrap Be Your Inspiration
It’s hard to argue that Twitter’s Bootstrap css framework is anything but elegant.  When compared to jQuery UI, for example, it is amazing how simple they were able to make everything without a whole lot of code/markup.  I used to struggle, like a lot of developers, with creating maintainable tableless designs.  With Bootstrap’s grid system, this task is amazingly simple.  In building our CMS, not only will bootstrap be one of the foundations, but it should inspire us to keep to point 1 above.

*By the way, I still love jQuery UI and think it is amazing, and my CMS is still utilizing it to fill in the gaps that Bootstrap lacks.*

### 4.Extensibility
Allow for core functionality to be extensible by implementing a provider.  Things like authentication, data persistence, themes, and search indexing should be simple to create custom implementations.  Ideally, the CMS could be updated and provisioned by simply copying a zip file in a known folder.

### 5.Minimal Dependencies
Getting the CMS up and running should require as few dependencies as possible.  Ideally, all one would need is IIS and .NET.  Things like a database would be optional, as a file system could be used for simple implementations.  Dependencies also apply to the modules, scripts, and widgets found in the core codebase.  Ideally, the core would be decoupled from the widgets used to maintain it, allowing for 3rd parties to easily offer more feature-rich alternatives.

### 6.Minimize Burdon on Developer
Developing an extension, like a widget, for the CMS should not be an involved task requiring lots of background knowledge.  Additionally, enabling that widget to utilize core capabilities like localization and search should also not require much effort.  Finally, utilize an open source-control system allowing community to easily pull and contribute to the codebase.

## Conclusion
Over the next couple weeks I plan on posting a few blogs that give insight into the design decisions of our CMS, along with some simple code examples.  In those posts, I also plan on referring back to this list in explaining why things were developed a certain way.  