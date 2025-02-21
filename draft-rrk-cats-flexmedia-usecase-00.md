---
title: "Challenges and Use Case for the Deployment and Operation of Flexible Media across the Internet"
abbrev: "Flexible Media Use Case"
category: info

docname: draft-rrk-cats-flexmedia-usecase-00
submissiontype: IETF
number:
date:
consensus: true
v: 3
area: AREA
workgroup: Compute Aware Traffic Steering (CATS)
keyword:
 - Flexible Media
 - Traffic Steering
 - Compute Metrics
venue:
  group: WG
  type: Working Group
  mail: WG@example.com
  arch: https://example.com/WG
  github: USER/REPO
  latest: https://example.com/LATEST

author:
- 
  fullname: Rajiv Ramdhany
  organization: BBC
  email: rajiv.Ramdhany@bbc.co.uk
- 
  fullname: Nicholas Race
  organization: Lancaster University
  email: n.race@lancaster.ac.uk
- 
  fullname: Daniel King
  organization: Lancaster University
  email: d.king@lancaster.ac.uk

normative:

informative:

--- abstract

This document outlines the challenges and use cases for deploying and operating Flexible Media across the Internet. It discusses key considerations such as compute-aware traffic steering, bandwidth optimization, latency reduction techniques, and personalization algorithms.

--- middle

# Introduction

Traditional media broadcasts, in both radio and video, broadcast a packaged, edited, single linear stream of information to all users regardless of playback device or environmental factors. Object-based media represents a significant shift from traditional media production and broadcasting methods, focusing instead on creating, storing, and transmitting media as a collection of discrete objects (such as audio, video, or text elements) rather than a single, unchangeable stream. This approach allows for media to be more interactive, adaptable, and personalised to individual viewers or listening environments, offering several advantages for the future of television and other media experiences.

Flexible Media (FM), or Object-based (OBM) media, enables content to be tailored to individual preferences or requirements. For instance, a viewer could adjust the level of background music in a program, switch between different camera angles, or select which storyline to follow in a complex narrative. This level of personalisation enhances viewer engagement and satisfaction. It can greatly improve accessibility features for diverse audiences. For example, audio descriptions for the visually impaired or sign language for the deaf can be seamlessly integrated and toggled on or off according to the viewer's needs. This inclusivity broadens the potential audience for content.

It is important to use Internet bandwidth, especially at scale, efficiently; broadcasters can use bandwidth more efficiently by transmitting only the objects necessary for a particular viewer's experience. This is particularly beneficial in environments with constrained bandwidth or users with limited data plans. FM media can be designed to be compatible across various devices and screen sizes, ensuring a consistent user experience whether the content is viewed on a smartphone, tablet, or large television screen. This scalability is crucial to the variety of devices and screens. 

FM Content may be stored using Content Delivery Networks (CDNs), which are designed to efficiently distribute digital content—such as multimedia files and live streams—over IP networks to numerous endpoints and viewers. Typically, a CDN includes one or more servers responsible for delivering digital objects or streams. Additionally, it features a management or control system that handles various operations such as content distribution, request routing, reporting, metadata management, and other functionalities essential for the system's performance.


# Conventions and Definitions

{::boilerplate bcp14-tagged}

The following terms are used in this document:

* AI: 
Artificial Intelligence aims to create systems capable of performing tasks that typically require human intelligence, such as understanding natural language, recognizing patterns, and making decisions.

* Clients: 
Media playback applications are designed to request and ingest flexible media content.

* Edge Computing:
Edge computing is a computing pattern that moves computing infrastructures, i.e, servers, away from centralized data centers and instead places it close to the end users for low latency communication.

* Network Edge:
The network edge is an architectural demarcation point used to identify physical locations where the corporate network connects to third-party networks.

* Objects: 
Assets that are used to make a piece of content.

* Scheduler:
Instantiates executors for jobs at a local controller based on the resources available at the compute site where the system resides.

* Service: 
A media stream of user-generated personalised content.

* Service identifier:
An identifier representing a service, which the clients use to access it.

# Significance of Flexible Media and Internet Usage

A Flex Media (FM) service is personalised media such as stories, audiobooks, and games. This content is generated based on user preferences and experiential learning, ensuring a tailored experience. It employs multi-directional delivery methods, allowing user-generated content and personalised media to thrive. This "software-powered content" caters to end-users, the primary recipients and participants in this dynamic ecosystem.

