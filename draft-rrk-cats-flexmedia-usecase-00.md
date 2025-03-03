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
  email: rajiv.ramdhany@bbc.co.uk
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

Contemporary approaches to media delivery are challenging for FM content distribution. The flexibility in personalised media introduces a challenge of re-versioning, where the combinatorial explosion of potential content versions makes it impractical to pre-render and store all permutations. On-demand re-versioning can occur on the device if local processing capabilities and network bandwidth allow the objects to be transported to the device and composited. However, it is likely that media object composition may need to be offloaded upstream in the distribution pipeline for universal delivery.

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

Personalisation of media can occur in multiple stages if regional and personal preferences are considered. Delivery infrastructures for personalised media need therefore offer flexibility in creating dynamic media composition stages at at various locations in the network to efficiently support the various personalisation permutations. Further, the selection of media composition sites depends on the availability of compute resources, proximity to storage for media objects and if user agency is afforded, round-trip times to the destination Client.     

# Deploying Flexible Media Services

It is important to optimise network traffic in OBM environments where computing resources are distributed across multiple locationss. This involves making the network aware of the computational context: where computing resources are located, their capabilities, and their current load or availability. By understanding these factors, the network can make more informed decisions about where to route data and processing tasks, aiming to improve efficiency, reduce latency, and enhance the overall performance of networked applications and services. Unlike traditional media formats, OBM treats media elements as independent objects that can be orchestrated at runtime. This document outlines the use cases and requirements for OBM, emphasising the possible role of the IETF Compute-Aware Traffic Steering (CATS) initiative in optimising the delivery of OBM content. Key components of OBM include:

* Media Objects:
Discrete elements such as video segments, audio layers, and metadata.

* Orchestration Engine:
Determines how objects are assembled based on contextual factors.

* Delivery Mechanisms:
Network protocols and architectures enabling object transport and synchronisation.

The dynamic nature of OBM necessitates advanced traffic steering mechanisms that can adapt to compute and network constraints in real-time.

## Compute Aware Traffic Steering

Deployment of OBM services introduces several technical challenges, particularly in the context of Compute Aware Traffic Steering (CATS). Real-time adaptation of compute resource usage is a major challenge, as media objects must be dynamically composed and delivered based on changing network and compute conditions. Synchronisation across distributed compute nodes is also essential, ensuring coordinated media object delivery and processing across edge, cloud, and on-premise compute resources. As the process is managed an additional challenge of Quality of Experience (QoE) management, where compute resource usage must be balanced with perceived quality improvements to enhance the user experience, is also required.  

To support OBM delivery, compute-aware traffic steering must fulfil several requirements. It must possess dynamic compute resource awareness, allowing assessment and adaptation to available compute power along the delivery path. Multi-layer orchestration is necessary to coordinate network-layer traffic steering with application-layer OBM composition. Low-latency compute routing is crucial for minimising processing delays in interactive media experiences. Additionally, scalability and load balancing are needed to ensure efficient distribution of media object processing, preventing compute bottlenecks. Lastly, edge-aware optimisation should be integrated to leverage edge computing for latency-sensitive OBM applications.

## Bandwidth Optimisation Strategies

To be discussed in future versions of this document. 

## Latency Reduction Techniques

To be discussed in future versions of this document. 

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

# Architecture for Flex Media

   {{fig1}} Flex Media Architecture

