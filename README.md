# GRED
**DPDK** -
  The Data Plane Development Kit (DPDK) is a set of data plane libraries and network interface controller drivers for fast packet processing.
  The DPDK framework creates a set of libraries for specific hardware/software environments through the creation of an Environment Abstraction Layer (EAL).
  The EAL hides the environment specifics and provides a standard programming interface to libraries, available hardware accelerators and other hardware and operating system (Linux, FreeBSD) elements.
  Once the EAL is created for a specific environment, developers link to the library to create their applications.

**Active queue management** - 
  In routers and switches, active queue management (AQM) is the policy of dropping packets inside a buffer associated with a network interface controller (NIC) before that buffer becomes full, often with the goal of reducing network congestion or improving end-to-end latency.
  This task is performed by the network scheduler, which for this purpose uses various algorithms such as random early detection (RED), Explicit Congestion Notification (ECN), or controlled delay (CoDel).
  Active queue disciplines drop or mark packets before the queue is full. Typically, they operate by maintaining one or more drop/mark probabilities, and probabilistically dropping or marking packets even when the queue is short.
  
**RED** - 
  Random early detection (RED), also known as random early discard or random early drop is a queuing discipline for a network scheduler suited for congestion avoidance.
  In the conventional tail drop algorithm, a router or other network component buffers as many packets as it can, and simply drops the ones it cannot buffer. If buffers are constantly full, the network is congested. Tail drop distributes buffer space unfairly among traffic flows.
  Tail drop can also lead to TCP global synchronization as all TCP connections "hold back" simultaneously, and then step forward simultaneously. Networks become under-utilized and flooded—alternately, in waves. 
  RED addresses these issues by pre-emptively dropping packets before the buffer becomes completely full. It uses predictive models to decide which packets to drop. 
  RED monitors the average queue size and drops (or marks when used in conjunction with ECN) packets based on statistical probabilities. If the buffer is almost empty, then all incoming packets are accepted. 
  As the queue grows, the probability for dropping an incoming packet grows too. When the buffer is full, the probability has reached 1 and all incoming packets are dropped.
  
**GRED** - 
  GRED(Gentle Random Early Detection)  was  proposed  as  an  AQM  method that  controls  congestion  at  router  buffers preliminary. GRED aims to solve some of RED’s problems. 
  GRED was proposed as a variant of RED, in which  GRED  enhances  the  way  of  tuning some  of  RED’s  parameters  such  as maxthreshold and Dmax(the maximum value of the initial packet dropping probability).
  Moreover, GRED maintains the aql(average queue length) value at a level on a   router   buffer   which   is   between   the minthreshold and maxthreshold positions,this level is named Taql(Target level for the aql).
  Maintaining aql value  at Taql level avoids increasing the router buffer size to be above the maxthreshold position, and therefore smaller number of packets is dropped. 

