# SRDA: A System-level Simplified Reconfigurable Dataflow Architecture for Large AI Models Training and Inferencing

<p align="center">
  <img src="https://img.shields.io/badge/Architecture-SRDA-blue" alt="Architecture">
  <img src="https://img.shields.io/badge/Status-In--Development-green" alt="Status">
  <img src="https://img.shields.io/badge/Ecosystem-RISC--V-orange" alt="Ecosystem">
</p>

## Overview

This document introduces **SRDA (System-level Simplified Reconfigurable Dataflow Architecture)**, an innovative computing architecture designed from an I/O-centric perspective specifically for AI. As AI hardware struggles to keep pace with software advancements, SRDA™ aims to systematically address fundamental I/O bottlenecks like the "Memory Wall" and "Power Wall," unlocking the true computational potential of large AI models.

Through its dataflow-driven design, deep hardware-software co-design, and key innovations in distributed memory, converged networking, and reconfigurable computing, SRDA™ is engineered to deliver a minimalist yet highly efficient AI compute platform.

## The Challenge: Current Bottlenecks in AI Computing

Traditional computing architectures have revealed multiple inherent limitations when faced with AI models scaling to trillions of parameters:

* **Von Neumann Bottleneck**: The separation of compute and storage units necessitates frequent data movement, severely limiting performance and energy efficiency.
* **Memory Bandwidth Limitation**: Shared memory systems like HBM in mainstream GPUs are prone to access congestion from read/write conflicts, creating a critical bottleneck.
* **Low Compute Utilization**: Communication overhead and memory access issues prevent the theoretical peak compute of chips from being fully realized in real-world AI workloads.
* **Ever-Increasing Power Consumption**: Top-tier AI accelerators consume enormous amounts of power (e.g., the H100 GPU at 700W), making electricity a core operational cost for data centers.
* **Large-Scale Cluster Expansion Challenges**: Traditional two-tiered networks (e.g., NVLink + InfiniBand) introduce bandwidth disparities, protocol overhead, and management complexity, making large-scale clusters costly and inefficient.
* **Software Complexity**: Existing software stacks for AI acceleration are highly complex, leading to high optimization costs and limiting their use for large models.

## SRDA: A New Paradigm in AI Computing

SRDA is a dataflow-centric, hardware-software co-designed AI computing architecture. Its core design philosophy is to maximize the efficiency, flexibility, and scalability of AI computation through simplification and reconfigurability.

### Core Design Philosophy

> The design philosophy of SRDA™ is rooted in a deep understanding of the characteristics of AI workloads.

1.  **Dataflow-Driven**
    * AI computation is fundamentally a large-scale, structured "dataflow" process.
    * SRDA places "dataflow" optimization at its core, using a compiler to statically map the compute graph directly onto the hardware for point-to-point data transfer between compute units.
    * This design minimizes data movement, allowing "compute to follow the data" and maximizing the proportion of effective computation.

2.  **Deep Hardware-Software Co-design**
    * From its inception, SRDA emphasizes deep co-design, treating software simplicity and usability as core architectural metrics.
    * The compiler has a precise understanding of the hardware's reconfigurable features, memory system, and interconnects, enabling global static optimization at compile time.
    * This deep integration achieves a level of optimization unattainable by general-purpose architectures.
    * The software stack provides a simple access layer for high-level AI frameworks (like PyTorch, JAX), allowing developers to leverage SRDA's power without needing to know the underlying hardware details.

3.  **Simplicity and Efficiency**
    * As an AI Domain-Specific Architecture (AI-DSA), SRDA strips away the complex control logic and redundant instruction sets found in general-purpose processors.
    * Hardware resources are focused on core AI operations like tensor and vector processing, leading to higher area and energy efficiency.
    * Built on the open-source RISC-V instruction set ecosystem, it significantly simplifies operator development and reduces costs.

4.  **Reconfigurability and Adaptability**
    * SRDA is not a rigid, fixed-function accelerator; its hardware data paths, compute functions, and memory access patterns can be configured by software.
    * This allows it to flexibly adapt to diverse and evolving model structures (e.g., Transformer, MoE, Mamba, DiT) and future-proofs the architecture against new AI algorithms.
    * Through controlled reconfigurability, SRDA strikes an ideal balance between the efficiency of a dedicated accelerator and the flexibility of a general-purpose processor.

