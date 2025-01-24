# MediatorManager Specification
The MediatorManager application will handle the creation and deletion of mediator instances.  

### Features covered by MediatorManager version 1.0.0:
- Defining MediatorVM templates
- Instantiating MediatorVMs from templates (incl. storing address of MediatorInstanceManagers)
- Creating new mediator processes (while regarding the engineering limits defined in the MediatorVM templates)
- Deleting existing mediator processes
- Automated load balancing accross MediatorVMs
- ApplicationPattern version 2.1.2
- Configuration data hand-over between application releases

### Creating a new mediator process
To create a new mediator process, following steps will be performed
- Calculate the respective load on the MediatorVMs for the incoming device's model name
- Chose the  MediatorVM with the lowest load
- Compare this load with the engineering limit
- Potentially create a mediator process on that MediatorVM

### Deletes existing mediator process
To delete a mediator process, following steps will be performed
- Get the list of MediatorInstanceManagers stored in the APPData file
- Find the MediatorInstanceManager that has the same ip-address as the incoming "mediator-ip-address" of the device and delete the instance.

[Thorsten]: # (Don't want to say that it would be a good idea, but at least want to put the idea on the table: Why not sending the delete to all xMIM? They can't delete what not exists and as an idempotent implementation they have to respond 204 anyway.)

### Proposal for future versions:
- Defining threshold cross alarms for informing about almost reaching the engineering limit shall be considered. 

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

