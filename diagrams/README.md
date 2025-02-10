MediatorManager Diagrams

```mermaid
---
title: Mount Name with different IP
---
flowchart TB
    start@{ shape: circle, label: "Start" } --> ping1[Ping existing assigned ip-address of mount-name]
    ping1 --> decision1{successful?}
    decision1 --yes--> reject1[reject request with 409 Operational management connection of <mountname> would be cut]
    reject1 --> stop@{ shape: circle, label: "stop" }
    decision1 -- no --> process1[delete existing mediator instance of the mount-name]
    process1  --> process2[create new mediator instance for the desired mount-name + ip-address combination]
    process2 --> process3[response request with 204 no content]
    process3 --> stop@{ shape: circle, label: "stop" }
```
