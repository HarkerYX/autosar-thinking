## Background

The AUTOSAR partnership is an alliance of OEM manufacturers, Tier 1 automotive suppliers, semiconductor manufactures, software suppliers, tool suppliers and others. Considering the different automotive E/E architectures in the current and future markets, the partnership established a de-facto open industry standard for an automotive software architecture. It will serve as a basic infrastructure for the management of functions within both future applications and standard software modules.





## Introduction to AUTOSAR Classic

Automotive systems are often developed in a collaborative effort between OEMs and suppliers. Suppliers develop subsystems specified by the OEM or develop their own subsystem that they sell as an “off-the-shelf” product. Before AUTOSAR, the collaboration relied on specification languages defined within the OEM-Supplier partnership. A new partnership began with an agreement on a new specification language, and integrating a proprietary supplier component required adaptation efforts. With the growing demand of new vehicle functions and the expansion into several domains, the old collaboration approach became impractical. Distributed functionalities in the vehicle architecture also added complexity. AUTOSAR was created to make this complexity manageable, by providing a system-based design environment for the development teams creating the software architecture. [source](https://www.btc-es.de/en/blog/autosar-what-every-function-developer-should-know.html)

### Modular architecture and virtual communication bus

To manage the complexity, AUTOSAR introduced a modular architecture with layers to separate hardware-independent application software from hardware-oriented software.

- The upper layer, **Application Software (ASW)** hosts the application functions as individual software components (SWC).
- The lower layer, the **Basic Software (BSW)** includes low level software like services and hardware specific software.
- Between these layers is an abstraction layer called the **Runtime Environment (RTE)** that manages the interface between the two other layers.

AUTOSAR also provides a way to decouple the applications from the hardware infrastructure. AUTOSAR introduced the concept of Virtual Functional Bus (VFB) which makes it possible for the SWCs to interact independently from where they are executed in the system (inside one ECU or on different ECUs).  As SWCs are allocated to the various ECUs, the virtual connections are mapped to local connections (intra-ECU) or onto network communication technologies such as CAN or FlexRay (inter-ECUs). The connection mapping is implemented by the RTE and becomes the concrete interface between individual SWCs and also between SWCs and the BSW (the RTE implements the VFB on a specific ECU).

With the VFB, OEMs and suppliers can develop multi-domains and competitive software without detailed knowledge on the lower-level technologies or dependencies. It gives the flexibility to scale the overall system afterwards (e.g. number of ECUs, ECU-to-Application mapping, network technology, etc.). It enables the reusability and transferability of software components and makes it easier to add new functions to the system. Moreover, the VFB validates all plausible communication between SWCs, which will detect any software architecture errors and improve the software architecture quality.

### classic platform

https://www.autosar.org/standards/classic-platform/

### adaptive platform

https://www.autosar.org/standards/adaptive-platform/







## Reference

1. https://www.etas.com/en/company/news-archive-2018-the-adaptive-platform-a-new-autosar.php
2. https://www.methodpark.de/blog/autosar-part-1-the-classic-platform/
3. https://www.btc-es.de/en/blog/autosar-what-every-function-developer-should-know.html
