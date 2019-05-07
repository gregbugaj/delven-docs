---
title: Welcome to Delven
type: index
weight: 0
---

Delven is a Domain Specific Language  (DSL) designed for mining content from static and dynamic sources, It closely resembles SQL with features borrowed from other popular dynamic languages.
It can be run as a interpreter or 'server' mode, it comes with type 4 JDBC driver for ease of integration with java applications.

This documentation is your guide to an advanced new world of real-time data connectivity.

* To get an idea of what Delven is and how it can benefit your organization, visit the Introduction Section page.
* New users and experienced users alike may refer to the [Syntax](/syntax) section for all the information you need to create robust queries. 
* For new users, the [Tutorial](/examples ) provides an introduction to basic query writing skills and a page of sample queries to get you started.
* Programmers interested in embedding Delven within their application should visit the [API Reference](/api).

## Under the hood

This is a complete rewrite of original PhantomSQL data extract engine that was written in Java.
Main issues that will be addressing with this rewrite are as follows

* Reworking language syntax
  * Based on modern languages / frameworks (EcmaScript / TypeScript / Python / Rubby / SQL/ Node.js)
  * Web 2.0 and beyound (Support for extracting data from dynamic websites as well as realtime data extraction)
* Exposing low level API as first class citizens
  * Javascript
  * TypeScript
  * C++ navive extensions  
* Query plan
* Package Manager
  * Delven Package Manager(DPM)
  * Node Package Manager(NPM)
* Distributed Processing
* Machine learning