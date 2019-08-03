---
title: "Content Management System @iitr.ac.in"
date: 2019-03-18T02:01:58+05:30
description: "Every institute has it's own official website. This is either maintained by a team of hired professionals or outsourced, but here in IIT Roorkee, a bunch of geeks do that."
tags: [CMS, IITRoorkee, IMG]
disqus: false
---

Content Management System, a multi-user role-based interface for managing, updating and publishing content on IIT Roorkee's official website. This is built and managed by the student body, Information Management Group. CMS simplifies the process of updating the content on the official website of IIT-Roorkee, which consists of more than 10000 pages in itself, we build our own CMS.


## Updating website before CMS

It is very difficult to update HTML pages, and when you have thousands of them, it because next to impossible to manage. If there are only a few pages, one can think of editing them but again, whom should be given access, to what extent one should be able to access and several other problems like these were there.

At that point, we at IMG decided to build something to solve the above-mentioned problems and make it easy to manage the official website of IIT-Roorkee. Today, we are working on upgrading it and adding more features, making it easy to scale and 12-factor compliant. Still, the core remains the same.

## Tech Stack

### Yii + Apache2 + PostgreSQL

_Yii is a fast, secure, and efficient PHP framework. Flexible yet pragmatic. Works right out of the box._

_Apache2 provides a secure, efficient and extensible server that provides HTTP services in sync with the current HTTP standards._

_PostgreSQL is a powerful, open source object-relational database system._

### Git
To maintain the source code?
No, Git is not only used to maintain the source code of the project but also to maintain the history of the pages.

> We keep a track of page revisions using git.


### RabbitMQ
_RabbitMQ is lightweight and easy to deploy on-premises and in the cloud. It supports multiple messaging protocols._ \
RabbitMQ is used to maintain publish requests and push changes in production.

## Architecture design

### It's static!

The website, https://www.iitr.ac.in, that everyone sees is static, just HTML pages. \
**Then how do you update them? - ** There comes the role of CMS, In CMS one can update the content, then CMS will take care of generating HTML pages and pushing those static pages on production.
### Database: The tree structure
The entire website has been stored in the form of a tree structure. The nodes of the tree can be either a special node, which stores some metadata for pages present as a child under that special node or node can be a page. 

This tree structure helps us in providing access to users of different levels and sharing of metadata with multiple pages. All the pages of the same department will have the same navbar, so there is one special node for each department which stores the navbar fields, which is used by all the pages present in that department.

![Site structure of website](/cmsdb.jpeg)

### Everything is a component
Each page is composed of several components and every page inherits all this information from the metadata of its parent special node. The side navbar, the footer, the menu bar these all are shared on the special node level. So, once you update the metadata stored in a special node, one can see the changes in all the pages under that node.

## What's next?
There is always the scope of improvement in any product, we are no special, we at IMG, work tirelessly around the year to make it better, easy to use and match with the expectations of IIT-Roorkee. Next, we are trying to make it cloud-native ready making it easy to scale and deploy.
