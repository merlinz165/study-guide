---
layout: post
title:  "Verteiltes Rechnen"
ref: verteiltes_rechnen
date:   2018-10-17 07:00:00 +0100
categories: master
excerpt: Die Vorlesung "Verteiltes Rechnen" gibt eine Einführung in die Welt des verteilten Rechnens mit einem Fokus auf Grundlagen, Technologien und Beispielen aus Grid, Cloud und dem Umgang mit Big Data.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/U8oAm94VRIyvtcN-9RuTmg">Verteiltes Rechnen</a>, Vorlesung, 4 ECTS <br>
    <strong>Dozent:</strong>Prof. Dr. Achim Streit<br>
   <strong>ILIAS:</strong> <a href="https://ilias.studium.kit.edu/goto_produktiv_crs_873428.html">https://ilias.studium.kit.edu/goto_produktiv_crs_873428.html</a><br>   
   <strong>Vorlesungswebsite:</strong> <a href="https://www.scc.kit.edu/bildung/11926.php">https://www.scc.kit.edu/bildung/11926.php</a> <br>   
   <strong>Klausur:</strong> schriftlich, Termin noch unklar <br>
   <strong>Einordnung:</strong> Vertiefungsfach "Telematik" und "Parallelverarbeitung", Profil "Datenintensives Rechnen" <br>
</div>

## Organisatorisches

### Vorlesungen
- **17.10.2018**: Organisatorisches und Foliensatz 0-1 bis 0-32
- **24.10.2018**: Foliensatz 1-1 bis 1-34
- **31.10.2018**: Foliensatz 2-1 bis 2-33
- **07.11.2018**: Foliensatz 2-2 bis 2-4
- **14.11.2018**: Foliensatz 3-0 bis 3-2
- **28.11.2018**: Foliensatz 3-3 bis 3-4


### Material
Die Vorlesungsfolien werden im ILIAS hochgeladen. Sämlichte Literatur befindet sich im Skript. Die Vorlesung
findet auf Deutsch statt, die Folien sind auf Englisch.

### Klausur
Die Klausur findet schriftlich statt und dauert 60min. Termin noch unklar, grober Zeitraum Februar/März.
 Zudem ob Klausur auf Deutsch oder Englisch gestellt wird.

