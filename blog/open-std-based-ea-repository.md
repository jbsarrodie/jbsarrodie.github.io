[gimmick:Disqus](artchitecture)

﻿Open Standards based Enterprise Architecture Repository
=================================================

How to build an efficient CMDB ?
--------------------------------

In this post I'm gonna share with you how I have designed our CMDB through the use of good standards like ITIL, TOGAF, ArchiMate... and some possible usages (for Internal Control Standards for example). But let's start by the begining...
 
For several reasons (that would need a dedicated post) I decided to use [CMDBuild](http://www.cmdbuild.org/en/) as it's an opensource that comes with no model configured (although recently a default configuration named [READY2USE](http://www.cmdbuild.org/en/prodotti/ready2use) is now available), which is nice as this has allowed us to start "from scratch". So, the first thing I did was to define the model, and here comes the standards...

Being used to TOGAF, I decided it's [content metamodel](http://pubs.opengroup.org/architecture/togaf9-doc/arch/chap34.html) was the best choice for a CMDB. And I will explain you why...


A well defined common language
------------------------------
 
In our day to day work, we rely more and more on a network of colleagues and internal service providers. in this context, the entities (or CI) in the CMDB model have to be understandable outside our own context. In other words, we have to find a shared language, a shared (and agreed) definition of these entities.
 
TOGAF offers an answer through the definition of (almost) all entities needed to describe our organisation. As this is the conclusion of several years of experience, I decided not to challenge it, but use it "as is" as much as possible.
 
For example, TOGAF defined a process as follows:

_A process represents flow of control between or within functions and/or services (depends on the granularity of definition). Processes represent a sequence of activities that together achieve a specified outcome, can be decomposed into sub-processes, and can show operation of a function or service (at next level of detail). Processes may also be used to link or compose organizations, functions, services, and processes._

In addition, TOGAF gives us a list of most important attributes:

  * **ID**: Unique identifier
  * **Name**: Brief name
  * **Description**: Textual description
  * **Category**: User-definable categorization taxonomy
  * **Source**: Location from where the information was collected
  * **Owner**: Owner of the architecture entity
  * **Process criticality**: Criticality of this process to business operations
  * **Manual or automated**: Whether this process is supported by IT or is a manual process
  * **Process volumetrics**: Data on frequency of process execution

And those additional attributes are used for to describe a standard process:

  * **Standards class**: Non-Standard, Proposed Standard, Provisional Standard, Standard, Phasing-Out Standard, Retired Standard
  * **Standard creation date**: If the product is a standard, when the standard was created
  * **Last standard review date**: Last date that the standard was reviewed
  * **Next standard review date**: Next date for the standard to be reviewed
  * **Retire date**: Date when the standard was/will be retired
 
Isn't it nice to have all this work already done?


A way to link these concepts each other
---------------------------------------
 
Having a nice set of entities is not enough, a CMDB is all about linking something to something else. TOGAF comes with a whole set of relations between entities. And again, all this is described:

![](http://pubs.opengroup.org/architecture/togaf9-doc/arch/Figures/34_contentfwk6.png)
 
Following our example, TOGAF tells us that these relations are related to process:
Source | Relation | Target
------ | -------- | ------
Process | Involves | Actor
Process | Is guided by | Control
Process | Generates | Event
Process | Resolves | Event
Process | Orchestrates | Function
Process | Decomposes | Function
Process | Produces | Product
Process | Orchestrates | Service
Process | Decomposes | Service
Process | Decomposes | Process
Process | Precedes/Follows | Process
 
 
And a way to classify them
--------------------------
 
Having well defined entities and relations is not enough: we also need some help to classify them. For example, SAP, WebMethods, Oracle Database and Windows are all softwares but obviously not of the same type. Some would say that some are applications, middleware or something else, but how can we all classify them the same way ?
 
Trying to define, agree and document such a classification (in other words a [taxonomy](http://en.wikipedia.org/wiki/Taxonomy_%28general%29)) can be a big challenge and a time consuming activity. Again, TOGAF proposes us the [Technical Reference Model](http://pubs.opengroup.org/architecture/togaf9-doc/arch/chap43.html) (TRM):

And as for the model, the TRM is documented and illustrated

![](http://pubs.opengroup.org/architecture/togaf9-doc/arch/Figures/43_trm_detail.png)

 
But what if I really need something not covered ?
-------------------------------------------------
 
Well, the role of TOGAF is to provide an open standard for architecture that is applicable in many scenarios and situations. Thus, it provides a basic model with the minimum feature set and then support the inclusion of optional extensions (In short, an extension is a group of entities and relations):
 
![](http://pubs.opengroup.org/architecture/togaf9-doc/arch/Figures/34_contentfwk1.png)
 
You can see that several extensions are already defined in TOGAF. In fact, with all these extensions used, the full picture looks like this:

![](http://pubs.opengroup.org/architecture/togaf9-doc/arch/Figures/34_contentfwk8.png)

 
Here comes the ArchiMate extension
----------------------------------
 
If you know TOGAF a little bit, you will perhaps think that it is made for Enterprise Architects (which is true) and thus will not go into detailed things like servers and network devices (which is also true as from a TOGAF point of view they are all Physical Technology Components). So how all this can be effectively used for a CMDB?
 
What we need is something compatible with TOGAF but with more "precise" entities. Such thing exists: it's [ArchiMate](http://pubs.opengroup.org/architecture/archimate2-doc/). With a little work (but helped a lot by public discussions) we can add things like Network, Communication Path, Device and so on. And turns all this into an extension for the model. That's what we did in our CMDB.
 

But also our own custom extension
---------------------------------
 
As nothing is perfect, we also had to add some other entities, but this was really easy because they where included in our own extension which is naturally well integrated with the rest. Obviously, deciding if a new entity is really a new one or a child of another one need some practice, but becomes easier when you get used to TOGAF model and ArchiMate.

 
Why do I think we succeeded in building an efficient CMDB ?
----------------------------------------------------------
 
You could argue that our tool is too young in our organisation do tell that it's a success, and you are right. From my point of view, the success is not in the tool itself but in the model in which all entities are based on agreed standards, that are well documented and allow us to easily share knowledge.


Download
--------

Warning: what follows has been developped for CMDBuild version 1.4. I shall post a more recent version some day, but as of today you have to first install CMDBuild v1.4, launch my queries and then update to CMDBuild latest version.

[Here](https://docs.google.com/open?id=0B0WsokejBIkgQlZyc2stT3lRWEE) you'll find:
  * The SQL queries needed to create classes, domains, lookup, role and menu for TOGAF

	
**Some explanations**

  * All classes (including domaines and attributes) have been created using the official [TOGAF content metamodel](http://pubs.opengroup.org/architecture/togaf9-doc/arch/)
  * As someone may want to extend this model, in fact each TOGAF class is in fact a super class. So I've create real classes to allow the creation of some cards for testing purpose.
  * My recommandation: you can extend this model by creating classes, but don't changes those already created. This will ease migration to futur releases.
  * This should be considered an incomplete but stable version: I still have to create more extensions (read TOGAF for more information, and see below "roadmap") but this setup is used in production.
  * I've followed this naming convention:
    * all classes and domains start with ea_xxx where xxx is the name of the extension (in this case 'core')
    * the "final" classes created to allow card creation is an instance and so ends with "_i"
    * all domains are in the form "ea_extension_source_relation_target" where relation is the name of the [ArchiMate relation](http://pubs.opengroup.org/architecture/archimate2-doc/chap07.html#_Toc309639775) that best match.

The primary purpose of TOGAF is Enterprise Architecture, and this kind of usage is perfect with CMDBuild. But this model can also be used as a starting point for a CMDB: in this case you have to extend it this way:

  * Technology equipments (computer, server, network equipments...) will be derived from "Physical Technology Component"
  * Software (not directly used by business people) will be derived from "Physical Technology Component"
  * Application (software used by business people) will be derived from 'Logical Application Component"

And here is my (sort of) roadmap:
	
  * finish togaf extensions (governance, services, process modelling, data, infrastructure consolidation and motivation)
  * finish an ArchiMate extension to allow some concepts and relations not already present in TOGAF (if needed)
  * create some standard reports (ie: artifact in TOGAF)
 
For my project I needed a way to export Lookups, Roles, Grants and Menu in a portable way (list of insert statements without any hard coded ids). This is needed to promote new configuration from a development platform to a Q&A platform and then to a production platform. As I haven't been able to find such queries, I wrote them and I now sharing them with you. You’ll find them in the “sql” subfolder.

