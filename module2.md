# MODULE 2

# Logical and System Architectures of Distributed Systems

Distributed systems architecture enables applications to communicate and share resources in a distributed environment. This document provides detailed learning material on the **Logical Architecture** and **System Architecture** of distributed systems.

---

## **1. Logical Architectures of Distributed Systems**

Logical architecture defines how the components of a distributed system interact with one another conceptually. It focuses on **logical layers and responsibilities** rather than specific physical implementations.

### **Key Logical Architectures**

### **1.1. Layered Architecture**

- **Definition**: Components are organized into layers, where each layer provides services to the layer above and consumes services from the layer below.
- **Layers**:
  1. **Presentation Layer**: Responsible for user interface and experience.
  2. **Business Logic Layer**: Handles the application’s processing, rules, and logic.
  3. **Data Access Layer**: Manages database interactions.
  4. **Data Storage Layer**: Stores persistent data.
- **Advantages**:
  - Clear separation of concerns.
  - Easier to develop, test, and maintain.
- **Use Cases**: Enterprise applications, web applications.

### **1.2. Object-Based Architecture**

- **Definition**: Distributed as objects or components, with each object encapsulating data and operations.
- **Components**:
  - Objects communicate using Remote Method Invocation (RMI) or similar protocols.
  - Often implemented using middleware (e.g., CORBA, .NET, Java RMI).
- **Advantages**:
  - Encapsulation and modularity.
  - Supports dynamic object interaction.
- **Use Cases**: Component-based development, IoT systems.

### **1.3. Service-Oriented Architecture (SOA)**

- **Definition**: Functionality is delivered as independent services that communicate over the network using standard protocols (e.g., HTTP, REST, SOAP).
- **Components**:
  - Services provide specific functionalities.
  - Service orchestration defines workflows between multiple services.
- **Advantages**:
  - Reusability and scalability.
  - Interoperability across platforms.
- **Use Cases**: Cloud services, API-driven applications.

### **1.4. Event-Driven Architecture**

- **Definition**: Components communicate through the generation and consumption of events.
- **Components**:
  - **Producers** create events.
  - **Consumers** listen to and act on events.
  - Middleware (e.g., Kafka) manages the event flow.
- **Advantages**:
  - Decoupled components.
  - Scales well for real-time data processing.
- **Use Cases**: IoT, financial systems, real-time applications.

---

## **2. System Architectures of Distributed Systems**

System architecture describes how distributed system components are physically deployed, structured, and managed.

### **Key System Architectures**

### **2.1. Client-Server Architecture**

- **Definition**: The system is divided into two main roles: **clients** (requesters) and **servers** (providers).
- **Components**:
  - **Client**: Sends requests to the server and displays results.
  - **Server**: Processes requests and sends responses back.
- **Advantages**:
  - Centralized server simplifies management.
  - Easier to maintain.
- **Disadvantages**:
  - Bottlenecks under heavy load.
  - A single point of failure (server).
- **Use Cases**: Web applications, file storage systems.

### **2.2. Peer-to-Peer (P2P) Architecture**

- **Definition**: All nodes have equal responsibilities and capabilities, acting as both clients and servers.
- **Types**:
  - **Pure P2P**: Fully decentralized (e.g., BitTorrent).
  - **Hybrid P2P**: Includes a centralized directory or lookup server.
- **Advantages**:
  - High scalability and fault tolerance.
  - Reduced dependency on a central server.
- **Disadvantages**:
  - Complex to manage and secure.
- **Use Cases**: File sharing, blockchain, distributed computing.

### **2.3. Multi-Tier Architecture**

- **Definition**: Components are distributed among multiple tiers, with each tier dedicated to a specific function.
- **Tiers**:
  1. **Client Tier**: User interface and input.
  2. **Application Tier**: Business logic and processing.
  3. **Database Tier**: Storage and data management.
- **Advantages**:
  - Improves modularity and scalability.
  - Separation of database and application logic enhances security.
- **Disadvantages**:
  - Increased complexity.
  - Higher latency compared to simpler architectures.
- **Use Cases**: Large-scale web services, ERP systems.

### **2.4. Microservices Architecture**