## Vorlesungsinhalt
### Opening
**Distributed Computing**: Definitionen aus [Wikipedia](https://en.wikipedia.org/wiki/Distributed_computing):
Components *interact* with each other to *achieve a common goal*; use of distributed systems to *solve computational problems*;
no clear distinction between *concurrent computing*, *parallel computing* and *distributed computing*.   
Definition in *Vorlesung*: Distributed Computing is about *systems* (hard- and software) that *work together*, *geographical distance*, 
problem *solving environment for benefit of their users*; e.g. Web Services, Grid Computing, Cloud Computing

**Metacomputing**: logical integration of several, independent supercomputer via high-performance WAN connections; aggregation of main
memory capacity, computing power → solve big problems, too big for one supercomputer (grand challenge problems e.b. clima simulations)

**Grid**: Term as analogy to electric power grids; Grids harness distributed resources to provide scalable, secure and high-performance mechanisms for discovering resources, negotiating 
the access to resources, using remote resources; share resources and work together e.g. scientific collaborations;  
 Checklist for Grids:
- Coordinates resources that are *not subject to centralized control* (user desktop vs. central computing; addresses securtiy, payment,...)
- Using *standard, open, general-purpose protocols and interfaces* (authentication, authorization, access, resource discovery)
- Deliver *non-trivial qualities of service* (response time, throughput, availability, security, co-allocation; 
utility of combined systems must be greate than sum of its parts)

**Big Data**: Definition by Doug Laney: **V**olume, **V**elocity, **V**ariety; often extended by **V**alue and **V**eracity (=Vertrauenswürdigkeit); 
Important also Privacy, Preservation and Sustainability;  
Scientific Big Data only possible due to extraordinary performance of *Grid Computing*

**Cloud Computing**: no single answer; e.g. Wikipedia: ubiquitous, convenient, on-demand networt access to shared pool of 
configurable computing resource;
- *Scalable:* partitioning of compley workflows in adaptive infrastructures
- *Flexible:* variety of workloads (consumer, business)
- *Fully-automatic:* resources on demand
- *Business modell:* utility computing, pay-per-use, pay-as-you-go
- *Service oriented architecture:* dynamic procision of resources via web services interfaces
- *Virtualisation:* arbitrary, customer-desired view on resources; location and type of resources transparent for user  
→ **Web Services + Virtualisation = Cloud Computing**

Unterscheidung Grid Computing - Cloud Computing:
> **Grid Computing:** nicht kommerziell, jeder bring Ressourcen ein; früher große Grid-Infrastrukturen → heutzutage nichtmehr da für kommerzielle Anbieter
kein Gewinn; Grid Computing für wissenschaftliche Zwecke, keine zentrale Kontrolle; z.B. GritKA  
**Cloud Computing:** agil, eingach zu nutzen, vor allem aber schnell; z.B. AWS

### Introduction
#### Distributed Systems & Middleware
> A **Distributed Systems** is a collection of independent computers, appear to user as single coherent system,autonomy of individual computers, 
single-system view

not visible for user if individual computer or distributed system; interaction with DS in uniform, consistent manner; 
should be **scalable**, **extensible** (Systeme auch herausnehmbar, können ausfallen) and **fault tolerant**; Grid infrasturcture is highly dynamic 
distributed system offering non-trivial qualities of service   
Examples: DesktopGrid (workstations not in use, single 
file system, commands typed locally → executed on available machines; act like single-processor time-sharing system), World Wide Web (simple, 
consistent and unifrom model of distributed documents, publishing documents via URL)    

Goals of Distributed Systems:
- **Connecting users and resources**: 
    - *Access*: to remote resources e.g. hardware, software, services 
    - *economical:* sharing supercomputer 
    - *collaboration and exchange of information*
    - *security mechanisms:* access to trusted users, accepting only secure resources 
    - *billing and accounting:* billing = Preis, Rechnung, nur mit accounting = Sammeln von Nutzerdaten, aber accounting ohne billing möglich
- **Transparency**:  
    - *Access:* hide **differences in data representation** e.g byte order, **how** accessing resource
    - *Location:* hide **where** resource is located
    - *Concurrency:* hide that resource may be shared with **competitive users**, consistency still important
    - *Failure:* hide **failure and recovery**
- **Openness**: 
    - *Access*: Protocols (specify format), Interfaces (specify syntax) and Semantics (hard to specify; informal e.g. comments) to standardize rules 
    how to access functionality
    - *Interoperability:* implementations should work together through each others interface specifications
    - *Portability:* implementation should run on different systems implementing the same interfaces
    - *Flexibility:* easy configuration of system with different components
- **Scalability**:
    - *Size:* large number of users/resources; main bottleneck: centralization
    - *Geographical extent:* main bottleneck: latency of wide-area, syncronous, unreliable communication e.g. transatlantic
    - *Administrative domains:* no trust, restrictions make systems more complex; → establish a trust relationship (e.g. certificates)
   
*Ende der Vorlesung vom 17.10*
    
#### Web Services
> A **Web Service** is a *new middleware technology* for *machine-to-machine* interaction, can be accessed through *web protocols* (e.g. http),
 provides an *interface* (web API), typically *registered*, located through registry, *loosely coupled connections* between systems

Web Services are not for users, only connection technology, behind the scenes, users should not know that they are using Web Services, form
basis of modern Grids  
Advantages of Web Services:
- Loosely coupled
- Platform independent (datatypes as XML)
- Language independent
- Self-describing (WSDL, XML-Schema)
- coexistence with firewalls 
- separation of interface definitions from their embodiment
- simplicity and extensibility
Disadvantages of Web Services:
- data conversion overhead (from and back to XML)

*Examples for Web Services:*
- Models and metamodels: Web Services Resource Frameword (WS-RF)
- Service description and metadata: Web Services Description Language (WS-DL) 

**Web Service Description Language (WSDL)**: defines message syntax for invocation and response of WS (messages part of data layer); WSDL is XML-document;
**WSDL is not used during communication!**, web service provider exposes its WSDL file; currently WSDL 1.1
Three parts:
- *What a service does:* operations with parameters, return type
- *How to access service:* data formats, protocols
- *Where a service is:* protocol-specific network address  
*WSDL Tooling:* WSDL interface provided by service provider, machine readable; stub, skeleton can for communication parts can be automatically created 
→ concentrate on logic, contents

**Extensible Markup Language (XML)**: Defines generic syntax to mark up text with tags; human- and machine-readable; XML is trimmed
down version SGML, HTML is SGML application  
*Well formed* XML:
- start/end tag
- may nest, but may not overlap
- exactly one root element
- attributed values are quoted
- within one element no two attributes with same name
- no comments or processing instructions inside tags
- no unescaped illegal characters

#### Web Services Resource Framework (WSRF)
Service interfaces often need stateful interaction between sclients and service, WSRF defines a generic framwork for modeling and 
accessing stateful resources using Web services → XML document to describe state of resource, Specifications of WSRF:
- **WS-Resource**: defines WS-Resource as combination of resource and Web Service to access resource
- **WS-ResourceProperties (WSRF-RP)**: defines messages to query or update property values
- **WS-ResourceLifetime (WSRF-RL)**: defines messages to detroy resource, monitor lifetime
- **WS-ServiceGroup (WSRF-SG)**: to form variety of collections of services
- **WS-BaseFaults**: set of information that my appear in fault messages
(siehe Folien 1-34)

*Ende der Vorlesung vom 24.10*

### Grid
**Grid**: internet infrastructure; harnessing (nutzbar machen) distributed ressources, provide
scalable, secure, high-performance mechanisms; enables scientific collaborations (virtual
organizations) to share ressources; Grid ist Analogie zu "Electric powe grid"; Konzept bereits seit 1965 bekannt

**Grid Checklist**: <span style="color: red">Prüfungsfrage in Altklausuren!</span>  

|         |     Grid       | Cloud  |
| ------------- |-------------| -----|
| **Control**      | keine zentrale Kontrolle, keine Kontrolle über andere Standorte des Grids | zentrale Kontrolle, Anbieter mit wirtschaflichem Interesse (z.B. Amazon) |
| **Protocols & Interfaces**      | standardisierte, offene, general-purpose Protokolle (Authentication, Authorization, Resource Discovery, Access      |   keine standardisierten Interfaces, Hinterrund ist "vendor"-Login (Kundenbinding, kein einefacher Umstieg auf die Konkurrenz) |
| **Quality of Service** | nicht-triviale Dienstgüte (response time, throughput, availability, securtiy, co-allocation); Kombination der Systeme muss Mehrwert liefern      |  triviale Dienstgüte |

**Meta-Computing**: logische Integration unabhängiger, heterogener, paralleler Computer
mit high-performance WAN Verbindungen zu einem System; verteilen einer Anwendungen über
mehrere Supercomputer; kann Probleme (schneller) lösen, die mit einem Supercomputer 
nicht lösbar sind; Fokus aufs Rechnen alleine

**Klassifikation von Grids**: by resource type shared/technology used
- *Compute Grids*: access to computational resources, classification by hardware:  
    - Desktop Grids
    - Server Grids
    - HPC/Cluster Grids
- *Data Grids*: transparent, secure, high-performance access to federated data sets (flat-file, relational, streaming data)
- *Peer-to-peer Grids*: storage capacity of individual computer workstation shared
- *Collaborative Grids*: resource is human expertise, human interaction across geograophical distances

Klassification organizal/geographic range: Department Grids, Enterprise Grids, Global Grids, Utility Grids, Service Grids

#### Architecture
**Anatomy of Grids**: middleware architecture, layered protocol stack; follows *hourglass model* 
(= small set of core abstractions to allow diverse application to be mapped onto diverse set of resources); e.g. APIs, SDKs
(vgl. Abb. s.18, Kapitel 2.0-2.1); Hourglass Neck = Resource & Connectivity in Protocol Stack  
Layers: bottom up
- *Fabric Layer:* sharing of resources, resource-specific operations; Enquiry Mechanisms, Management Mechanisms
- *Connectivity Layer:* core communication protocols, authentication protocols
- *Resource Layer:* sharing of single resources, information protocols, management protocols
- *Collective Layer:* coordinates multiple resources, directory services, co-allocation, scheduling, brokering services, data replication

**Physiology of Grids**: service-oriented architecture based on Web Services technology: *Open Grid Services Architecture (OGSA)* =
standardized framework; includes set of basic interfaces to access state of resource

**Open Grid Services Architecture Capabilites**:
- *Resource management services:* management of resources themselves, resources in grid, OGSA infrastructure
- *Security services:* Authentication, Authorization, Audit, non-repudiation, Privacy and secure conversations
- *Self-management services:* Monitoring, fault-tolerance, self-healing, analysis and projection
- *Information services:* Naming, Logging, Monitoring, Message delivery   
→ Framework for grid structures

#### Security
**Security Requirements in Grids**: 
- *Identification of individuals:* private key per user, needs to be protected
- *Single sign-on* 
- *Uniform credentials/certification infrastructure:* standards such as X.509
- *Interoperability with local security solutions:* ressources with different authentication, authorization mechanisms
- *Support for multiple implementations:* based on public od symmetric key cryptography

**Digital Certificate**: signed by *certification authority (CA), Certificates contain public key, user shows authentication: presents certificate, proves
that he knows private key, most commonly used X.509

**Public Key Infrastructure (PKI)**: only a single CA → do not scale → chain of trust needed → PKI; Registration 
Authority (RA) issues certificates in name of CA

**Certification Authority (CA)**:issues certificates for servers, individuals on request, defines policy for whom certificates 
are issued, under which conditions, maintains *Certificate Revocation List (CRL)*, answers question in certification
issues

**Registration Authority (RA)**: field office of CA, accepts request for certificates, checks identities, issues no own 
certificates

**Short-Lived Credential Service (SLCS)**: easiest way to hide certificates from user → Idea: use existing credential to issue 
short-lived certificates automatically; commonly used *Shibboleth*

**Shibboleth**: Online-CA issuing short-lived X.509 certificates based on authentication at Shibboleth Identity Provider, ~ 11 days, 
easy generation from command line, can be reissued many times

#### Job Submission
**Job**: work to be executed, requires CPU and memory, possibly accesses additional resources (storage, devices, services,..)

**Resource**: Compute (characterized by memory, CPU/core, nodes threads/tasks), Data (Characterized by size, transfer, rate), 
Network (Characerized by bandwidth, latency)

**Differentiation of Computer Systems**:
- *Number of User:* single-user, multi-user
- *Usage:* personal computers, servers, supercomputers
- *Number of CPUs:* single processors, multi processor (e.g. clusters)

**Cluster Systems**: every node acts as independent system with own OS; former times: interprocess-communication through network; today:
particular with multi-core porcessors, cluster system are hybrid systems  
*Usage:* user/job resource demands greater than available resources → competition of users and jobs, typically resource requirements differ
from user to user (large/small, long/short) → * resource management & job scheduling required

**Job Sumission Description Language (JSDL)**: describing (job and resource) requirements of computational jobs fo submissions to Grids and
other systems, also used between middleware systems for submitting to grid middleware (→ interoperability); does not definde submission
interface, what result of submission looks like, how resources are selected 
→ JSDL can not be directly submitted to Grid resources

**Steps to run grid job**: 
1. *Resource discovery:* determine set of suitable resources, static information on resource availabilty status, usage policies, authorization
filtering, minimum requirement filtering; Problem: discovery may not revealed all resource details
2. *Resource selection and allocation:* dynamic information gathering (detailed information of possible resources), Assigning resources to job, 
verifying that match still valid, allocation of resources
3. *Executing and job management:* initiating/submitting, monitoring, managing jobs, handling and staging of all job data, 
coordinating scheduling of multi-step jobs

#### Infrastructures
> Grid Technology is storing and analyzing data from the LHC, can also be used by other data intensive projects

**WLCG Hierarchy**:
- *Tier-0:* accelarator center at CERN, recording raw data, long-term data curation
- *Tier-1:* regional centers (GridKA), managing permanent, online data storage (raw, simulated and processed data), data intensive analysis, 
reprocessing of raw data
- *Tier-2:* national centers, end-user analysis

### Big Data
#### Introduction
**Four pillars of Science**:
- Experiment
- Data
- Simulation
- Theory

**Scientific Data Pyramide**:
- Publications with data
- Processed Data and data representations
- Data collections and structured databases
- Raw data and data sets

**Big Data**: Doug Laney’s 3 V’s:
- *Volume:* Umfang, Datenvolumen
- *Velocity:* Geschwindigkeit, mit der die Datenmengen generiert und transferiert werden (Data Taking, Ingest, Analysis, Transfer, Visualization)
- *Variety:* Bandbreite der Datentypen und -quellen (Data Sources, Data Formats, Workflows, Analysis Methods)

Often extended by:
- *Veracity:* Vertrauen (Systemic and statistical uncertainites, biased sample)
- *Value:* Mehrwert der Daten (non-reproducable data, (high) costs of reproduction)

Additional:
- *Variability:* Changing Data, Changing Models, Linkage

#### Management at LHC
**Data Analysis at LHC**: Reconstruction (reconstructing physical reactions from energy depositions in detector, 
time consuming, rentrally organized → Tier-1), "Monte Carlo" (simulated events, for specific physical processes → Tier-2),
 User Analysis (specifiv processes and parameters, low efficiency on raw data → coupled in analysis trains → Tier-2 (Tier-3))
 
**Data Management at LHC**: sites with data run storage elements, file access via grid commands, potential problem "dark data"

**Dark Data:** [Wikipedia](https://de.wikipedia.org/wiki/Dark_Data): "Als Dark Data bezeichnet man Daten, die zwar von 
Informationssystemen erfasst und gespeichert werden aber nicht verwendet werden. Bei großen Datenmengen (Big Data) können 
viele Daten entstehen, die nicht alle analysiert 
oder betrachtet benutzt werden und so kommt es dazu das man sich über die Existenz der Daten nicht mehr bewusst ist."

#### Data Stewardship, Curation and Preservation
**Data Stewardship**: Responsible use and protection of digital assets through management, infrastructure support and sustainable
practices, Tasks:
- creating/maintaining consistent metadata
- handling data ownership
- ensuring data preservation
- facilitating data curation

**Data Preservation**: Actions undertaken to ensure *long-term* viability and availability of digital assets, long-term:
might be forever (at least 5-10 years), includes changing technologies, new data formats, new user communities   
*Preservation ensures:*
- authenticity
- reliabilty
- usability
- integrity

**Bit-stream preservation**: physical preservation of data objects on "bit level"  
*maximizing data-reliabiliy:* 
- Redundant storage
- Hetrogenoeous, standardized storage technologies
- replication to remote site
- refreshment
- periodically exchanging technologies
- security and disaster planning

*Entities:*
- File: Corrupted media, disk failure (1 year)
- Tape: Simulatenous failure of 2 copies (5 years)
- System: Systemic errors in vendor, malicious user, operator error (15 years)
- Archive: natural disaster, obsolescence of standards (50-100 years)

**Data Curation**: Maintaining and adding value to trusted body of digital information for current and future use; data
curation is typicall user initiated and maintains metadata rather than database itself; Aspects of use: Accessibilty and digital
rights management, Aspects of value: annotations, linking to related data, improving and updating documentation

#### Open Access
**Classical Scientific Publishing
1) Authors submit article
2) peer-review
3) Publication of corrected article
4) allow others to access atrticles

