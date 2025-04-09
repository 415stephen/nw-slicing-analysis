# Network Slicing Competitive Analysis: Cisco, Velocloud, and Cradlepoint

## Executive Summary

This report provides a comprehensive technical analysis of network slicing capabilities across three major vendors: Cisco, Velocloud (now part of Broadcom, previously VMware), and Cradlepoint (now part of Ericsson). Network slicing has emerged as a critical technology for next-generation networks, particularly with the rollout of 5G, enabling the creation of multiple virtual networks on a shared physical infrastructure with tailored characteristics for specific applications and services.

Our analysis reveals distinct approaches to network slicing implementation:

- **Cisco** offers a comprehensive end-to-end network slicing solution across multiple domains (RAN, transport, core) with both hard and soft slicing capabilities, providing the most complete but complex implementation.

- **Velocloud** takes a unique application-centric approach with their Dynamic Application-Based Slicing (DABS), focusing on application performance rather than network infrastructure, making it more flexible across different network types.

- **Cradlepoint** emphasizes tight integration with 5G Standalone (SA) networks to provide MPLS-like guarantees over wireless connections, with a focus on simplicity and ease of deployment.

Each vendor has distinct strengths and limitations that make them suitable for different deployment scenarios and organizational requirements. This report details their technical capabilities, integration options, target use cases, and provides recommendations for selecting the most appropriate solution based on specific needs.

## Table of Contents

