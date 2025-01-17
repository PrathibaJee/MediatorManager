# MediatorManager Specification
The MediatorManager application will handle the creation/deletion of mediator instance for the newly mounted/unmounted devices respectively. MountingOrchestrator application trigger the creation/deletion of a mediator instance via this application based on the activity performed by the field engineer through APT.

### Features covered by MediatorManager version 1.0.0:
- Stores information about MediatorInstanceManagers
- Creates new mediator instances
- Deletes existing mediator instances
- LoadBalancing Mechanism 
- Handling Engineering limits of the Mediators
- ApplicationPattern version 2.1.2

### Creates new mediator instances
To create a new mediator instance , following steps will be performed
- Get the list of MediatorInstanceManagers stored in the APPData file
- Filter the MediatorInstanceManagers those are defined for the incoming device's model name
- If LoadBalancing is turned ON in the string-profile(allocationMethodType) then the MediatorInstanceManager with the least load considered and a instance will be created. 
 
### Deletes existing mediator instances
To delete a new mediator instance , following steps will be performed
- Get the list of MediatorInstanceManagers stored in the APPData file
- Find the MediatorInstanceManager that has the same ip-address as the incoming "mediator-ip-address" of the device and delete the instance.

### Proposal for MediatorManager Future version:
- A cyclic process shall check(for a fixed frequency) whether any of the MediatorInstanceManager exceeds its engineering limits. If so , an alarm shall be raised to the upcoming AlarmManagement application. So that proactively measures shall be taken.

### Dependencies
- TAC version 2.1.2
- [MediatorInstanceManager](https://github.com/openBackhaul/MediatorInstanceManager)

### Diagrams  
- [Collection of Diagrams](./diagrams)

### ServiceList
- [MediatorManager+services](./MediatorManager+services.yaml)

### ProfileList and ProfileInstanceList
- [MediatorManager+profiles](./MediatorManager+profiles.yaml)
- [MediatorManager+profileInstances](./MediatorManager+profileInstances.yaml)

### ForwardingList
- [MediatorManager+forwardings](./MediatorManager+forwardings.yaml)

### Open API specification (Swagger)
- [MediatorManager](./MediatorManager.yaml)

### CONFIGfile (JSON)
- [MediatorManager+config](./MediatorManager+config.json)

### Comments
./.