**Open Access**:
- *Green Open Access:* publish work, self-archive manuscript, responsibility with author
- *Gold Open Access:* publish work so its immediately available from publisher, charge, freely available online via publishers website
- *Hybrid Open Access:* business model of publisher is partially based on fees, provides gold open access only for those their authors paid a fee

*Open Access in Practice:* publishers of "cash cow" journals are at risk; Possibilities to stop that: make journal hybrid, 
convert journal to gold, create companion journal

**Double dipping**: double payment to publishers, Subscription fees + article processing charge   
*Avoid Douple Dipping:* price reduction from publishers to subscription fee for articles that have been made Open Access, but the
price reduction is often incomprehensible and irreproducible.
- *Advantages*: simple model that can be realized easily
- *Disdvantages*: non-transparent prices, no benefits for those who pay for a lot of article processing charges

#### Metadata
> **Metadata** is data that provides information about other data; short: metadata is data about data

**Examples of metadata for data**: means of creation of the data, purpose of the data, time and date of creation, 
creator or author ot data, location on computer network where data was created, standards used, file size

**Metadata Types**: 
- *Administrative:* Acquisition and location information, Documentation of legal access requirements
- *Descriptive:* title, abstract, data creator, keywords, annotations by users
- *Technical:* formats, compression ratios, scaling routine, Authentication and security data
- *Preservation:* documentation of physical condition of resource, documentattion of actions taken to preserve physical and digital versions
- *Use:* use and user tracking

