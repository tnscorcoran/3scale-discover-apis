# 3scale Service Discovery / API Catalog.

## Introduction 

API search and discovery can be a key requirement for organizations exposing APIs. This is a particularly strong requirement for larger organizations with disparate and dispersed development teams. A key driver behind this need is prevention of duplication of effort. We frequently run into situations where one team writes and exposes an API which has already written and exposed, either partially or completely elsewhere within the enterprise. By creating a central repository of APIs, where APIs can be searched for and discovered, this situation can be avoided. 

In this article, we highlight and demonstrate a solution that can be deployed on the 3scale Developer Portal – to allow such search and discovery. The template are available at the [3scale Discover APIs](https://github.com/3scale/3scale-discover-APIs) Github repository. This community based solution was developed and is mainly contributed to by 3scale API evangelist, Nicolas Grenie.

We walk through creating a working example whose end result is a searchable catalog that resembles the following - though for simplicity we just add the member element:
![1-api-catalog](https://access.redhat.com/sites/default/files/images/1-api-catalog.png)  