1. [Introduction to Network Slicing](#introduction-to-network-slicing)
2. [Vendor Overview](#vendor-overview)
3. [Technical Approach Comparison](#technical-approach-comparison)
4. [Implementation and Integration](#implementation-and-integration)
5. [Hardware and Software Requirements](#hardware-and-software-requirements)
6. [Target Use Cases and Vertical Focus](#target-use-cases-and-vertical-focus)
7. [Strengths and Limitations Analysis](#strengths-and-limitations-analysis)
8. [Innovation and Future Direction](#innovation-and-future-direction)
9. [Vendor Selection Recommendations](#vendor-selection-recommendations)
10. [Conclusion](#conclusion)
11. [References](#references)

## Introduction to Network Slicing

### Definition and Importance

Network slicing is a network architecture that enables the creation of multiple virtual networks on top of a shared physical infrastructure. Each network slice is isolated and can be tailored with specific characteristics to meet the requirements of different applications, services, or customers. This technology is particularly important in the context of 5G networks, where diverse use cases with varying requirements need to be supported simultaneously.

### Key Characteristics of Network Slicing

1. **Isolation**: Each slice operates independently with dedicated or shared resources
2. **Customization**: Slices can be tailored for specific performance characteristics (bandwidth, latency, reliability)
3. **End-to-End**: Slicing spans across all network domains (RAN, transport, core)
4. **Dynamic Management**: Slices can be created, modified, and deleted as needed
5. **Resource Efficiency**: Optimizes the use of network resources across multiple services

### Network Slicing Types

1. **Hard Slicing**: Provides dedicated resources (especially bandwidth) not shared with other slices, ensuring strict performance guarantees
2. **Soft Slicing**: More flexible approach where resources can be shared between slices while maintaining SLA requirements
3. **Application-Based Slicing**: Focuses on application performance rather than network infrastructure

### 3GPP-Defined Network Slice Types

The 3rd Generation Partnership Project (3GPP) has defined three primary slice types for 5G networks:

1. **Enhanced Mobile Broadband (eMBB)**: For high-bandwidth applications like video streaming, augmented reality, and virtual reality
2. **Ultra-Reliable Low Latency Communications (URLLC)**: For applications requiring extremely low latency and high reliability, such as autonomous vehicles and remote surgery
3. **Massive Machine Type Communications (mMTC)**: For IoT and similar applications with many devices but lower bandwidth requirements per device

## Vendor Overview

### Cisco

Cisco is a global leader in networking technology, offering a comprehensive portfolio of products and solutions across all network domains. Their approach to network slicing spans multiple product lines and focuses on end-to-end capabilities across RAN, transport, and core networks.

**Key Products for Network Slicing:**
- Cisco IoT Control Center with On-Demand Network Slicing and Assurance
- Ultra Cloud Core 5G Policy Control Function (PCF)
- Transport Layer Network Slicing solutions with Segment Routing and EVPN

### Velocloud (Broadcom/VMware)

Velocloud, originally an SD-WAN pioneer, was acquired by VMware in 2017 and is now part of Broadcom following their acquisition of VMware. Their approach to network slicing is primarily through their SD-WAN platform with a unique application-based slicing methodology.

**Key Products for Network Slicing:**
- VeloRAIN (Robust Artificial Intelligence Networking)
- VeloSky
- VMware SD-WAN by VeloCloud with 5G integration

### Cradlepoint (Ericsson)

Cradlepoint, acquired by Ericsson in 2020, specializes in wireless edge solutions and 4G/5G routers. Their network slicing approach is tightly integrated with 5G Standalone networks and focuses on providing enterprise-grade performance guarantees over wireless WANs.

**Key Products for Network Slicing:**
- Cradlepoint X20 5G Router
- Cradlepoint E3000 Series Enterprise Routers
- NetCloud Exchange Service Gateway

## Technical Approach Comparison

### Fundamental Approach to Network Slicing

| Vendor | Core Approach | Primary Technology Base | Network Slicing Type |
|--------|---------------|-------------------------|----------------------|
| **Cisco** | End-to-end network slicing across multiple domains | Dedicated network infrastructure with virtualization | Both hard slicing (dedicated resources) and soft slicing (shared resources) |
| **Velocloud** | Application-based slicing (DABS) | SD-WAN with AI enhancement | Software-defined application-layer slicing that works across various network types |
| **Cradlepoint** | 5G Standalone-based network slicing | 5G SA with SD-WAN integration | Traditional 3GPP-defined network slicing requiring 5G SA infrastructure |

### Key Differentiators in Approach

- **Cisco** focuses on comprehensive end-to-end slicing across all network domains (RAN, transport, core) with both infrastructure-level and application-level capabilities. Their approach is the most complete but also the most complex, requiring integration across multiple Cisco products and platforms.

- **Velocloud** takes a unique application-centric approach with Dynamic Application-Based Slicing (DABS), which operates at the application layer rather than the infrastructure layer. This allows their solution to work across various network types without requiring specific network infrastructure support, making it more flexible but potentially less tightly integrated with the underlying network.

- **Cradlepoint** emphasizes tight integration with 5G Standalone networks, focusing on providing MPLS-like guarantees over wireless connections. Their approach is more dependent on specific network infrastructure (5G SA) but offers a more straightforward implementation for organizations looking to leverage 5G network slicing.

### Technical Implementation Details

#### Cisco Implementation

Cisco's network slicing implementation addresses several key requirements:

1. **Transport Slice Management**: Ability to create, modify, and delete 3GPP network slices, including actions required on the transport layer. Slice owners and operators can monitor health and performance through pre-slice operations, administration, and maintenance (OAM) capabilities.

2. **Slice Isolation**: Each transport slice is isolated from other slices to meet stringent SLAs, ensuring proper performance, security, operation, and reliability levels.

3. **Resource Reservation**: Capability to reserve transport resources for specific slices.

4. **Abstraction**: Ability to utilize resources required to model and build transport infrastructure to meet slice needs.

5. **Hard and Soft Slicing Support**: 
   - **Hard Slicing**: Provides dedicated resources (especially bandwidth) not shared with other slices
   - **Soft Slicing**: More agile and flexible approach where resources can be shared between slices while maintaining SLA requirements

Cisco's Ultra Cloud Core 5G PCF implements network slicing capabilities through:

- **Network Virtualization**: Registers Single-Network Slice Selection Assistance Information (S-NSSAIs) with the Network Repository Function (NRF)
- **Slice Identification**: Uses S-NSSAI to identify network slices, enabling PCF to identify specific slices
- **Service-Based Discovery**: After registration, Session Management Function (SMF) and Access and Mobility Management Function (AMF) can discover the PCF instances serving specific slices

#### Velocloud Implementation

Velocloud's Dynamic Application-Based Slicing (DABS) differs from traditional network slicing:

1. **Focuses on Applications**: Prioritizes at the application layer rather than the network layer.

2. **Works Across Multiple Networks**: Functions across disparate underlying networks, whether they support network layer slicing or not.

3. **Adapts Dynamically**: Uses AI to adjust policies based on real-time conditions and application needs.

4. **Handles Encrypted Traffic**: Can identify and prioritize encrypted application traffic that was previously unreadable for network optimization solutions.

Velocloud enhances its Dynamic Multipath Optimization (DMPO) technology with AI capabilities:

1. **Channel Estimation**: Applies machine learning to perform channel estimation for various network types, including satellite, 4G, and 5G.

2. **Adaptive Management**: Dynamically manages bandwidth, latency, and jitter based on predicted channel conditions.

3. **Natural Language Interaction**: Allows users to ask natural-language questions about network performance and receive immediate responses.

#### Cradlepoint Implementation

Cradlepoint's network slicing capabilities are built on 5G Standalone architecture:

1. **5G SA Requirement**: Full network slicing capabilities require 5G Standalone networks with a dedicated 5G core
2. **End-to-End Performance**: Provides end-to-end performance guarantees over 5G Wireless WANs, similar to SLAs available with MPLS
3. **Chipset Dependencies**: Requires the latest chipsets that support 5G SA and network slicing capabilities

Cradlepoint's approach to network slicing includes sophisticated traffic steering capabilities:

1. **Application Recognition**: Identifies applications and their requirements
2. **Policy-Based Routing**: Directs traffic to appropriate network slices based on policies
3. **SD-WAN Integration**: Leverages SD-WAN technology to steer traffic to network slices
4. **Quality of Service (QoS)**: Ensures business-critical applications maintain performance even during congestion

## Implementation and Integration

### Network Infrastructure Requirements

| Vendor | Infrastructure Requirements | Dependency on 5G | Multi-Domain Support |
|--------|----------------------------|-----------------|---------------------|
| **Cisco** | Requires Cisco network infrastructure components for full functionality | Supports 5G but not exclusively dependent | Strong multi-domain support across RAN, transport, and core |
| **Velocloud** | Works with existing network infrastructure | Can work with or without 5G | Primarily focused on WAN domain with some edge integration |
| **Cradlepoint** | Requires 5G Standalone networks for full functionality | Heavily dependent on 5G SA | Primarily focused on wireless WAN domain |

### Slice Creation and Management

| Vendor | Slice Creation Method | Management Interface | Automation Level |
|--------|----------------------|---------------------|-----------------|
| **Cisco** | Network-level virtualization with S-NSSAI registration | IoT Control Center and dedicated management platforms | High automation with AI-insights and self-healing capabilities |
| **Velocloud** | Application-based virtual slicing through SD-WAN | VeloCloud SD-WAN management interface | High automation with AI-driven optimization and dynamic adaptation |
| **Cradlepoint** | 3GPP-standard network slicing with SD-WAN integration | NetCloud Exchange Service Gateway | Medium-high automation with policy-based routing and application recognition |

### Traffic Steering and QoS

| Vendor | Traffic Steering Approach | QoS Implementation | Application Recognition |
|--------|--------------------------|-------------------|------------------------|
| **Cisco** | Granular traffic classification with self-serve capabilities | End-to-end QoS across network domains | Advanced application recognition with AI-insights |
| **Velocloud** | AI-driven Dynamic Application-Based Slicing (DABS) | Application-specific QoE guarantees | AI-powered application profiling including encrypted traffic |
| **Cradlepoint** | SD-WAN-based traffic steering to network slices | Slice-Aware QoS to protect critical flows | Application recognition with policy-based routing |

### Integration with Other Technologies

#### 5G Integration

| Vendor | 5G Integration Level | Support for 5G SA | Support for 5G NSA |
|--------|---------------------|------------------|-------------------|
| **Cisco** | Deep integration across product lines | Full support | Full support |
| **Velocloud** | Integration through partnerships (e.g., AT&T) | Partial support with evolving capabilities | Good support |
| **Cradlepoint** | Core dependency on 5G SA for full functionality | Full support (required for full capabilities) | Limited network slicing support |

#### SD-WAN Integration

| Vendor | SD-WAN Integration | Traffic Management Capabilities | Multi-Cloud Support |
|--------|-------------------|-------------------------------|-------------------|
| **Cisco** | Native integration with Cisco SD-WAN | Advanced traffic management with segment routing | Strong multi-cloud support |
| **Velocloud** | Core part of solution (SD-WAN is the foundation) | AI-enhanced Dynamic Multipath Optimization (DMPO) | Strong multi-cloud optimization |
| **Cradlepoint** | Integration with NetCloud SD-WAN capabilities | SD-WAN-based traffic steering to network slices | Good cloud support |

#### Edge Computing Integration

| Vendor | Edge Computing Support | Local Processing Capabilities | Edge Security |
|--------|----------------------|----------------------------|--------------|
| **Cisco** | Strong support for edge computing | Advanced edge processing capabilities | Comprehensive edge security |
| **Velocloud** | Good support with focus on AI workloads | Optimized for distributed AI applications | Integrated security features |
| **Cradlepoint** | Emerging support with focus on FWA | Basic edge processing capabilities | Integrated security features |

## Hardware and Software Requirements

| Vendor | Required Hardware | Software Platform | Deployment Flexibility |
|--------|------------------|------------------|----------------------|
| **Cisco** | Cisco networking hardware (various product lines) | Cisco IOS XR, IoT Control Center, Ultra Cloud Core | Multiple deployment options across various domains |
| **Velocloud** | Velocloud SD-WAN appliances (physical or virtual) | VeloCloud SD-WAN platform | Flexible deployment with physical or virtual appliances |
| **Cradlepoint** | Cradlepoint routers with 5G SA support (X20, E3000 series) | NetCloud platform | Focus on physical router appliances |

### Cisco Hardware/Software Requirements

Cisco's network slicing implementation requires various hardware and software components depending on the network domain:

- **RAN Domain**: Cisco Ultra Cloud Core components
- **Transport Domain**: Cisco IOS XR-based routers with segment routing capabilities
- **Core Domain**: Cisco Ultra Cloud Core 5G PCF and related components
- **Management**: Cisco IoT Control Center and other management platforms

### Velocloud Hardware/Software Requirements

Velocloud's network slicing implementation is primarily software-based but requires:

- **SD-WAN Edge Devices**: Physical or virtual Velocloud SD-WAN appliances
- **SD-WAN Orchestrator**: VeloCloud Orchestrator for centralized management
- **SD-WAN Gateway**: VeloCloud Gateway for cloud-hosted services

### Cradlepoint Hardware/Software Requirements

Cradlepoint's network slicing implementation requires:

- **5G Routers**: Cradlepoint X20 5G Router or E3000 Series Enterprise Routers with 5G SA support
- **NetCloud Platform**: NetCloud Exchange Service Gateway for management and orchestration
- **5G SA Network**: Access to a 5G Standalone network with network slicing capabilities

## Target Use Cases and Vertical Focus

| Vendor | Primary Use Cases | Vertical Industries | Deployment Scenarios |
|--------|------------------|-------------------|---------------------|
| **Cisco** | Connected vehicles, enterprise connectivity, developer ecosystem | Automotive, telecommunications, enterprise | Fixed, mobile, and hybrid deployments |
| **Velocloud** | AI workload optimization, manufacturing, retail, connected vehicles | Manufacturing, retail, automotive, enterprise | Primarily fixed with some mobile support |
| **Cradlepoint** | SMB connectivity, temporary sites, remote work, public safety | SMB, healthcare, public safety, industrial | Fixed, mobile, and temporary deployments |

### Cisco Target Use Cases

Cisco's network slicing solutions target several key use cases:

1. **Connected Vehicles**: Enabling OEMs to offer immersive in-car experiences and subscription services
2. **Enterprise Connectivity**: Providing secure and reliable connectivity for enterprise applications
3. **Private-Macro Interoperability**: Supporting enterprises that require physical and logical isolation without needing a fully private network
4. **Developer Ecosystem Empowerment**: Enabling API-based network programmability for application developers

### Velocloud Target Use Cases

Velocloud's network slicing solutions target several key use cases:

1. **AI Workload Optimization**: Supporting the unique requirements of AI applications, which can be bursty, highly sensitive to latency, and often operate on a peer-to-peer basis
2. **Manufacturing**: Dividing traffic so that manufacturing floor traffic goes over fixed wireless using a deployed 5G network, while keeping general office traffic on landline broadband
3. **Retail**: Supporting vision applications analyzing in-store behavior with real-time policy adjustments
4. **Connected Vehicles**: Enabling applications that require high upstream bandwidth and low latency
5. **Multi-Cloud Access**: Simplifying hybrid and multi-cloud access by determining optimal paths for workloads in various cloud destinations

### Cradlepoint Target Use Cases

Cradlepoint's network slicing solutions target several key use cases:

1. **Small-to-Medium Sized Businesses**: Providing reliable, high-speed connectivity without traditional wired infrastructure
2. **Temporary Sites**: Supporting pop-up stores, mobile clinics, and construction sites with rapid deployment and flexibility
3. **Remote Workers and Home-Based Businesses**: Offering easy setup and portable, high-speed internet for remote work
4. **Public Safety**: Dedicated network slices for first responders and emergency services
5. **Industrial Automation**: Ultra-reliable, low-latency connectivity for manufacturing and industrial applications
6. **Healthcare**: Secure and reliable connectivity for telemedicine and remote patient monitoring

## Strengths and Limitations Analysis

### Cisco

**Strengths:**
- Comprehensive end-to-end network slicing across all domains
- Strong multi-vendor support and open network architecture
- Advanced automation and orchestration capabilities
- Broad product portfolio covering all aspects of network slicing
- Granular traffic classification with self-serve capabilities
- Strong integration with edge computing and multi-cloud environments

**Limitations:**
- PCF supports only soft slicing without isolating system resources
- Full implementation requires integration across multiple Cisco products
- Higher complexity due to comprehensive approach
- Some aspects of network slicing require 5G standalone (SA) architecture for full benefits
- Potentially higher cost due to comprehensive solution

### Velocloud

**Strengths:**
- Unique application-based slicing approach that works across network types
- AI-driven optimization and application profiling
- Can work with or without 5G network infrastructure
- Strong focus on application performance and user experience
- Ability to identify and prioritize encrypted application traffic
- Flexible deployment with physical or virtual appliances

**Limitations:**
- Not traditional infrastructure-level network slicing
- Requires Velocloud's SD-WAN implementation to function
- Full integration with 5G network slicing still evolving
- May require specific hardware appliances for optimal performance
- Less control over the underlying network infrastructure

### Cradlepoint

**Strengths:**
- Strong integration with 5G SA networks
- MPLS-like guarantees over wireless connections
- Tight integration with Ericsson's 5G infrastructure
- Focus on simplicity and ease of deployment
- Dual-SIM failover capabilities for enhanced reliability
- Battery backup options for continuous operation

**Limitations:**
- Heavy dependency on 5G SA networks for full functionality
- Network slicing effectiveness depends on carrier implementation
- Requires specific hardware with latest chipsets
- Limited availability as 5G SA networks are still being rolled out
- Primarily focused on the wireless WAN domain

## Innovation and Future Direction

| Vendor | Key Innovations | Future Focus | Development Pace |
|--------|----------------|--------------|-----------------|
| **Cisco** | Cross-domain orchestration, granular traffic classification | Enhanced automation, expanded use cases | Steady innovation across product lines |
| **Velocloud** | Dynamic Application-Based Slicing, AI-enhanced DMPO | Enhanced AI integration, hybrid slicing approaches | Rapid innovation in AI-driven networking |
| **Cradlepoint** | 5G SA integration, MPLS-like guarantees over wireless | Expanded hardware support, multi-carrier support | Accelerating with Ericsson partnership |

### Cisco Innovation Direction

Cisco is continuing to develop its network slicing capabilities with a focus on:

1. **Enhanced Automation**: Further automating slice creation and management across all network domains
2. **Expanded Use Cases**: Developing solutions for new industry verticals and applications
3. **Improved Analytics**: Enhancing real-time analytics and visibility into slice performance
4. **Multi-Vendor Support**: Strengthening support for multi-vendor environments
5. **API Ecosystem**: Expanding API-based network programmability for developers

### Velocloud Innovation Direction

Velocloud is continuing to develop its network slicing capabilities with a focus on:

1. **Enhanced AI Integration**: Further leveraging AI for network optimization and application prioritization
2. **Expanded 5G Support**: Deeper integration with 5G networks as they become more widely available
3. **Hybrid Slicing Approaches**: Developing solutions that can dynamically choose between application-based and network-based slicing
4. **Edge Computing Support**: Optimizing network slices for edge computing applications
5. **Natural Language Interfaces**: Expanding natural language interaction capabilities for network management

### Cradlepoint Innovation Direction

Cradlepoint is continuing to develop its network slicing capabilities with a focus on:

1. **Expanded Hardware Support**: Developing more routers and endpoints with network slicing capabilities
2. **Enhanced Integration**: Deeper integration between NetCloud Exchange and network slicing functionality
3. **Automated Slice Selection**: More intelligent and automated selection of network slices based on application needs
4. **Multi-Carrier Support**: Expanding support for network slicing across multiple carriers
5. **Edge Computing Integration**: Combining network slicing with edge computing capabilities for improved performance

## Vendor Selection Recommendations

### Best Fit Scenarios

**Cisco** is best suited for:
- Organizations requiring comprehensive end-to-end network slicing
- Environments with existing Cisco infrastructure
- Complex multi-domain deployments
- Service providers looking to offer network slicing as a service
- Organizations with advanced technical expertise and resources

**Velocloud** is best suited for:
- Organizations focused on application performance rather than network infrastructure
- Environments with diverse network types that need unified management
- AI-intensive workloads with dynamic requirements
- Businesses that want network slicing benefits without 5G SA dependency
- Organizations with existing SD-WAN deployments looking to enhance capabilities

**Cradlepoint** is best suited for:
- Organizations requiring MPLS-like guarantees over wireless connections
- Environments with 5G SA availability
- Small to medium businesses, temporary sites, and remote workers
- Deployments that prioritize simplicity and ease of management
- Organizations looking for integrated solutions with Ericsson's 5G infrastructure

### Selection Criteria Framework

When selecting a network slicing solution, organizations should consider:

1. **Existing Infrastructure**: Compatibility with current network infrastructure and investments
2. **5G Availability**: Current and planned 5G coverage in deployment areas
3. **Technical Expertise**: Internal capabilities to implement and manage the solution
4. **Use Case Requirements**: Specific performance, security, and reliability needs
5. **Budget Constraints**: Total cost of ownership including hardware, software, and operational costs
6. **Future Scalability**: Ability to grow and adapt as requirements evolve
7. **Vendor Ecosystem**: Alignment with other strategic technology partners

### Decision Matrix

| Selection Factor | Cisco | Velocloud | Cradlepoint |
|-----------------|-------|-----------|-------------|
| Comprehensive end-to-end slicing | High | Medium | Medium |
| 5G SA dependency | Medium | Low | High |
| Implementation complexity | High | Medium | Medium-Low |
| Application-layer focus | Medium | High | Medium |
| Infrastructure-layer focus | High | Medium | High |
| Multi-domain support | High | Medium | Medium-Low |
| Edge computing integration | High | Medium-High | Medium |
| Deployment flexibility | High | High | Medium |
| AI/ML capabilities | Medium-High | High | Medium |
| Total cost of ownership | High | Medium | Medium-Low |

## Conclusion

Network slicing represents a transformative technology for next-generation networks, enabling the creation of tailored virtual networks on shared physical infrastructure. Our analysis of Cisco, Velocloud, and Cradlepoint reveals three distinct approaches to network slicing implementation, each with unique strengths and limitations.

Cisco offers the most comprehensive end-to-end solution across all network domains but with higher complexity. Velocloud provides a unique application-centric approach that works across various network types without requiring specific infrastructure support. Cradlepoint focuses on tight integration with 5G Standalone networks to deliver MPLS-like guarantees over wireless connections with an emphasis on simplicity.

The choice between these vendors should be based on specific organizational requirements, existing infrastructure, technical expertise, and use case needs. Organizations should carefully evaluate their current and future needs against the capabilities, limitations, and roadmaps of each vendor to select the most appropriate solution.

As 5G networks continue to mature and network slicing technology evolves, we expect to see further innovation and convergence in approaches, with all three vendors expanding their capabilities and addressing current limitations. Organizations should maintain flexibility in their network slicing strategy to adapt to these evolving technologies and maximize the benefits for their specific use cases.

## References

### Network Slicing Fundamentals

1. VIAVI Solutions. (2024). "5G Network Slicing." Retrieved from https://www.viavisolutions.com/en-us/5g-network-slicing

2. Wikipedia. (2023). "5G Network Slicing." Retrieved from https://en.wikipedia.org/wiki/5G_network_slicing

3. IBM. (2023). "What is 5G Network Slicing?" Retrieved from https://www.ibm.com/think/topics/5g-network-slicing

### Cisco Network Slicing

1. Cisco. (2024). "On-Demand Network Slicing and Assurance." Retrieved from https://www.cisco.com/c/en/us/solutions/collateral/internet-of-things/iot-control-center/on-demand-network-slicing-assurance-so.html

2. Cisco. (2024). "Network Slicing." Retrieved from https://www.cisco.com/c/en/us/td/docs/wireless/ucc/pcf/2022-04-0/Configuration-admin/b_ucc-5g-pcf-config-and-admin-guide_2022-04/m_network_slicing_f109147.html

3. Cisco. (2021). "5G Network Slicing White Paper." Retrieved from https://www.cisco.com/c/dam/en/us/products/collateral/cloud-systems-management/network-services-orchestrator/white-paper-sp-5g-network-slicing.pdf

4. Cisco Blogs. (2023). "5G Automation." Retrieved from https://blogs.cisco.com/sp/5g_automation

### Velocloud (VMware) Network Slicing

1. VMware Blogs. (2024). "VeloRAIN AI Networking is the Next SD-WAN Revolution." Retrieved from https://blogs.vmware.com/sase/2024/11/20/velorain-ai-networking-is-the-next-sd-wan-revolution/

2. Techzine. (2024). "Broadcom VeloSky brings application-based slicing to FWA, fibre and satellite links." Retrieved from https://www.techzine.eu/blogs/infrastructure/129263/broadcom-velosky-brings-application-based-slicing-to-fwa-fibre-and-satellite-links/

3. TechTarget. (2023). "VMware VeloCloud sees the future of SD-WAN with 5G, hybrid cloud." Retrieved from https://www.techtarget.com/searchnetworking/feature/VMware-VeloCloud-sees-the-future-of-SD-WAN-with-5G-hybrid-cloud

4. PR Newswire. (2019). "AT&T Bridging 5G and SD-WAN with VMware SD-WAN by VeloCloud for a New Layer of Control at the Edge." Retrieved from https://www.prnewswire.com/news-releases/att-bridging-5g-and-sd-wan-with-vmware-sd-wan-by-velocloud-for-a-new-layer-of-control-at-the-edge-300800353.html

### Cradlepoint Network Slicing

1. Cradlepoint. (2024). "Connectivity meets customization with 5G network slicing." Retrieved from https://cradlepoint.com/resources/blog/connectivity-meets-customization-with-5g-network-slicing/

2. Cradlepoint. (2023). "What is 5G Standalone? 5G SA Means Network Slicing, Security, and Automation." Retrieved from https://cradlepoint.com/resources/blog/what-is-5g-standalone-5g-sa-means-network-slicing-security-and-automation/

3. Cradlepoint. (2022). "Traffic Optimization Through 5G Network Slicing Explained." Retrieved from https://cradlepoint.com/resources/blog/traffic-optimization-through-5g-network-slicing-explained/

4. Ericsson. (2025). "Ericsson launches the Cradlepoint X20 5G Router." Retrieved from https://www.ericsson.com/en/news/2025/2/ericsson-cradlepoint-x20-announcement

5. Cradlepoint. (2021). "Cradlepoint and Ericsson Network Slicing Proof-of-Concept Highlights How Acquisition Will Unlock 5G Capabilities for Enterprises." Retrieved from https://cradlepoint.com/press-release/cradlepoint-and-ericsson-network-slicing-proof-of-concept-highlights-how-acquisition-will-unlock-5g-capabilities-for-enterprises/

6. Intelligent CIO. (2023). "Cradlepoint successfully demonstrates 5G Standalone network slicing." Retrieved from https://www.intelligentcio.com/north-america/2023/02/23/cradlepoint-successfully-demonstrates-5g-standalone-network-slicing/

7. Cradlepoint. (2025). "Ericsson Cradlepoint X20 5G Router enables differentiated Service Provider FWA with network slicing capabilities." Retrieved from https://cradlepoint.com/press-release/ericsson-cradlepoint-x20-5g-router-enables-differentiated-service-provider-fwa-with-network-slicing-capabilities/