**Dublin Core Metadata Element Set**: is a small set of core vocabulary terms to describe web resources and physical resources 
([Wikipedia](https://en.wikipedia.org/wiki/Dublin_Core))
1) *Title:* A name given to the resource  
2) *Creator:* An entity primarily responsible for making the resource  
3) *Subject:* The topic of the resource  
4) *Description:* An account of the resource  
5) *Publisher:* +An entity responsible for making the resource available  
6) *Contributor:* An entity responsible for making contributions to the resource  
7) *Date:* A point or period of time associated with an event in the lifecycle of the resource  
8) *Type:* The nature or genre of the resource  
9) *Format:* The file format, physical medium, or dimensions of the resource  
10) *Identifier:* An unambiguous reference to the resource within a given context  
11) *Source:* A related resource from which the described resource is derived  
12) *Language:* A language of the resource  
13) *Relation:* A related resource  
14) *Coverage:* The spatial or temporal topic of the resource, the spatial  
   applicability of the resource, or the jurisdiction under which the resource is
   relevant  
15) *Rights:* Information about rights held in and over the resource  

#### Map Reduce
**Reasons for MapReduce**: *Massive data* cannot be stored on a single machine. It takes too long to process in serial. 
*Application developers* have little experience with large amount of data and only some experience with parallel 
computing. → problems