From a network distribution perspective, FM media requires a robust and flexible delivery infrastructure capable of handling the dynamic assembly of content based on user interactions and preferences. This necessitates advanced content delivery networks (CDNs) and edge computing solutions that efficiently process and deliver personalised content streams. Moreover, the scalability of this approach is critical, as it must support a potentially vast number of unique user experiences generated from the same set of media objects. By separating media components, creators can offer multiple versions of content tailored to different needs, such as alternative audio tracks for different languages or visually impaired audiences requiring descriptive audio. This level of adaptability not only enhances the user experience but also broadens the audience's reach.

## Previous IETF work on Video Media Delivery across Internet Infrastructure

The Internet Engineering Task Force (IETF) has been involved in numerous initiatives and has developed various standards and protocols to improve and facilitate video media delivery across Internet infrastructure. 

* Real-Time Streaming Protocol (RTSP):
Defined in {::RFC2326}, RTSP controls streaming media servers. RTSP is designed to control media sessions between endpoints and acts as a network remote control for multimedia servers.

* Real-time Transport Protocol (RTP): 
Specified in {::RFC3550}, RTP delivers audio and video over IP networks. It is widely used in streaming media systems, video conferencing, and push-to-talk features (VoIP).

* RTP Control Protocol (RTCP):
Defined alongside RTP in {::RFC3550}, RTCP provides out-of-band statistics and control information for an RTP flow. It monitors transmission statistics and quality of service (QoS) and aids in synchronisation between different streams.

* HTTP Live Streaming (HLS):
While initially developed by Apple and not originally an IETF standard, HLS has become widely adopted for online streaming live and on-demand video content. The IETF has documents that discuss HLS within the context of internet infrastructure, such as {::RFC8216}.

* Media Over QUIC (MoQ):
TBA

# Deploying Flexible Media Services

Unlike traditional media formats, OBM treats media elements as independent objects that can be orchestrated at runtime. This document outlines the use cases and requirements for OBM, emphasising the role of the IETF Compute-Aware Traffic Steering (CATS) initiative in optimising the delivery of OBM content. Key components of OBM include:

* Media Objects:
Discrete elements such as video segments, audio layers, and metadata.

* Orchestration Engine:
Determines how objects are assembled based on contextual factors.

* Delivery Mechanisms:
Network protocols and architectures enabling object transport and synchronisation.

The dynamic nature of OBM necessitates advanced traffic steering mechanisms that can adapt to compute and network constraints in real-time.

## Compute Aware Traffic Steering

Deployment of OBM services introduces several technical challenges, particularly in the context of Compute Aware Traffic Steering (CATS). Real-time adaptation of compute resource usuage is a major challenge, as media objects must be dynamically composed and delivered based on changing network and compute conditions. Synchronisation across distributed compute nodes is also essential, ensuring coordinated media object delivery and processing across edge, cloud, and on-premise compute resources. As the process is managed an aditional challange of Quality of Experience (QoE) management, where compute resource usage must be balanced with perceived quality improvements to enhance the user experience, is also required.

To support OBM delivery, compute-aware traffic steering must fulfil several requirements. It must possess dynamic compute resource awareness, allowing assessment and adaptation to available compute power along the delivery path. Multi-layer orchestration is necessary to coordinate network-layer traffic steering with application-layer OBM composition. Low-latency compute routing is crucial for minimising processing delays in interactive media experiences. Additionally, scalability and load balancing are needed to ensure efficient distribution of media object processing, preventing compute bottlenecks. Lastly, edge-aware optimisation should be integrated to leverage edge computing for latency-sensitive OBM applications.

## Bandwidth Optimisation Strategies


## Latency Reduction Techniques

# Architecture for Flex Media


   {{fig1}} AI4ME Network Architecture