- **Definition**: Application is composed of small, independent services that communicate through APIs.
- **Features**:
  - Each service has its own data store and runs independently.
  - Services are deployed and scaled independently.
- **Advantages**:
  - Enhanced flexibility and scalability.
  - Failure in one service doesn’t bring down the entire system.
- **Disadvantages**:
  - Difficult to monitor and manage.
  - High overhead due to service communication.
- **Use Cases**: Cloud-native applications, large e-commerce platforms.

---

## **Comparing Logical and System Architectures**

| **Aspect**        | **Logical Architecture**                               | **System Architecture**                              |
|--------------------|-------------------------------------------------------|----------------------------------------------------|
| **Focus**         | Conceptual organization and interaction of components. | Physical deployment and system configuration.      |
| **Examples**      | Layered, SOA, Object-Based, Event-Driven.             | Client-Server, P2P, Multi-Tier, Microservices.     |
| **Responsibility**| Defines the logical flow and layers of applications.   | Manages communication, deployment, and scalability.|

---

## **Challenges in Designing Distributed Architectures**

1. **Scalability**: Ensuring the system grows efficiently under increased load.
2. **Fault Tolerance**: Guaranteeing reliability despite component failures.
3. **Consistency**: Maintaining synchronized states across distributed components.
4. **Security**: Protecting interactions and data within distributed environments.
5. **Performance**: Balancing latency, bandwidth, and throughput.
<br><br>

# Clock Synchronization in Distributed Systems

In distributed computing, where multiple systems collaborate to accomplish tasks, ensuring that all the clocks are synchronized plays a crucial role. Clock synchronization involves aligning the clocks of computers or nodes, enabling efficient data transfer, smooth communication, and coordinated task execution. This article explores the importance of clock synchronization in distributed systems, discusses the challenges it addresses, and delves into approaches used to achieve synchronization.<br>

## What is Clock Synchronization in Distributed Systems?

Clock synchronization in distributed systems refers to the process of ensuring that all clocks across various nodes or computers in the system are set to the same time or at least have their times closely aligned.

In a distributed system, where multiple computers communicate and collaborate over a network, each computer typically has its own local clock. However, due to factors such as hardware differences, network delays, and clock drift (inaccuracies in timekeeping), these local clocks can drift apart over time.<br><br>

## Importance of Clock Synchronization

### Consistency and Coherence

Clock synchronization ensures that timestamps and time-based decisions made across different nodes in the distributed system are consistent and coherent. This is crucial for maintaining the correctness of distributed algorithms and protocols.

### Event Ordering

Many distributed systems rely on the notion of event ordering based on timestamps to ensure causality and maintain logical consistency. Clock synchronization helps in correctly ordering events across distributed nodes.

### Data Integrity and Conflict Resolution

In distributed databases and file systems, synchronized clocks help in timestamping data operations accurately. This aids in conflict resolution and maintaining data integrity, especially in scenarios involving concurrent writes or updates.

### Fault Detection and Recovery

Synchronized clocks facilitate efficient fault detection and recovery mechanisms in distributed systems. Timestamps can help identify the sequence of events leading to a fault, aiding in debugging and recovery processes.

### Security and Authentication

Timestamps generated by synchronized clocks are crucial for security protocols, such as in cryptographic operations and digital signatures. They provide a reliable basis for verifying the authenticity and temporal validity of transactions and messages.<br><br>

## Bridging Time Gaps

Clock synchronization in distributed systems aims to establish a reference for time across nodes.

Imagine a scenario where three distinct systems are part of a distributed environment. In order for data exchange and coordinated operations to take place, these systems must have a shared understanding of time.

Achieving clock synchronization ensures that data flows seamlessly between them, tasks are executed coherently, and communication happens without any ambiguity.<br><br>

## Types of Clock Synchronization in Distributed Systems

### 1. Physical Clock Synchronization

In distributed systems, each node operates with its own clock, which can lead to time differences. The goal of physical clock synchronization is to overcome this challenge. This involves equipping each node with a clock that is adjusted to match Universal Coordinated Time (UTC), a recognized standard. By synchronizing their clocks in this way, diverse systems across the distributed landscape can maintain harmony.

- **Addressing Time Disparities:** The goal is to minimize these disparities by aligning the clocks.
- **Using UTC as a Common Reference Point:** The key to achieving this synchronization lies in adjusting the clocks to adhere to UTC.