### Key Architectural Innovations

Base on SRDA, Moonquest-AI integrates several key technological breakthroughs into our first generation AI Chip product.

#### QDDM™: Distributed On-chip 3D-Stacked Memory
* **Goal**: To break through the "memory wall".
* **Implementation**: Utilizes 3D stacking to integrate a high-bandwidth, high-capacity distributed memory network directly on the compute chip.
* **Features**:
    * **Privatized Memory**: Each compute core has its own private memory, eliminating bandwidth competition and access conflicts.
    * **Specialized Controller**: An integrated, custom 3D-DRAM controller reduces access latency and provides dedicated data acceleration functions.
    * **Yield Enhancement**: Incorporates a specialized solution to ensure the feasibility and cost-effectiveness of large-scale production.

#### QLink™: Converged High-Speed Interconnect
* **Goal**: To build a unified, efficient, and low-cost interconnect for large-scale clusters.
* **Implementation**: Merges multiple network layers (like NVLink, InfiniBand) into a single, unified QLink network for seamless scaling from core-to-core to node-to-node.
* **Features**:
    * **Converged Architecture**: Simplifies network topology, reduces management complexity, and eliminates the need for expensive dedicated NICs.
    * **Independent Communication Engine**: Decouples compute and communication tasks, freeing up valuable core compute resources.
    * **Linear Scalability & Reliability**: Supports near-linear scaling for massive AI clusters (e.g., 100,000-accelerator scale) with enhanced reliability.

#### High-Performance Compute Engine
* **Reconfigurable Dataflow**: Dynamically builds optimized computation paths based on model operators, allowing intermediate results to be passed directly between units and dramatically reducing data movement.
* **Low-Precision Support**: Provides native support for trending low-precision data types like FP8, FP6, and FP4 to reduce memory footprint and increase throughput.
* **Flexible Operations**: Compute units support flexible combinations of operations, ensuring strong general-purpose applicability for AI workloads.

#### Minimalist AI Compiler & Software Stack
* **Static Compilation**: Performs most optimizations at compile-time through static compute graph analysis.
* **RISC-V Ecosystem**: Built on the open-source RISC-V ISA, simplifying low-level development.
* **Framework Compatibility**: Designed for compatibility with mainstream frameworks like PyTorch and JAX for smooth user migration.
* **Unified Resource Management**: The compiler enables unified and efficient management of network, compute, and storage at the cluster level.

## Technical Advantages at a Glance

* ✅ **Ultra-High Compute Utilization**: Maximizes effective computation time by integrating compute and memory and decoupling compute from communication.
* ✅ **Exceptional Memory Bandwidth & Efficiency**: QDDM™ technology effectively alleviates the memory bottleneck in large model applications.
* ✅ **Cost-Effective Large-Scale Expansion**: QLink™ technology simplifies network deployment and lowers interconnect costs for massive clusters.
* ✅ **High Performance on Mature Processes**: Achieves high effective compute on mature manufacturing processes without relying on cutting-edge nodes.
* ✅ **Optimized Total Cost of Ownership (TCO)**: Delivers superior TCO by boosting single-node performance and reducing cluster deployment and maintenance complexity.
* ✅ **Flexible Model & Algorithm Adaptability**: Reconfigurability allows SRDA to adapt to constantly evolving AI models and algorithms.
* ✅ **Developer-Friendly Migration**: Compatibility with mainstream frameworks and a simplified software stack lower the barrier to entry for users.

## Our Vision: The "Moonquest"

The launch of SRDA is both a response to today's compute bottlenecks and a vision for the future of AI computing. We believe SRDA can become the superior computing architecture for the next generation of large AI models. Our goals include:
* Reshaping data centers and intelligent compute networks.
* Empowering next-generation AI models and complex applications.
* Exploring the paradigm shift in AI computing architectures.
* Building an open and collaborative ecosystem.
