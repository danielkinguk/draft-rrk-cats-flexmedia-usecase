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

Technical Overview of Flexible Media

# Conventions and Definitions

{::boilerplate bcp14-tagged}

The following terms are used in this document:

* AI: 
: Artificial Intelligence aims to create systems capable of performing
tasks that typically require human intelligence, such as understanding
natural language, recognizing patterns, and making decisions.

# Significance of Flexible Media and Internet Usage


# Objectives of the Analysis


# Background and Related Work


## Evolution of Digital Media Streaming over the Internet


## Previous IETF work on Video Media Delivery across Internet Infrastructure


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