~~~~
   +-------------------------------------+
   |     BBC Flex Media Orchestrator     |
   |  +------------------------------+   |
   |  |  Object Media Queue Manager  |   |
   |  | +--------------------------+ |   |
   |  | | Personalised Media Queue | |   |
   |  | +--------------------------+ |   |
   |  | | Personalised Media Queue | |   |
   |  | +--------------------------+ |   |
   |  | | Personalised Media Queue | |   |
   |  | +--------------------------+ |   |
   |  | | Personalised Media Queue | |   |
   |  | +--------------------------+ |   |
   |  +------------------------------+   |
   |          |                |         |
   |  +--------------+  +--------------+ |
   |  | Job Scheduler|  | Job Scheduler| |
   |  | Compute Alloc|  | Compute Alloc| |
   |  +--------------+  +--------------+ |
   +-------------------------------------+
           |               |
           v               v
   +-----------------------------+
   |  Compute & Object Resource  |
   |  +-----------------------+  |
   |  | Distributed Compute   |  |
   |  |  Grid (Nodes/Jobs)    |  |
   |  +-----------------------+  |
   +-----------------------------+
            |
            v
   +-----------------------------+
   |   Network Orchestrator      |
   |  +-----------------------+  |
   |  |     Core Network      |  |
   |  |  (Cloud & Telecom)    |  |
   |  +-----------------------+  |
   |      |       |      |       |
   |  +------+ +------+ +------+ |
   |  | Metro| | Metro| | Metro| |
   |  +------+ +------+ +------+ |
   |      |       |      |       |
   |  +--------+  +--------+     |
   |  |  Users |  | Devices|     |
   |  +--------+  +--------+     |
   +-----------------------------+


                                     +-------------------------------+
                                     |   BBC Flex Media Orchestrator |
                                     |  +-------------------------+  |
                                     |  | Policy Decision         |  |
                                     |  | Site Manager            |  |
                                     |  | Site Observer (Cloud)   |  |
                                     |  +-------------------------+  |
                                     +-------------------------------+
                                                               |
                                                               |
+----------------+       +-----+       +----------------+      |
|     Client     |------>| CDN |<----->|    Storage     |      |
+----------------+       +-----+       +----------------+      |
       |                                 |                     |
       |                                 v                     |
       |      +------------------------------------+           |
       |      |        FM Ingress Site             |           |
       |      | +------------+    +-------------+  |           |
       |----->| | Media Switch|-->|   Cache     |  |           |
       |      | +------------+    +-------------+  |           |
       |      | | Job Board   |   | Scheduler   |  |<----------|
       |      | | Board Ctrl  |   | Flex Media  |  |           |
       |      | | CDN PoP     |   | Net Perf    |  |           |
       |      | +------------+    +-------------+  |           |
       |      +------------------------------------+           |
       |                                                       |
       v                                                       |