### 2. Logical Clock Synchronization

In distributed systems, absolute time often takes a backseat to logical clock synchronization. Think of clocks as storytellers that prioritize the order of events over their exact timing. These clocks enable the establishment of connections between events, like weaving threads of cause and effect. By bringing order and structure into play, task coordination within distributed systems becomes akin to a choreographed dance where steps are sequenced for execution.

- **Event Order Over Absolute Time:** The primary objective is to establish connections between events.
- **Approach towards Understanding Behavior:** Logical clocks serve as storytellers weaving together a narrative of events. This narrative enhances comprehension and facilitates coordination within the distributed system.

### 3. Mutual Exclusion Synchronization

In the bustling symphony of distributed systems, one major challenge is managing shared resources. Imagine multiple processes competing for access to the resource simultaneously. To address this issue, mutual exclusion synchronization comes into play as an expert technique that reduces chaos and promotes resource harmony. This approach relies on creating a system where different processes take turns accessing shared resources.

- **Managing Resource Conflicts:** This synchronization approach ensures that resources are accessed sequentially, minimizing conflicts and collisions.
- **Enhancing Efficiency through Sequential Access:** By orchestrating access in this manner, resource utilization and overall system efficiency are optimized.<br><br>

## Techniques of Clock Synchronization in Distributed Systems

Clock synchronization techniques aim to address the challenge of ensuring that clocks across distributed nodes in a system are aligned or synchronized. Here are some commonly used techniques:

### 1. Network Time Protocol (NTP)

**Overview:** NTP is one of the oldest and most widely used protocols for synchronizing clocks over a network. It is designed to synchronize time across systems with high accuracy.

**Operation:**
- **Client-Server Architecture:** NTP operates in a hierarchical client-server mode. Clients (synchronized systems) periodically query time servers for the current time.
- **Stratum Levels:** Time servers are organized into strata, where lower stratum levels indicate higher accuracy and reliability (e.g., stratum 1 servers are directly connected to a reference clock).
- **Timestamp Comparison:** NTP compares timestamps from multiple time servers, calculates the offset (difference in time), and adjusts the local clock gradually to minimize error.

**Applications:** NTP is widely used in systems where moderate time accuracy is sufficient, such as network infrastructure, servers, and general-purpose computing.

### 2. Precision Time Protocol (PTP)

**Overview:** PTP is a more advanced protocol compared to NTP, designed for high-precision clock synchronization in environments where very accurate timekeeping is required.

**Operation:**
- **Master-Slave Architecture:** PTP operates in a master-slave architecture, where one node (master) distributes its highly accurate time to other nodes (slaves).
- **Hardware Timestamping:** PTP uses hardware timestamping capabilities (e.g., IEEE 1588) to reduce network-induced delays and improve synchronization accuracy.
- **Sync and Delay Messages:** PTP exchanges synchronization (Sync) and delay measurement (Delay Request/Response) messages to calculate the propagation delay and adjust clocks accordingly.

**Applications:** PTP is commonly used in industries requiring precise time synchronization, such as telecommunications, industrial automation, financial trading, and scientific research.

### 3. Berkeley Algorithm

**Overview:** The Berkeley Algorithm is a decentralized algorithm that aims to synchronize the clocks of distributed systems without requiring a centralized time server.

**Operation:**
- **Coordinator Election:** A coordinator node periodically gathers time values from other nodes in the system.
- **Clock Adjustment:** The coordinator calculates the average time and broadcasts the adjustment to all nodes, which then adjust their local clocks based on the received time difference.
- **Handling Clock Drift:** The algorithm accounts for clock drift by periodically recalculating and adjusting the time offset.

**Formula:**
The average time T_avg is calculated as:
T_avg = (1/N) * ∑(T_i)
where N is the number of nodes and T_i is the time of the i-th node.

Each node then adjusts its clock by:
T_new = T_old + (T_avg - T_old)

**Applications:** The Berkeley Algorithm is suitable for environments where a centralized time server is impractical or unavailable, such as peer-to-peer networks or systems with decentralized control.

### 4. Christian's Algorithm

