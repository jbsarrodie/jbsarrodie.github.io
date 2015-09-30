[gimmick:Disqus](artchitecture)

Exact meaning of _Business Service_ concept in ITIL ?
===============================================

Note: I wrote this post more than a year ago for internal purpose, but recent discussions about _Business Service_ between [Gerben Wierda](http://masteringarchimate.com/2015/09/24/what-is-wrong-with-this-picture-2) and [Tom Graves](http://weblog.tetradian.com/2015/09/27/why-service-function-and-capability) make me think about it. So I publish it here so that you can enjoin inner contradiction in ITIL itself ;-)

During a discussion with some colleagues, we saw that the concept of _Business Service_ was not clear. This post is an attempt at clarifying this concept and is open to any remarks or criticisms.
 
First, it's important to note that ITIL itself redefined _Business Service_ several times, as you can see by yourself in these (all official) definitions:
 
_Business Service_ in ITIL v2 (Glossary edition 2006)

  * _A Service that is delivered to Business Customers by Business Units. For example delivery of financial services to Customers of a bank, or goods to the Customers of a retail store. Successful delivery of Business Services often depends on one or more IT Services._
 
_Business Service_ in ITIL v3 (Glossary edition 2007)

  * _An IT Service that directly supports a Business Process, as opposed to an Infrastructure Service which is used internally by the IT Service Provider and is not usually visible to the Business. The term Business Service is also used to mean a Service that is delivered to Business Customers by Business Units. For example delivery of financial services to Customers of a bank, or goods to the Customers of a retail store. Successful delivery of Business Services often depends on one or more IT Services._
 
_Business Service_ in ITIL v3 (Glossary edition 2011, latest one)

  * _A service that is delivered to business customers by business units. For example, delivery of financial services to customers of a bank, or goods to the customers of a retail store. Successful delivery of business services often depends on one or more IT services. A business service may consist almost entirely of an IT service – for example, an online banking service or an external website where product orders can be placed by business customers._
 
We can see that the first and latest definition are aligned (a _Business Service_ is delivered to a customers by the Business) but that a clarification has been attempted to include the specific case where a _Business Service_ consist almost entirely of an IT Service. This has led to an important contradiction (cyclic definition introduced in 2007 but solved in 2011):

  * A _Business Service_ is an IT Service that directly supports a Business Process
  * A Business Process contributes to the delivery of a [...] _Business Service_

Understand: A _Business Service_ supports a Business Process which deliver a _Business Service_, thus a _Business Service_ support/delivers a... _Business Service_ !
 
This was due to a badly formulated specific context where we consider an IT Service Provider organisation whose business is to deliver (IT) services to other organisations. In this specific context we can have an IT Service acting as a _Business Service_, but that's obviously not the case in every organisations.
 
So at this point what can we say about a _Business Service_ ? My attempt would be to first tell what it's not: it's definitly not an application. I could then summarize it as "a value delivered to a (potentially internal) customer through a business process".
 
In an attempt to make is even clearer, here is the chain from infrastructure to customer (I've added latest ITIL v3 definitions of concepts):

![](/img/itil-business-service-1.png)

So you may ask what kind of ununderstanding we may face. That's pretty easy: depending on how we consider IT (one would say how we partition architecture) we may see ourself as service provider and thus consider services we deliver to the rest of our Organization as _Business Service_, but that's IMHO a bad way, leading to more confusion. A potential "solution" is (sticking to ITIL v3) to use the concepts of Supporting Services and Core Services:

  * Supporting Service: _An IT service that is not directly used by the business, but is required by the IT service provider to deliver customer-facing services (for example, a directory service or a backup service). Supporting services may also include IT services only used by the IT service provider. All live supporting services, including those available for deployment, are recorded in the service catalogue along with information about their relationships to customer-facing services and other CIs._
  * Core Service: _A service that delivers the basic outcomes desired by one or more customers. A core service provides a specific level of utility and warranty. Customers may be offered a choice of utility and warranty through one or more service options._
 
We could then have the generic (all purpose) case presented before:

  * IT delivers Applications which realise IT Services which are used by Business Processes
 
...and another case for our internal processes:

  * IT uses internal Supporting Services and Processes to provide IT Services which are used by Business (in context of Business Processes or not)
 
This leads us to the following chain:

![](/img/itil-business-service-2.png)

Last (but not least) both chains are fully compatible/aligned with Enterprise Architecture approach (thanks to recent alignment of ITIL and TOGAF for example).


