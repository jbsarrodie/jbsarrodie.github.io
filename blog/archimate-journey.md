[gimmick:Disqus](artchitecture)

How to best start your ArchiMate journey
====================================

First of all, in case you still don't know what ArchiMate is, here is a (very) small description:

_ArchiMate is an open and independent enterprise architecture modelling language to support the description, analysis and visualization of architecture within and across business domains in an unambiguous way. In most cases, it can be use instead of BPMN or UML and as an open standard is fully documented. ArchiMate is a technical standard from [The Open Group](http://opengroup.org)_


Best reading for ArchiMate
--------------------------
The best book about ArchiMate is definitely [Mastering ArchiMate](http://masteringarchimate.com/mastering-archimate-edition-ii/) by [Gerben Wierda](http://masteringarchimate.com/about/), now in its second edition. You can buy either an electronic or printed edition. You can also [download a free excerpt](https://rna.dpdcart.com/) presenting (in a very understandable way) ArchiMate syntax. The full book presents a lot of generic patterns to help start using the language, but also some "real life" examples like Organization Charts, Enterprise Service Bus, Citrix...

 
Software to start modelling using ArchiMate language
----------------------------------------------------
One could start using ArchiMate language with just a paper and a pen, or through generic diagramming applications like Visio (there are even "official" stencils published by the Open Group). But in order to see all advantages of such language (being able to work a unique model through several -linked- views being one of the most important) one has to use a dedicated software. Several well known software are ArchiMate compliant (directly or through some add-ons) like ARIS, Mega, BIZZdesign Architect... All have a cost (and are really not cheap), so if you want a powerfull but low-cost entry solution, the best tool is [Archi](archimatetool.com).
 
Archi is an opensource modeller, dedicated to ArchiMate language. It is widely used among ArchiMate "community" (it is used globally by banks, insurance companies, industry, EA consultants, training organisations, universities, and students...).


Software download and basic setup
---------------------------------
Archi is the de-facto standard tool as it's the only opensource modeller available, but without compromising on quality/features. It offers of course modelling but also interactive model navigation, report creation and other features for when you will master the first ones.
 
**Suggested installation steps:**

  * [Download it](http://www.archimatetool.com/download)
  * Download the [Mastering ArchiMate color scheme](http://www.archimatetool.com/downloads/tools/ArchiMasteringArchiMateColours.prefs) that I use and recommend
  * Start Archi and then go to the preference menu (on "Edit > Preference" on Win/Linux)
  * Go to "Colours and Fonts" tab and import the colour scheme

    ![](/img/archimate-journey-1.png)

  * Go on "Connections" tab and enable orthogonal connections

    ![](/img/archimate-journey-2.png)

  * Validate changes through the "OK" button
 
**Remarks and usefull features**

  * Archimate is all about creating a model (set of entities linked together) and use part of it in views. This mean that an object (an application for example) have to be created only once. The most frequent mistake I see is using it like Visio and re-creating objects that already exist on several views: this leads to an unusable and unmanageable model.
  * When you create views, you have two kind of deletions possible: deletion from the view (so element is still present in the model for another use) or deletion from the model. DEL key does the first one, you have to use a contextual menu on elements to "Delete from Model".
  * When you have a view opened, you can use the Hints window to read ArchiMate official description of (view or palette) element selected:

    ![](/img/archimate-journey-3.png)

  * As a "beginner" you will not always know what relations are permitted between elements. The [Magic Connector](http://www.archimatetool.com/movies/magic_connector/magic_connector.html) is here to help you.
 
**Models examples**

  * You'll also find attached the model I use for training purposes. It contains training materials (views under "Concepts" folder) but also architecture patterns (views under "Patterns" folder) for citrix, Oracle, FileBox, Java webapps, webMethods...). Do not forget to open the Properties windows to read comments I made on some views (ArchiMate Training.archimate).
  * The European Customer Portal design (both .archimate file and PDF report file) included in the report ZIP file (EDC_detailed_design_v1.2.zip). See below.


Model and Report templates
--------------------------
You'll find attached report template in the ZIP file (EDC_detailed_design_v1.2.zip), alongside with a documentation (Archi document & report template for EDC.docx) for setup. Also contains a model example (European Customer Portal Platform) and generated PDF file. This template as been designed and use for the France Datacenters Consolidation to EDC project.
 
Hope this will help you start quickly.