~~~~
                  ((Users))
                      |
   +------------------+------------------+
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
     |  Compute & Object Allocator |
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
~~~~
{: #fig1 title="Figure 1: Flex Media Architecture" artwork-align="center"}

The above figure provides a conceptulized architecture for Object-Based Media (OBM) processing and delivery, where media objects are dynamically assembled and personalized for individual users. Unlike traditional media streaming, which delivers a pre-encoded linear stream, OBM decomposes content into discrete media objects such as video segments, audio tracks, subtitles, and metadata. These objects are retrieved, processed, and compiled dynamically based on user preferences, user device capabilities (or distributed and dedicated compute nodes), and network conditions.

   {{fig2}} Flex Media Functional Components
~~~~
                                     +-------------------------------+
                                     |   BBC Flex Media Orchestrator |
                                     |  +-------------------------+  |
                                     |  | Policy Decision         |  |
       +-----------------------------+  | Site Manager            |  |
       |                             |  | Site Observer (Cloud)   |  |
       |                             |  +-------------------------+  |
       |                             +-------------------------------+
       |                                                       |
       |                                                       |
+------+---------+       +-----+       +----------------+      |
|     Users      |------>| CDN |<----->|    Storage     |      |
+------+---------+       +-----+       +----------------+      |
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
{: #fig2 title="Figure 2: AI4ME Resources" artwork-align="center"}

In the figure above users are shown as interacting with a system that manages personalized media queues. Each user is associated with a dedicated queue that maintains a sequence of media objects tailored to their specific requirements. This approach allows for fine-grained control over content delivery, ensuring that media elements are customized in real-time. The Object Media Queue Manager is responsible for handling these personalized queues and forwarding processing requests to the appropriate compute resources. These components coordinate the retrieval and processing of media objects by distributing tasks across available resources. The Job Scheduler determines the order and priority of processing tasks, while the Resource Allocator assigns computational and storage resources to execute them. This scheduling mechanism is critical for balancing resource utilization, optimizing media rendering, and ensuring low-latency delivery.

The Compute and Object Resource layer, which includes distributed compute nodes and storage elements responsible for processing media objects. The connections between the Job Scheduler, Resource Allocator, and compute nodes allow workloads to mapped to specific resources. The dynamic scheduling approach where different media objects are processed in parallel across multiple compute units, enhances scalability and efficiency, enabling personalized media delivery at scale. By integrating compute-aware resource scheduling with object-based media workflows, this architecture supports adaptive content distribution while optimizing network and compute resources.


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

Furthermore, an effective OBM system should balance network path selection with the real-time availability of compute resources to ensure optimal QoE. This may involve leveraging distributed compute resources across the network, matching computing workloads to resource-availability and allowing OBM elements to be processed closer to the user when necessary. Mechanisms for synchronising compute-aware decisions across different network segments will be crucial to ensuring seamless media composition and delivery.

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

In addition to metrics for assessing compute suitability and availability, metrics are also required to select a particular compute site. This decision requires an undertanding of both the cost of offloading and its impact on Quality of Experience (QoE). For most flex media experiences, there are also baseline QoE constraints that need to be factored in this decision. 
These metrics can be grouped in three main classes: 

1. Delivery Performance
This includes metrics associated with video delivery and media experience responsiveness , if the user is afforded agency via interaction:

* Frame Rate: target frame rate for the experience (30 fps for video animations, sampling rate for audio);  also specifies the rate of work done required to produce the frames i.e. at frame rate 60 fps, twice the amount of computation is required compared to a 30 fps offloaded experience. 
  
* Frame Size: size of video frames (pixels) or audio samples (bit depth); usual Flex Media video resolutions are 720p, 1080p (HD) and 2160p (4K).

* Bit Rate: amount of media data processed per second. Usually calculated as Frame Rate x Resolution (bps)

* Delay: The end-to-end delay for streaming offloaded flex media consists of the following: 

  * Render Delay: time to render each frame; this is dependent on the frame size, the number of objects to render and metrics indicating compute type (CPU, SIMD, GPU) and capabilities (frequency, boosted frequency, number of cores, number of render units, memory bandwidth, memory size, memory utilization, core utilization).
  
  * Encode Delay: time taken to encode and package frames for streaming. This depends on encoder type (hardware or software), encoding type (some are more optimised for low-latency) and media segment length.
  
  * Transport Delay: the network propagation delay for a media frame; depends on Frame Size and network bandwith
  

2. Client QoE

These metrics concern the consumption of flex media and the perception of degradations by the user. Some metrics like delay/asynchrony tolerance are set by editorial guidelines. For example, there are different acceptable delays for interactive TV applications like switching media objects than for game-like or XR applications.  

* Delay tolerance: The threshold for the particular experience beyond which the delay becomes perceptible/irritating to the user; usually editorially set as it may be experience-specific.

* Object Asynchrony: the asynchrony between the various objects being assembled; offloading one or more objects processing may result in the objects arriving out of sync at the point of assembly due to network delay variation.
    
* Asynchrony Tolerance: the threshold beyond which the time shift between the objects becomes perceptible to the user. Lip-sync (between audio and video objects) has a lower asynchrony tolerance than Picture-in-Picture.

* Object Quality: the average Frame Rate and the Frame Size of the media object; objects can be streamed at different qualities to meet bandwidth constraints based on user perception.
   
* Quality Switches (Magnitude, Frequency): if the media object is delivered via adaptive streaming, then this metric measures the frequency and magnitude of switches between available object qualities (e.g. resolution/bit rates).
  
* Number of Rebuffering Events: number of audio/video stalls over a time period due to network congestion or server performance delaying arrival of frames for decoding and playback.
  
* Playback Rate: the rates at which different objects are played at the point of assembly and presentation. These can vary if local playback adaptation algorithms are used to overcome object asynchrony. 


3. Cost
These metrics refer to the cost of running offloaded media processing jobs at a selected compute site and streaming the results back to the client.

* Render Cost: this is determined from resources used (CPU/+GPU), the time taken to render, and time to encode a given task for transport.

* Cache Recency: this specifies the (caching policy) i.e. the priority to be set for keeping a generated object frame in a cache . Utilisation of a cache reduces compute resource utilisation. An object with higher Cache Recency indicates a higher probability that this object will be required by another client in the lifetime of the experience.


## Compute Metrics

These metrics are used to assess the suitability of compute resources and their availability for offloading of flex media compute tasks. They denote different types of compute hardware as well as their level of utilisation. GPUs will run tasks such as rendering complex images, where NPUs are preferred for repetitive and less complex AI tasks, such as background blurring or object detection.


* Compute Type:  Type of processor (CPU, GPU, Frequency, FLOPS, integer, FP8, 4 octets)

*  CPU: Frequency, number of cores, core utilization, memory bandwidth, memory size, 
   memory utilization, power consumption. 

*  GPU: Frequency, number of render units, memory bandwidth, memory
  size, memory utilization, core utilization, power consumption. For

*  NPU: TOPS , utilization, power consumption 
  
*  System Load Average: A measure of the average workload of a system over a time period, providing a snapshot of overall system performance.

*  Storage: Available space, read speed, write speed.

## Network Metrics

These metrics enable the assessment the suitability ot network links based on their characteristics as they can adversely affect QoE.

*	Latency: The time it takes for data to travel from source to destination is critical for the time-sensitive delivery of flex media. 
*	Bandwidth: The maximum rate of data transfer across a network path, indicating the capacity of the network link.
*	Packet Loss: The percentage of packets that fail to reach their destination, affecting the network connection quality.
*	Jitter: The variability in packet delay can impact the performance of real-time applications like VoIP or video streaming.
*	Throughput: The actual data transfer rate achieved can be lower than the available bandwidth due to various factors like congestion.
*	Error Rates: The rate of erroneous packets, indicating the quality of the network link.



# Scalability Considerations

Scalability concerns for OBM distribution at scale are significant due to the inherently complex and dynamic nature of delivering personalised, interactive content to a wide audience. These concerns primarily revolve around the following aspects:

* Network Bandwidth: Object-based media, by its nature, can require more data transmission than traditional linear media because it involves sending multiple media objects (and potentially multiple versions of each object) to allow for user customisation and interactivity. This can lead to increased bandwidth demands, particularly during peak usage times, posing challenges for content delivery networks (CDNs) and end-user internet connections.

* Compute Resource Usuage:
TBD

Addressing these scalability concerns requires innovative solutions in content distribution architectures, such as more intelligent edge computing frameworks, advanced caching strategies, more efficient encoding techniques, and the development of new standards and protocols designed to support the dynamic nature of object-based media. Additionally, leveraging advancements in network infrastructure, such as 5G and beyond, can provide the high bandwidth and low latency needed to deliver personalised, interactive media experiences to large audiences.

## Server-Side Processing

The dynamic assembly of media objects based on user preferences, context, or device capabilities can impose significant processing loads on servers, especially for live or real-time content. Scalability challenges arise in efficiently managing these computational demands, particularly when serving a large and concurrent user base.

## Client-Side Processing

The variability in client devices (ranging from smart TVs and set-top boxes to smartphones and tablets) poses challenges in ensuring a consistent and seamless user experience. Scalability issues may arise from the need to adapt real-time content to each device's capabilities, considering factors such as processing power, screen size, and available bandwidth.

## Storage Requirements

## Metadata Management


## Quality of Service (QoS) and Quality of Experience (QoE)

Maintaining high QoS and QoE levels as the user base scales is critical. This includes challenges related to minimising buffering, ensuring synchronisation between media objects (e.g., audio tracks with video), and adapting to varying network conditions in real time.

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

