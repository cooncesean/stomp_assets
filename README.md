## What We Are Building
Provide a quick overview of the technical implementation of the project so folks have enough context about our stack to answer client questions, file bug reports, etc.

1. **Tech Stack (Back-End):** The back-end is essentially morphing into a fat data store with an API layer around it that provides an interface for users to get and set data.
    * The back-end team develops in a programming language called Python, 
    * Leverages a web framework called Django (which provides a lot built-in niceties around user management, authentication, etc).
    * And are using an open source library called DjangoRestFramework, which acts as our API library.
1. **Tech Stack (Front-End):** By contrast, the front-end is evolving from a number of individual templates into a single page app written in pure Javascript. The end result should be a faster, more fluid interface that makes it easy for CSAs and customers to manage their guides.
    * The front-end team develops in a programming language called CoffeeScript,
    * And leverages a new front-end framework called ReactJS (which is an open source library from Facebook).
1. **Communication:** These two projects are being developed independently from each other but they communicate by making API calls to fetch, create, edit and delete data. Why are building it this way I'll get into why this is preferred in a bit), but the two primary factors are performance and re-usability as we'll be opening up a subset of these APIs to our app teams and eventually to third parties.

## Why We Are Building It This Way:
Discuss the main drivers behind our architecture decisions.

1. **Market Flexibility:** We wanted to build Gears in such a way that it was not only forward thinking in terms of architecture and scalability, but wanted to be flexible enough to address different verticals with ease.
1. **Localization:** We wanted to make the platform readily able to handle localized content -- we currently have a very hacky way of handling Guide content that needs to translated into multiple languages and our goal was to build the project in such a way that it can support a much more scalable approach.
1. **Expose Guidebook Data:** A big goal of this re-architecture was to unlock Guidebook data to enable us to more easily connect with third party services. Turning the back-end into a set of APIs allows us great freedom to start talking with a number of different services.
1. **Performance:** The current page load times in Gears is ~3 seconds - which is obviously something our team is striving to improve. Most of the performance lag actually occurs during page render (on the front-end), so moving the architecture to a single page app will have a tremendous impact on performance and I'll explain why:
    * On the user's initial request to Gears, they download a single, tiny html file and single gzipped javascript file which contains all of the logic needed to render our single page app.
    * All subsequent navigation to different parts of the CMS no longer require full round trip page rendering and delivery to the client. Every request (from the front-end to the back-end) returns a simple status code and optional json payloads. 
Anecdotally, (and we've only tested with small data sets and limited traffic) performance seems about ~10-15x faster than current Gears 2 production.
1. **Technical Debt:** Gears 2 was built over 2 years ago to address a very specific use case -- Events. As the product has evolved, we've had to scramble to add new functionality and features that weren't part of the initial architecture. That has led to some Frankenstein additions to our code base -- all of which will be cleaned up after Gears 3 is out. Note, this is totally natural, but as the company grows and our teams scale, it becomes more and more important to keep this debt to a minimum --- both teams are doing a fantastic job to build Gears 3 in a way that will make future additions easier and cleaner to integrate.

## Where We're At

1. Discuss progress that has been made.
1. Discuss where we are.
1. Set expectations with the launch date (both internal and external).

## Thanks
Big thanks to everyone on the team for all of their hard work and intelligent contributions to date -- we have come a very long way and I couldn't be prouder of the team we have built and the product we're launching. We understand how important it is to the company to get this shipped and we are doing all we can to work towards that goal.

##Questions
