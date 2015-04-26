<p align="center">
  <img src="https://github.com/yevhen-personal/test/blob/master/Logo.Compact.png?raw=true" alt="Streamstone's logo"/>
</p>

Streamstone is a small library targeted at building scalable event-sourced applications on top of Azure Table Storage. It has simple, functional style API, heavily inspired by Greg Young's Event Store.


## Features

+ ACID stream operations
+ Optimistic concurrency and idempotency support
+ Custom stream and event properties
+ Arbitrary entity includes within a batch (for synchronous snapshots and projections)
+ Virtual partitions (for multi-tenant apps and global event ordering) [PLANNED]

## Design
Streamstone is just a thin layer (library, not a server) on top of Windows Azure Table Storage. It implements low-level mechanics for dealing with event streams, and all heavy-weight lifting is done by underlying store. 

The api is stateless and all exposed objects are immutable, once fully constructed. 

## Schema

<a href="https://raw.githubusercontent.com/yevhen-personal/test/master/Schema.png" target="_blank" title="Click to view full size"><img src="https://raw.githubusercontent.com/yevhen-personal/test/master/Schema.png" alt="Schema" tyle="max-width:100%;"/></a>

---

<a href="https://raw.githubusercontent.com/yevhen-personal/test/master/Schema2.png" target="_blank" title="Click to view full size"><img src="https://raw.githubusercontent.com/yevhen-personal/test/master/Schema2.png" alt="Schema for virtual partitions" tyle="max-width:100%;"/></a>

## Usage
TODO

## Limitations

Same as for underlying Windows Azure Table Storage:
+ Maximum size of batch is 4MB
+ Maximum size of event is 1 MB
+ Maximum size of payload and metadata properties is 64Kb 
+ Maximum length of property name is 255 chars
+ An event can have up to 255 custom properties

> 
+ [WATS limitations on MSDN](http://msdn.microsoft.com/en-us/library/azure/dd179338.aspx)
+ [Entity size calculation](http://blogs.msdn.com/b/avkashchauhan/archive/2011/11/30/how-the-size-of-an-entity-is-caclulated-in-windows-azure-table-storage.aspx)
