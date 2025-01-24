# MediatorManager Specification
The MediatorManager application will handle the creation/deletion of mediator instance for the newly mounted/unmounted devices respectively. MountingOrchestrator application trigger the creation/deletion of a mediator instance via this application based on the activity performed by the field engineer through APT.  

[Thorsten]: # (We cannot tell today, which applications will consume the api of the MM, in future. We should abstract the information here.)

### Features covered by MediatorManager version 1.0.0:
- Stores information about MediatorInstanceManagers
- Creates new mediator instances
- Deletes existing mediator instances
- LoadBalancing Mechanism 
- Handling Engineering limits of the Mediators
- ApplicationPattern version 2.1.2
- Bequeathing process transfers the list of regarded MIM clients from old to new release

### Creates new mediator instances
To create a new mediator instance , following steps will be performed
- Get the list of MediatorInstanceManagers stored in the APPData file

[Thorsten]: # (Not sure whether we have the same understanding. The connection between the MM and xMIM is a communication connection alike between applications or between devices. Address information of the xMIM should be stored in the CONFIGfile not in an APPData.)

- Filter the MediatorInstanceManagers those are defined for the incoming device's model name
- If LoadBalancing is turned ON in the string-profile(allocationMethodType) then the MediatorInstanceManager with the least load considered and a instance will be created. 

[Thorsten]: # (Understood, but what would happen, if load balancing is switched off? Does this alternative behavior make sense? Does it make sense to switch load balancing off?)

### Deletes existing mediator instances
To delete a mediator instance, following steps will be performed
- Get the list of MediatorInstanceManagers stored in the APPData file
- Find the MediatorInstanceManager that has the same ip-address as the incoming "mediator-ip-address" of the device and delete the instance.

[Thorsten]: # (Don't want to say that it would be a good idea, but at least want to put the idea on the table: Why not sending the delete to all xMIM? They can't delete what not exists and as an idempotent implementation they have to respond 204 anyway.)

### Proposal for MediatorManager Future version:
- A cyclic process shall check(for a fixed frequency) whether any of the MediatorInstanceManager exceeds its engineering limits. If so, an alarm shall be raised to the upcoming AlarmManagement application. So that proactively measures shall be taken.

[Thorsten]: # (If the MM would be the only instance allowed to address the xMIM services, there would be no exceeding of the engineering limits, except the engineering limit would be lowered during operation. If this would happen, I would expect the load balancer to take care for keeping the limites. An alarm only to be send, if this would not be feasible.)

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

