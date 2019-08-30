## CephFS and RBD volume provisioners for Kubernetes

This fork was needed because no current container images were available anymore as there haven't been any releases
since August 2018. It is current with upstream `master` as of 08/08/2019 and contains one further fix to allow the RBD
provisioner to compile again. It also supports all Ceph RBD image features and not only `layering` in the storage
class specification.

Container images are automatically made available on Docker Hub:

* [elementalnet/cephfs-provisioner](https://cloud.docker.com/u/elementalnet/repository/docker/elementalnet/cephfs-provisioner)
* [rbd-provisioner](https://cloud.docker.com/u/elementalnet/repository/docker/elementalnet/rbd-provisioner)
