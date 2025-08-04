- [Introduction](#introduction)
- [Structural Components](#structural-components)
- [Queueing Systems](#queueing-systems)
  - [Single-Server Queueing Systems](#single-server-queueing-systems)
  - [Two-Server Queueing System in Series](#two-server-queueing-system-in-series)
  - [Two-Server Queueing System in Parallel](#two-server-queueing-system-in-parallel)

# Introduction

**Discrete Event Simulation**: A tool that represents a dynamic model of a real system, where changes in the state occur at specific points in time called *events*. Unlike continuous models, this simulation focuses on discrete events that alter the system’s flow or state, making it ideal for processes with discrete and random characteristics.

**Discrete Event**: Represents a specific and punctual change that alters the state of the system in a simulation. For example: the arrival of a raw material, the start or end of an operation, or the availability of a resource. Events are the foundation of the model since each event triggers variable changes and advances the simulation time.

**Discrete Event Systems vs. Continuous Event Systems**:
- *Discrete Event Systems*: Experience abrupt changes at specific instants (e.g., queues in a bank), using tools like automata or event lists.
- *Continuous Event Systems*: Characterized by smooth changes in state variables over time, modeled by differential equations (e.g., pendulum motion).

# Structural Components

**Structural Components of a Discrete Event Simulation**: This structure is composed of interdependent elements to model complex dynamics:

- *System State*: Set of variables defining the critical properties of the system at a given instant (e.g., number of customers in a queue, machine availability).
- *Time Variable*: Refers to the amount of simulation time elapsed ($t$).
  - *Counting Variables*: Variables that count how many times an event has occurred up to time $t$.
- *Event Sequence*: Data structure that schedules events in an organized manner, prioritizing their execution.
- *Entities*: Dynamic elements flowing through the system, generating events and modifying the state. They represent objects or agents actively participating in the simulation. Classified as:
  - *Temporary*: Exist for a limited time (e.g., customers in a bank, vehicles on a highway, packages in a logistics network).
  - *Permanent*: Exist during the entire simulation though can change state (e.g., machines in a factory, traffic lights at an intersection, servers in a data center). These usually serve temporary entities.
- *Resources*: Limited static elements that provide capacity to serve entities. They are passive: they do not generate events themselves but are required by entities to progress. The availability of these resources defines system efficiency, as entities wait in queues if no resources are free. Classified as:
  - *Fixed*: Finite capacity released after use (e.g., cashiers in a supermarket, cranes at a port, communication channels). Entities occupy and release them, like a customer using a cashier for 5 minutes then freeing it.
  - *Consumable*: Physically depleted upon use (e.g., raw materials in manufacturing, money in a cash register). Entities consume them, permanently reducing their stock.

# Queueing Systems

## Single-Server Queueing Systems

**Definition**: A system where a single server attends all customers, who form a single waiting queue.

**Structure**: Queue → Server → Exit

**Operation**: If the server is busy, new customers wait in the queue (under policies like FIFO, LIFO, or priorities). When a service ends, the server attends the next customer in line.

## Two-Server Queueing System in Series

**Definition**: A system where customers must be served sequentially by two independent servers, first by server 1 and then by server 2.

**Structure**: Initial Queue → Server 1 → Intermediate Queue → Server 2 → Exit

**Operation**: After being served by server 1, customers enter an intermediate queue. If server 2 is busy, they wait in that queue until served.

## Two-Server Queueing System in Parallel

**Definition**: A system where two servers attend customers from a single shared queue, operating independently.

**Structure**: Queue → Server 1 / Server 2 → Exit

**Operation**: Customers are assigned to the first available server. If both are free, an assignment rule applies (e.g., prioritize the server with the longest idle time).
