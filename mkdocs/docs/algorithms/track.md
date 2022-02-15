### Difference between tracking and tracing

[From StackExchange:](http://ell.stackexchange.com/questions/34391/difference-between-track-and-trace):

> The difference is in direction & point in time:

> To trace: follow the completed path backwards from its current point to where it began.

> To track: follow the emerging path forwards from your starting point to wherever the thing currently is.

> When you "trace" a cellphone call, you try to determine its origin... You go backward to the starting point.

> When you "track" a cellphone, you monitor [the starting] location ... and follow it wherever it goes...

One of the most-often used traces is to find the origins of health problems like mad cow disease and tainted drugs and food. In Valueflows terms, that would start with the product (economic resource) that caused a health problem, and trace back along the chain of resource flows to the source or sources of the product.  Then it might be necessary to also track forwards from the source(s) to find everything else that might include that source(s).

It is also used when the provenance is useful for other information, like to determine the sustainability of the creation of a resource (like fossil fuel inputs, potential carbon implications, etc.), how healthy the inputs are, how local is the production and distribution, etc.  Or when an agent is interested in what happens to a resource they created, for example what is the effect of their recycling efforts or material donations to an educational program.

Also, this logic is used in other features, like "contribution economy" calculations.

Terminology note:
* `previous` and `next` bring back the element one layer backwards or forwards
* `track` and `trace` bring back the whole resource flow forwards or backwards, starting with a resource (or a deliver-service? or... ?)

### Previous and next logic

Here is the logic finding the flow element that comes directly after a particular element (next for tracking) and immediately before a particular element (previous for tracing):

* For an EconomicResource:
    * next:
        * EconomicEvents affecting it that are inputs to Processes (`resourceInventoriedAs`), or
        * transfer (any kind) or move EconomicEvents with the EconomicResource referenced as `resourceInventoriedAs`
    * previous:
        * EconomicEvents affecting it that are outputs from Processes (`resourceInventoriedAs`), or
        * transfer (any kind) or move EconomicEvents with the EconomicResource referenced as `toResourceInventoriedAs`
* For a Process:
    * next:
        * EconomicEvents that are outputs
    * previous:
        * EconomicEvents that are inputs
* For an EconomicEvent:
    * next:
        * a Process to which it is an input, or
        * an EconomicResource which it affected as the output of a Process, or
        * if it is a transfer (any kind) or move event, the EconomicResource referenced as `toResourceInventoriedAs`
    * previous:
        * a Process from which it is an output, or
        * an EconomicResource which it affected as the input of a Process, or
        * if it is a transfer (any kind) or move event, the EconomicResource referenced as `resourceInventoriedAs`
        * if it is a pack event, the EconomicResource referenced as `containedIn`

### Tracking identifier and lot

Currently, often companies' internal flow information is not public, although in many countries they are required to be able to provide input and output information when needed in a medical emergency, without connecting all the dots internally.  Also any organization can be missing resource flow data so that there are gaps in the flows, no matter the level of transparency.

For these reasons, tracking identifier (often a serial number) and a standard lot identifier are currently used when food or medical tracing and tracking is required.  And in VF, they can be used whenever there is missing resource flow information for any reason.

Note that in VF, for simplicity, besides `lot`, a lot identifier can be stored in the `trackingIdentifier` property.

Also note that lots get "spread out" into splits of a resource or different types of resources.  For example, one cow could have a lot identifier, which when the cow goes through a butchering process will be included in all the cuts of beef from that cow.  Or one production batch of a medicine that contains many packages of the same medicine would have a lot identifier, which follows all the individual packages wherever they go.


### Track and trace Logic

To gather a whole track or trace..... recursive logic; topological sort  maybe, but I don't think so; ...


some specifics....

When dealing with resources that are packed into and unpacked from a container resource, if the resource has been packed, then the logic needs to follow the container resource until the resource is unpacked.


for an event, next:
        * if it is a pack event, handle normally as above (a Process to which it is an input), but... coming out of that Process you will see the modify event of the container, referencing the container EconomicResource, but you have to remember the original resource also, which is now in the container, see diagram at https://www.valueflo.ws/examples/ex-production/#pack-unpack
        * if it is an unpack event, handle normally as above (an EconomicResource which it affected), but... you will not be tracking the container any more

for an event, previous:
        * if it is a pack event, the EconomicResource referenced as `containedIn` ... but keep track of the original resource...
        * if it is an unpack event, the Process as normal, ... but then follow the container in `containedIn` while remembering the contained resource to find again when it is packed


When the same economic resource is both input and output of a process, sometimes a series of processes, such as for repair or quality testing or a workflow where a resource is refined through stages like writing/editing/etc, the stage must be identified, based on the kind of process the resource was last output of.

state.....

how to pick the best previous or next when the resource is the same through multiple stages or cycles, so that previous or next returns multiple records, which will only happen when a resourc is looking for output events that reference it.... I thnk we will have to use event dates, but discussion is ongoing...
