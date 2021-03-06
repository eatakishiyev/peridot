# Ledger

[TOC]

## What is Ledger?

Ledger is a distributed storage system for Fuchsia.

Each application (or more precisely, each [component]) running on behalf of a
particular user has a separate data store provided and managed by Ledger, and
vended to a client application by Fuchsia framework through its [component
context].

The data store for the particular component/user combination is private - not
accessible to other apps of the same user, and not accessible to other users of
the same app.

Each data store is transparently **synchronized** across devices of its user
through a [cloud provider]. Any data operations are made **offline-first** with
no coordination with the cloud. If concurrent modifications result in a data
conflict, the conflict is resolved using an app-configurable merge policy.

Each data store is organized into collections exposing a **key-value store** API
called *pages*. Page API supports storing data of arbitrary size, atomic changes
across multiple keys, snapshots and modification observers.

## Documentation

Documentation for using Ledger:

 - [User Guide](user_guide.md)

Documentation for integrating with Ledger in client apps:

 - [API Guide](api_guide.md)
 - [Data Organization](data_organization.md)
 - [Examples](examples.md)

Documentation for setting up a remote Cloud sync provider:

 - [Firebase](firebase.md)

Documentation for developing Ledger:

 - [Developer Workflow](workflow.md)
 - [Field Data](field_data.md)
 - [Style Guide](style_guide.md)
 - [Testing](testing.md)

Design documentation:

 - [Architecture](architecture.md)
 - [Conflict Resolution](conflict_resolution.md)
 - [Life of a Put](life_of_a_put.md)


[cloud provider]: https://fuchsia.googlesource.com/peridot/+/master/public/lib/cloud_provider/fidl/cloud_provider.fidl
[component]: https://fuchsia.googlesource.com/peridot/+/master/public/lib/component/fidl
[component context]: https://fuchsia.googlesource.com/peridot/+/master/public/lib/component/fidl/component_context.fidl