**Overview:** Christian's Algorithm is another decentralized algorithm for clock synchronization in distributed systems. It aims to minimize the maximum difference between any two clocks in the system.

**Operation:**
- **Time Exchange:** Each node periodically sends its current time to all other nodes.
- **Clock Adjustment:** Upon receiving the times from other nodes, each node adjusts its clock to the average of the maximum and minimum times received.
- **Handling Clock Drift:** The algorithm accounts for clock drift by periodically recalculating and adjusting the time offset.

**Formula:**
Each node adjusts its clock by:
T_new = (T_max + T_min) / 2
where T_max is the maximum time received from other nodes and T_min is the minimum time received from other nodes.

**Applications:** Christian's Algorithm is suitable for environments where a centralized time server is impractical or unavailable, such as peer-to-peer networks or systems with decentralized control.<br><br>


## Real-World Examples of Clock Synchronization in Distributed Systems

### Network Time Protocol (NTP)

NTP is a widely used protocol for clock synchronization over the Internet. It ensures that computers on a network have accurate time information, essential for tasks such as logging events, scheduling tasks, and coordinating distributed applications.

### Financial Trading Systems

In trading systems, timestamp accuracy is critical for ensuring fair order execution and compliance with regulatory requirements. Synchronized clocks enable precise recording and sequencing of trade orders and transactions.

### Distributed Databases

Distributed databases rely on synchronized clocks to maintain consistency and coherence across replicas and nodes. Timestamps help in conflict resolution and ensuring that data operations are applied in the correct order.

### Cloud Computing

Cloud environments often span multiple data centers and regions. Synchronized clocks are essential for tasks such as resource allocation, load balancing, and ensuring the consistency of distributed storage systems.

### Industrial Control Systems

In industries such as manufacturing and automation, precise time synchronization (often using protocols like Precision Time Protocol, PTP) is critical for coordinating processes, synchronizing sensors and actuators, and ensuring timely and accurate data logging.<br><br>

## Challenges of Clock Synchronization in Distributed Systems

Clock synchronization in distributed systems introduces complexities compared to centralized ones due to the use of distributed algorithms. Some notable challenges include:

- **Information Dispersion:** Distributed systems store information on machines. Gathering and harmonizing this information to achieve synchronization presents a challenge.
- **Local Decision Realm:** Distributed systems rely on localized data for making decisions. As a result, when it comes to synchronization, we have to make decisions with information from each node, which makes the process more complex.
- **Mitigating Failures:** In a distributed environment, it becomes crucial to prevent failures in one node from disrupting synchronization.
- **Temporal Uncertainty:** The existence of clocks in distributed systems creates the potential for time variations.<br><br>

## Logical Clock in Distributed System

In distributed systems, ensuring synchronized events across multiple nodes is crucial for consistency and reliability. Enter logical clocks, a fundamental concept that orchestrates event ordering without relying on physical time. By assigning logical timestamps to events, these clocks enable systems to reason about causality and sequence events accurately, even across network delays and varied system clocks. This article explores how logical clocks enhance distributed system design.

## What are Logical Clocks?
Logical clocks are a concept used in distributed systems to order events without relying on physical time synchronization. They provide a way to establish a partial ordering of events based on causality rather than real-time clock values.

- By assigning logical timestamps to events, logical clocks allow distributed systems to maintain consistency and coherence across different nodes, despite varying clock speeds and network delays.
- This ensures that events can be correctly ordered and coordinated, facilitating fault tolerance and reliable operation in distributed computing environments.

## Lamport Clocks
Lamport clocks provide a simple way to order events in a distributed system. Each node maintains a counter that increments with each event. When nodes communicate, they update their counters based on the maximum value seen, ensuring a consistent order of events.

### Characteristics of Lamport Clocks:
- Simple to implement.
- Provides a total order of events but doesn’t capture concurrency.
- Not suitable for detecting causal relationships between events.
#### Algorithm of Lamport Clocks:
- Initialization: Each node initializes its clock LLL to 0.
- Internal Event: When a node performs an internal event, it increments its clock LLL.
- Send Message: When a node sends a message, it increments its clock LLL and includes this value in the message.
- Receive Message: When a node receives a message with timestamp T: It sets L=max⁡(L,T)+1
#### Advantages of Lamport Clocks:
- Simple to implement and understand.
- Ensures total ordering of events.

