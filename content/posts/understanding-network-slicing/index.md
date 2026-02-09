---
title: "Understanding Network slicing from the UPF Perspective"
date: 2024-07-16
lastmod: 2024-09-16
categories:
    - "Article"
tags:
    - "6G-RUPA"
    - "Position Paper"
    - "MDPI"
    - "Publication"
---

## A quick reminder about 5G mobile network layers

First, in mobile networks you have a fixed amount of layers:

![Layer view in the 3GPP way](./3gpp_way_layers.png)

If we look this with the lens of the IPC Model looks like:

![IPC Model view](./ipc_model_layers.png)

So essentially PDU-flows are mapped into Service data flows in what we
call the N DIF Layer. Service Data Flows then are mapped: First in the
N-1-core-DIF as "QoS Flows" (as per 3GPP jargon). Then, in the
N-1-radio-DIF as "Data Radio Bearer" (as per 3GPP jargon). I also find
this diagram a bit helpful to understand what I just wrote:

![QoS Flows in
5G](../../presentations/20251015_presentation/qos_flows_pdu.png)

## Network Slice Definition

Made this reminder, then if we look at the definition of 3GPP for
"Network Slice" does not tells us much. It says:

-   A set of network functions and corresponding resources necessary to
    provide the required telecommunication services and network
    capabilities [1].
-   A logical network that provides specific network capabilities and
    network characteristics [2].

But I have been doing archeology in the specs of 3GPP and I came up with
a bit better definition:

In the context of 5G, a network slice instance is a set of network and
compute resources that can be used on top of existing infrastructure and
network functions. It's something more at administrative level, but not
at network level. At network level, different PDU sessions belonging to
the same UE can be different slices if they have different NSI ID (the
identifier of the network slice instance).

In terms of the IPC Model, a network slice would be two separate N-flows
that have some sort of field in a policy that tells you if they belong
or not to the same administrative domain. So essentially seems like
network slicing is just a policy and management overlay applied to
existing mechanisms. Let's see an example:

Imagine a virtual operator (MNVO) that uses the infra of a public
operator (PLMNO) that has his own infrastructure. The PLMNO "rents" to
the MNVO part of the network. A way to do that is that the PLMNO gives
the MNVO an instance of a network slice.

So in 6G-RUPA, when a UE (belonging to the MVNO) requests a new N-flow (a
PDU session in 5G), it passes its NSI ID as part of the flow allocation
request. The PLMNO's Flow Allocator receives this request, checks the
NSI ID against its policies, and verifies: Is this a valid MVNO? Does
the requested QoS profile fit the service agreement for this slice? Has
this slice exceeded its maximum number of PDU sessions? If these policy
checks pass, the Flow Allocator proceeds to create the flow, mapping it
onto the underlying (N-1) DIFs (radio and core).

At the end, in terms of forwarding state we just don't care about
slicing. The extra flow "in parallel" has the same source and
destination, so in the forwarding table they are both agreggated. The
RMT is completely unaware of NSI IDs, MVNOs, or "slices." It just sees
two (or two thousand) N-flows all addressed to the same destination
address and aggregates them through the same forwarding-table entry.

## References

1. 3GPP TS 22.261 V20.4.0 - Service requirements for the 5G system. Available at: <https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3107>

2. 3GPP TS 23.501 V19.5.0 - System architecture for the 5G System (5GS). Available at: <https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3144>