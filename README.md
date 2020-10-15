# FlexRAN manifests

This project contains a set of manifests that will configure an OpenShift platform to run RAN workloads on it.

## Getting Started

First thing will be to apply the extra operators that are missing. This needs to be done at first stage,
because they take some time to be applied. This can be done with:

```
oc apply -k additional_components
```
 
The manifests are created with 2 layers, base and site, so people can create independent sites for their own settings.
Manifests can be applied on a running cluster, by simple running:

```
oc apply -k cluster_configuration/path/to/site/
```

for example you can run:

```
oc apply -k sample_site/


namespace/cluster-configuration created
namespace/flexran-workloads created
namespace/multus-networks created
namespace/openshift-nfd created
namespace/openshift-performance-addon created
channel.apps.open-cluster-management.io/acm-gitops-github created
placementrule.apps.open-cluster-management.io/cluster-configuration-rule created
placementrule.apps.open-cluster-management.io/cvo-rule created
placementrule.apps.open-cluster-management.io/placement-upgrade-cluster created
placementrule.apps.open-cluster-management.io/apply-multus-to-ready-clusters created
placementrule.apps.open-cluster-management.io/apply-nfd-to-ready-clusters created
placementrule.apps.open-cluster-management.io/apply-performance-to-ready-clusters created
subscription.apps.open-cluster-management.io/flexran-multus-networks created
subscription.apps.open-cluster-management.io/flexran-nfd created
subscription.apps.open-cluster-management.io/flexran-performance created
placementbinding.policy.open-cluster-management.io/cluster-configuration-policy created
placementbinding.policy.open-cluster-management.io/cvo-policy created
placementbinding.policy.open-cluster-management.io/binding-upgrade-cluster created
policy.policy.open-cluster-management.io/upgrade-cluster created

```

### Prerequisites

Have a running OpenShift >=4.4 cluster installed and running, export KUBECONFIG to access it.
These manifests have been tested using a 3-node footprint (3 masters/workers combined).
```
