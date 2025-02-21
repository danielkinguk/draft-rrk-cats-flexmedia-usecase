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

* Objects: 
Assets that are used to make a piece of content.

* Scheduler:
Instantiates executors for jobs at a local controller based on the resources available at the compute site where the system resides.

* Service: 
A media stream of user-generated personalised content.

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


## Compute Aware Traffic Steering


## Bandwidth Optimisation Strategies


## Latency Reduction Techniques


## Content Personalisation Algorithms


## Metrics


### Flex Media Metrics


### Compute Metrics


### Network Metrics


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


# Infrastructure Implications

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


## Scalability Considerations


### Content Delivery Networks (CDNs)


### Server-Side Processing


### Storage Requirements


### Client-Side Capabilities


### Metadata Management


### Quality of Service (QoS) and Quality of Experience (QoE)


## Role and Adaptation of Content Delivery Networks (CDNs)


## Edge Computing in Media Delivery


## Additional Desirable Capabilities


# Privacy and Security in Flexible Media


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

