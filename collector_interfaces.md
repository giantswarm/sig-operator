# Collector Interfaces

In our operators we tend implement collectors for metrics collection. The
following suggestions provide an idea on how this could look like.

### File Structure

There is usually a `service` directory that implements the controllers and
collectors. Here we are interested in the `collector` directory, where
collectors are implemented. In this directory there is a `set.go` which
implements the collector interface as documented in
https://godoc.org/github.com/giantswarm/exporterkit/collector. The purpose of
the collector set is to manage multiple collectors more easily in order to
guarantee a separation of concerns. The file structure of an operator might look
like the following example.

```
.
└── service
    └── collector
        ├── error.go
        ├── resource_group.go
        ├── set.go
        └── vpn_connection.go
```

### Generated Listers

The Kubernetes client libraries are usually generated and provide lister and
watcher interfaces. In the past we used the watcher interfaces for legacy
reasons which resulted in issues because of duplicated metrics being collected.
Instead we should simply use the lister interfaces, which also provide paging
support.

```
List(opts v1.ListOptions) (*v1alpha1.AzureConfigList, error)
Watch(opts v1.ListOptions) (watch.Interface, error)
```