# Mutual Exclusion in Distributed Systems

Mutual exclusion is a concurrency control property introduced to prevent race conditions. It ensures that a process cannot enter its critical section while another concurrent process is currently present or executing in its critical section. In other words, only one process is allowed to execute the critical section at any given instance of time.<br><br>

## Mutual Exclusion in Single Computer Systems vs. Distributed Systems

In a single computer system, memory and other resources are shared between different processes. The status of shared resources and the status of users is easily available in the shared memory, so mutual exclusion problems can be easily solved using shared variables (e.g., semaphores).

In distributed systems, we neither have shared memory nor a common physical clock. Therefore, we cannot solve mutual exclusion problems using shared variables. To eliminate the mutual exclusion problem in distributed systems, an approach based on message passing is used. A site in a distributed system does not have complete information about the state of the system due to the lack of shared memory and a common physical clock.<br><br>

## Requirements of Mutual Exclusion Algorithm

1. **No Deadlock:** Two or more sites should not endlessly wait for any message that will never arrive.
2. **No Starvation:** Every site that wants to execute the critical section should get an opportunity to execute it in finite time. Any site should not wait indefinitely to execute the critical section while other sites are repeatedly executing the critical section.
3. **Fairness:** Each site should get a fair chance to execute the critical section. Any request to execute the critical section must be executed in the order they are made.
4. **Fault Tolerance:** In case of failure, it should be able to recognize it by itself in order to continue functioning without any disruption.<br><br>

## Key Points to Understand Mutual Exclusion

1. Mutual exclusion is an issue that frequently arises when concurrent access to shared resources by several sites is involved. For example, directory management where updates and reads to a directory must be done atomically to ensure correctness.
2. It is a fundamental issue in the design of distributed systems.
3. Mutual exclusion for a single computer is not applicable for shared resources since it involves resource distribution, transmission delays, and lack of global information.<br><br>

## Solutions to Distributed Mutual Exclusion

As we know, shared variables or a local kernel cannot be used to implement mutual exclusion in distributed systems. Message passing is a way to implement mutual exclusion. Below are the three approaches based on message passing to implement mutual exclusion in distributed systems:

### 1. Token-Based Algorithm

- A unique token is shared among all the sites.
- If a site possesses the unique token, it is allowed to enter its critical section.
- This approach uses sequence numbers to order requests for the critical section.
- Each request for the critical section contains a sequence number, which is used to distinguish old and current requests.
- This approach ensures mutual exclusion as the token is unique.
- **Example:** Suzuki–Kasami Algorithm

### 2. Non-Token-Based Approach

- A site communicates with other sites to determine which sites should execute the critical section next. This requires the exchange of two or more successive rounds of messages among sites.
- This approach uses timestamps instead of sequence numbers to order requests for the critical section.
- Whenever a site makes a request for the critical section, it gets a timestamp. The timestamp is also used to resolve any conflict between critical section requests.
- All algorithms that follow the non-token-based approach maintain a logical clock. Logical clocks get updated according to Lamport’s scheme.
- **Example:** Ricart–Agrawala Algorithm

### 3. Quorum-Based Approach

- Instead of requesting permission to execute the critical section from all other sites, each site requests only a subset of sites, which is called a quorum.
- Any two subsets of sites or quorums contain a common site.
- This common site is responsible for ensuring mutual exclusion.
- **Example:** Maekawa’s Algorithm<br><br>

# Election algorithm and distributed processing

Election algorithms are designed to choose a coordinator. 

```
In distributed system, to avoid central server designs, election algorithms can help to establish a failover server to act as the boss.

Voting/consensus algorithms are a common methodology for handling this.
```

Election Algorithms: Election algorithms choose a process from a group of processors to act as a coordinator. If the coordinator process crashes due to some reasons, then a new coordinator is elected on other processor. Election algorithm basically determines where a new copy of the coordinator should be restarted. Election algorithm assumes that every active process in the system has a unique priority number. The process with highest priority will be chosen as a new coordinator. Hence, when a coordinator fails, this algorithm elects that active process which has highest priority number.Then this number is send to every active process in the distributed system. We have two election algorithms for two different configurations of a distributed system. 