+----------------------------------+                           |
|         Compute Site             |<--------------------------+
| +----------------+  +---------+  |
| | Media Server 1 |->| Jobs    |  |
| | Media Server N |->| Storage |  |
| +----------------+  +---------+  |
| +-------------------------------+|
| |  Media Orchestrator            |
| +--------------------------------|
| |  Site Controller  | Allocator  |
+----------------------------------+
~~~~
{: #fig1 title="Figure 1: AI4ME Network Architecture" artwork-align="center"}


# Compute and Network Estimates

   {{fig2}} Compute Estimates

~~~~
Compute Estimates: Narrative Versioning

+-----------------------------------------------------------+
|Number of Users | Worst Case | Best Case (90% Cache Hits)  |
+----------------+------------+-----------------------------+
| 10,000 users   |  45 nodes  |  5 nodes                    |
| 250,000 users  | 1,125 nodes| 113 nodes                   |
| 1,000,000 users| 4,500 nodes| 450 nodes                   |
+----------------+------------+-----------------------------+

Compute Estimates: Layered Compositing

+-----------------------------------------------------------+
|Number of Users | Worst Case  | Best Case (90% Cache Hits) |
+----------------+------------+-----------------------------+
| 10,000 users   | 111 nodes  |  84 nodes                   |
| 250,000 users  | 2,775 nodes| 2,082 nodes                 |
| 1,000,000 users|11,100 nodes| 8,325 nodes                 |
+----------------+------------+-----------------------------+

Compute Estimates: Rendered Objects

+-----------------------------------------------------------+
|Number of Users | Worst Case  | Best Case (90% Cache Hits) |
+----------------+------------+-----------------------------+
| 10,000 users   | 138 nodes  | 104 nodes                   |
| 250,000 users  | 3,450 nodes| 2,600 nodes                 |
| 1,000,000 users|13,800 nodes|10,400 nodes                 |
+----------------+------------+-----------------------------+

Compute Estimates: Non-Graphical

+-----------------------------+
|Number of Users | Worst Case |
+----------------+------------+
| 10,000 users   | 10 nodes   |
| 250,000 users  | 250 nodes  |
| 1,000,000 users| 1,000 nodes|
+----------------+------------+

{: #fig1 title="Figure 2: Compute Estimates" artwork-align="center"}

Bandwidth Requirements: User

+------------------------------------------------------------------------------------------------------------------------------------+
| Type                 | Number of Users | HD Bandwidth   Req. (Mbps)     | 4K Bandwidth Requirement (Mbps) | Total Bandwidth (Gbps)|
+----------------------+----------------+---------------------------------+--------------------------------+-------------------------+
| Narrative Versioning | 10,000         | 25,000 - 40,000                 | 75,000 - 125,000               | 100 - 165               |
|                      | 250,000        | 625,000 - 1,000,000             | 1,875,000 - 3,125,000          | 2,500 - 4,125           |
|                      | 1,000,000      | 2,500,000 - 4,000,000           | 7,500,000 - 12,500,000         | 10,000 - 16,500         |
| Layered Compositing  | 10,000         | 25,000 - 40,000                 | 75,000 - 125,000               | 100 - 165               |
|                      | 250,000        | 625,000 - 1,000,000             | 1,875,000 - 3,125,000          | 2,500 - 4,125           |
|                      | 1,000,000      | 2,500,000 - 4,000,000           | 7,500,000 - 12,500,000         | 10,000 - 16,500         |
| Rendered Objects     | 10,000         | 25,000 - 40,000                 | 75,000 - 125,000               | 100 - 165               |
|                      | 250,000        | 625,000 - 1,000,000             | 1,875,000 - 3,125,000          | 2,500 - 4,125           |
|                      | 1,000,000      | 2,500,000 - 4,000,000           | 7,500,000 - 12,500,000         | 10,000 - 16,500         |
+------------------------------------------------------------------------------------------------------------------------------------+
~~~~

# Metrics

In traditional routing systems, often network path costs may not change frequently unless there is a resource failure or planned outage, whereas network traffic engineering metrics, such as available bandwidth, may fluctuate more dynamically. However, the computation-oriented metrics relevant to OBM can be highly variable, influenced by factors such as session numbers, CPU and GPU utilisation, and memory consumption. Determining the appropriate interval or triggering events for distributing this information is critical, as overly frequent updates may cause unnecessary signalling overhead.

OBM requires the ability to dynamically assess compute availability and adjust media object delivery accordingly. Depending on the decision logic associated with OBM service delivery, one or more compute-related metrics must be conveyed within a CATS domain. The frequency of such conveyance must be optimised to ensure that signalling overhead does not introduce additional network congestion. While existing routing protocols can provide a baseline for conveying such metrics, alternative mechanisms may be required to efficiently integrate compute-aware decision-making processes.

Furthermore, an effective OBM system should balance network path selection with the real-time availability of compute resources to ensure optimal QoE. This may involve leveraging distributed compute resources across the network, allowing OBM elements to be processed closer to the user when necessary. Mechanisms for synchronising compute-aware decisions across different network segments will be crucial to ensuring seamless media composition and delivery.

The categories of metrics relevant to OBM in a compute-aware traffic steering context include:

* Compute and GPU Resource Availability:
CPU and GPU utilisation, memory consumption, and storage capacity at different compute nodes.

* Session and User Load:
Number of concurrent media sessions, user distribution, and geographic density of active users.

* Processing Latency
Delays introduced by encoding, decoding, and media object composition at various compute locations.

* Network Throughput and Congestion:
Available bandwidth, packet loss, and jitter affecting media object transmission.

* Edge and Cloud Resource Allocation:
Distribution of OBM processing tasks between central cloud servers and edge computing nodes to balance performance and latency.

## Flex Media Metrics


## Compute Metrics


## Network Metrics

# Scalability Considerations


## Content Delivery Networks (CDNs)


## Server-Side Processing


## Storage Requirements


## Client-Side Capabilities


## Metadata Management


## Quality of Service (QoS) and Quality of Experience (QoE)


# Privacy and Security in Flexible Media

Ensuring privacy and user confidentiality in OBM requires careful management of compute-related and object (asset) information. Exposing details about compute and asset resources to the network may inadvertently reveal sensitive application or domain-level data. To mitigate this risk, strategies for protecting sensitive information should be incorporated into OBM traffic steering mechanisms. An approach might be to anonymise or abstract key identifiers, preventing direct exposure of device identities or application-specific details. This could involve using generic identifiers, such as service-level indicators, instead of detailed resource specifications. Additionally, customisable information exposure policies can be applied, allowing different levels of detail to be shared based on application or network scheduling requirements.

While ensuring anonymity, it is also necessary to maintain the utility of compute-aware traffic steering. The challenge lies in striking a balance between protecting confidentiality and providing sufficient information for effective resource allocation. Techniques such as secure aggregation, differential privacy, and encryption-based mechanisms may help achieve this balance, ensuring that traffic steering decisions are both privacy-preserving and optimised for performance.

## Data Protection Challenges


## Personalisation versus Privacy


##  Applicable Security Techniques

--- back

# IANA Considerations

This document has no IANA actions.

# Acknowledgments
{:numbered="false"}

This work has benefited from discussions within the IETF community.

Additionally the work has been partly funded by the AI4ME project.

