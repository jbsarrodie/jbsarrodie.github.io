[gimmick:Disqus](artchitecture)

NodeXL - Graph visualisation for better analysis
===========================================

![](/img/nodexl.png)
Here I wanna share with you some knowledge about tools that have helped me in the past and can help you in the future: graph visualisation tools. In this context, a graph is nothing more than vertices (or nodes) interconnected by edges. This can be used to show a lot of relations like people (A reports to B...), physical networks (switch A is connected to switch B...) or anything else. This kind of tools become useful when you have a lot of elements to analyse and a simple spreadsheet is not enough. I my case, it began with and internal audit need: document how our critical applications are linked and what tools runs each interface. Of course all this information is listed in my [CMDB](open-std-based-ea-repository.md) and can easily be extracted, but I needed a better way to show this information, a way that could reveal hidden knowledge.
 
Here comes [NodeXL](http://nodexl.codeplex.com/). NodeXL is a free graph visualisation tool integrated in Excel (so you don't have to really learn a new tool). It allows you to easily list your edges and vertices with any properties you want (some for visualisation -color, size...-, some for your own purpose -technology...-) and creates a visual representation (a network graph) for you in one clic.
 
But visualisation is not enough, It's even better to analyse data. NodeXL allows you to do it with things like:

  * calculate some graph metrics like degree (number of incoming/outgoing edges for a specific node)
  * change node shape, size or color depending on any criteria (including metrics),
  * change edge thickness and color depending on any criteria (including metrics),
  * group nodes ether manually or (better) via an algorithm which will detect cluster (group of highly linked nodes, but loosely connected to the ohers nodes)
  * and many other things to discover by yourself
 
Using these capabilities, you can easily create graphs showing how your main applications are connected (node size is linked to degree, colors are used to distinguish clusters detected by NodeXL).
 
Using this kind of graph, I'm now able to:

  * check for error or inconsistency in application naming in my data source,
  * see and better understand how some applications are linked
  * have a rough idea of applications that have to be kept together in case of DRP, datacenter migration...
