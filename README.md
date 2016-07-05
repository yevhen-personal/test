![Logo](image__for_github.jpg)

Streamstone is a small library targeted at building scalable event-sourced applications on top of Azure Table Storage. It has simple, functional style API, heavily inspired by Greg Young's Event Store.

## Features

+ ACID stream operations
+ Optimistic concurrency and idempotency support
+ Custom stream and event properties
+ Arbitrary entity includes within a batch (for synchronous snapshots and projections)
+ Virtual partitions (for multi-tenant apps and global event ordering) [PLANNED]

## Installing from NuGet [![NuGet](https://img.shields.io/nuget/v/Streamstone.svg?style=flat)](https://www.nuget.org/packages/Streamstone/)

To install Streamstone via NuGet, run this command in NuGet package manager console:

    PM> Install-Package Streamstone

## Building from source [![Build status](https://ci.appveyor.com/api/projects/status/3rsmwblor11b6inq/branch/master?svg=true)](https://ci.appveyor.com/project/yevhen/streamstone/branch/master)

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

+ The maximum batch size is 99 entities (100 entities WATS batch size limit - 1 stream header entity) 
+ With idempotency enabled, the maximum batch size is 49 events (100/2 - 1 stream header entity) 
+ The maximum slice size when reading events is 1000 (WATS limitation)

Plus, all of the limitations of the underlying Azure Table Storage API:

+ Maximum size of batch is 4MB
+ Maximum size of entity is 1 MB
+ Maximum size of property is 64Kb 
+ Maximum length of property name is 255 chars
+ An entity can have up to 255 custom properties

>  [WATS limitations on MSDN](http://msdn.microsoft.com/en-us/library/azure/dd179338.aspx) 

## Community

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/yevhen/Streamstone?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## License

Apache 2 License
