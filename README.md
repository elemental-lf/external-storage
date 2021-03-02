## CephFS and RBD volume provisioners for Kubernetes

This fork of https://github.com/kubernetes-retired/external-storage was needed because no current container images were 
available anymore as there haven't been any releases since August 2018 and since then the whole project has been retired.

The fork is current with upstream `master` as of 08/08/2019. In March 2021 I merged the `openstorage-5.5` branch of 
the "Open Storage for Linux Containers by Portwkorx" fork of this project (found at 
https://github.com/libopenstorage/external-storage/tree/openstorage-5.5, commit 697cbc8) to vendor in new Kubernetes
client libraries which also required some small changes to the code of the provisioners. These changes allowed the
provisioners to work with Kubernetes 1.20.

Here is a summary of the Ceph related changes that were made in addition to the work documented above:

* Support for more RBD image features apart from `layering` (NB: Your RBD client needs to support them too!)
* Ignore already deleted images and allow K8s resource deletion to proceed
* Purge any (unprotected) snapshots before deleting the image allowing the image deletion to succeed
* Add support for erasure pools in Ceph RBD provisioner (authored by @sagor999, cherry-picked from upstream commit
  8a3a9e81)

The last change is probably the one with the most impact, and you should consider if this is the right behaviour
for your use case.

Container images are automatically made available on Docker Hub:

* [elementalnet/cephfs-provisioner](https://cloud.docker.com/u/elementalnet/repository/docker/elementalnet/cephfs-provisioner)
* [rbd-provisioner](https://cloud.docker.com/u/elementalnet/repository/docker/elementalnet/rbd-provisioner)
