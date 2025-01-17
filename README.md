# MediatorManager

### Location
The MediatorManager is part of the OperationSupport.

### Description
The MediatorManager decides about which MediatorInstanceManager to be addressed for provisioning of a mediator process for an individual device. It is regarding device type and e.g. load balancing criteria. Future versions might support re-allocation of mediator processes based on planned operational activities like replacement of a mediator virtual machine or unplanned events like failure of a mediator virtual machine.

New and to be discussed:
A prerequisite for creating or modifying a mediator is that the IP address provided as an input is not used for an existing mediator instance with another mount name in connected state.

### Relevance
The MediatorManager is required for connecting devices to the controller.

### Resources
- [Specification](./spec/)
- [TestSuite](./testing/)
- [Implementation](./server/)

### Comments
./.
