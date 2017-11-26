# 3scale Service Discovery / API Catalog.

## Introduction 

API search and discovery can be a key requirement for organizations exposing APIs. This is a particularly strong requirement for larger organizations with disparate and dispersed development teams. A key driver behind this need is prevention of duplication of effort. We frequently run into situations where one team writes and exposes an API which has already written and exposed, either partially or completely elsewhere within the enterprise. By creating a central repository of APIs, where APIs can be searched for and discovered, this situation can be avoided. 

In this article, we highlight and demonstrate a solution that can be deployed on the 3scale Developer Portal – to allow such search and discovery. The template are available at the [3scale Discover APIs](https://github.com/3scale/3scale-discover-APIs) Github repository. This community based solution was developed and is mainly contributed to by 3scale API evangelist, Nicolas Grenie.

We walk through creating a working example whose end result is a searchable catalog that resembles the following - though for simplicity we just add the member element:
![1-api-catalog](https://access.redhat.com/sites/default/files/images/1-api-catalog.png)  

## Pre-requisites
There are 2 simple prerequisites to implement this solution. 
* To implement the first part of this workshop, you’ll just need a free 3scale account - available at https://www.3scale.net/signup/. You will be given a 3scale administration URL, something like: **https://<my-3scale-account>-admin.3scale.net**
* A Github account.

## Implementation
We take the approach of building on the [3scale repository](https://github.com/3scale/3scale-discover-APIs), walking through the end-to-end steps to add a Members API to a new Catalog which we’ll expose on the 3scale [Developer Portal](https://access.redhat.com/documentation/en-us/red_hat_3scale/2.saas/html/developer_portal/).
Go ahead and execute the following steps:
* Upload your OAS (i.e. Swagger) JSON specification to your 3scale account. There are 3 ways to do this:
  * Copy the specification into the Active Docs section of the 3scale Administration Portal. It’s done by Creating a new spec here:
https://<my-3scale-account>-admin.3scale.net/admin/api_docs/services
![active-docs](https://access.redhat.com/sites/default/files/images/2-active-docs.png)  
  * This can also be done using the ActiveDocs Spec Create endpoint in your 3scale API: **https://<my-3scale-account>-admin.3scale.net/p/admin/api_docs#/account_management_api**
![api](https://access.redhat.com/sites/default/files/images/3-3scale-api-menu.png)  
  * This can also be doing using the Import Active Docs section of the [3scale CLI](https://github.com/3scale/3scale-cli/blob/master/docs/import-api-definition.md)

  For convenience I have created a prepopulated one for our Members API [here](https://github.com/tnscorcoran/3scale-discover-apis/blob/master/members-oas-spec.json). This is useful for illustration but to actually use it for API calls, you’ll need to update the spec as described in [API Documentation](https://access.redhat.com/documentation/en-us/red_hat_3scale/2.saas/html/api_documentation/)  

* Download the preconfigured versions of the 4 files required to build the API catalog which I placed in my [github repository](https://github.com/tnscorcoran/3scale-discover-apis):
  * [apidetails](https://github.com/tnscorcoran/3scale-discover-apis/blob/master/apidetails) (the Documentation added per API)
  * [apilist](https://github.com/tnscorcoran/3scale-discover-apis/blob/master/apilist) (the Catalog page itself)
  * [apis.json](https://github.com/tnscorcoran/3scale-discover-apis/blob/master/apis.json) (a JSON spec containing various details on each API )
  * [image for Members API](https://github.com/tnscorcoran/3scale-discover-apis/blob/master/member.jpeg) (image that will appear on the catalog)  

* Upload the 4 files to your 3scale CMS as described in more detail on the [3scale repository](https://github.com/3scale/3scale-discover-APIs):
  * Member's image: Fill in as follows
    ![memberpage](https://access.redhat.com/sites/default/files/images/6-member.png)
  * apidetails. This contains the details of each API when you drill into it. Fill in as follows. Note to click Liquid Enabled: Fill in as follows
    ![api-details](https://access.redhat.com/sites/default/files/images/4-api-details.png)
  * apilist. This is the catalog overview page - which draws its individual catalog entries from apis.json below. Fill in as follows:
    ![apilist](https://access.redhat.com/sites/default/files/images/5-apilist.png)
  * apis.json. Fill in as follows (note empty Layout):
    ![apis.json](https://access.redhat.com/sites/default/files/images/7-1-apis.json_.png)
  * This contains the details **inside apis.json** for each catalog entry - normally an API. The highlighted area should be repeated per API:
    ![apis.json-json](https://access.redhat.com/sites/default/files/images/7-2-apis.json-json-view.png)
    Make your substitutions into the red highlighted elements:
    * Service ID. Get this under your APIs menu:
      ![serviceid](https://access.redhat.com/sites/default/files/images/9-service-id.png)
    * Swagger System name. Same as you entered creating your OAS spec in the first Implementation step above, i.e. member Catalog image for this API you created previous - something like: **https://<my-3scale-account>.3scale.net/images/member** (Note omission of -admin as it’s a Dev Portal asset)
    * Tags. These are strings that when entered in the Search box should return your API.
    * Swagger URL. Dev Portal host followed by /swagger/spec/<oas spec system name>.json, e.g. https://<my-3scale-account>.3scale.net/swagger/spec/members.json
Save then Publish.








