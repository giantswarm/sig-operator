How to 
------
During development of [`app-operator`](https://github.com/giantswarm/app-operator/pull/3), 
we agreed that we should not setup `health` service but only endpoint needed since we don't
want to use Kubernetes health check inside operator to prevent cascading failures. 
Discussion: https://github.com/giantswarm/app-operator/pull/3#discussion_r241714624