**Map Reduce**: is a simple programming model from *Google*. (Hadoop: MapReduce implementation for clusters). 
Map Reduce is a *Programming model for processing large scale data* with automatic parallelization, that is friendly
to procedural languages and scalable with peta bytes data on thousands of machines.   
The *basic data type* is a *key-value pait(k,v)* (e.g. key=Url, value=HTML on a web page).  
Data processing is based on a *map step* and a *reduce step*. A map operation is applied on each logical "record" in the input
to generate intermediate values. Followed by the reduce operation to *merge* the same intermediate values. To process
data with MapReduce, it is neccessary that the data is *independent*!   
*Application:* web data processing, data mining an machine learning, log file analysis  
*Anatomy:* *Mappers* transform input record into intermediate records. *Reducers* reduce a set of intermediate valures, which share
a key to a smaller set of values.

(inser imt anatomy-mapreduce.png)



**Example "WordCount":** This example simply counts the occurence of each word in a text. Therefore
the data has to be separated at first. The data here is already splitted. 

(insert img wordcount.png)

**Example "PageRank":** PageRank uses the link structure of the web to find the "best" pages. Good pages are linked by 
many other web pages. There are several formulations for this problem:
- *Voting system:* the rank of a page is based on the weighted votes of pages linking to that site
- *Eigenvector-Problem:* Ar = r where r ist the vector containing the ranks of all pages and A is the ajacency matrix
- *Random Walk/Markov Chains:* If a surfer randomly surfes the web, the page rank expresses the probability of the surfer accessing
a certain page in a given time.   
 
*Simplified Algorithm:* sum of all PageRanks (PR) is between 0 and 1, we have four web pages, initial PageRank is evenly ditributed: 0.25;
$PR(u) = \frac{1-\beta}{N} + \beta \sum_{v \in B_u} \frac{PR(v)}{L(v)} $ where $\beta$ is a scalar damping factor to get rid or *dead
ends* (no outgoing edges) and *spider traps* (page is linking itself) $\beta$ is usally around 0.8; set $B_u$ contains all pages
linking to page u; L(v) is the number of links from page v (outbound links). Iterate algorithm until result converges.   
For given image: $PR(A) = \frac{PR(B)}{2} + \frac{PR(C)}{1} + \frac{PR(D)}{3} = 0,458$
(insert img pagerank.png)

Map emits: key is vertex, value is endpoint of outgoing link devided by the amound of outgoing links
- (A, B/2), (C, B/2)
- (A, C)
- (A, D/3), (B, D/3), (C, D/3)
Reduce gets: combine values for each vertex
- (A, [B/2, C, D/3])
- (B, [D/3])
- (C, [B/2, D/3])



