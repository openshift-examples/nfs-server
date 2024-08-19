# NFS-exporter container with a file

This is a copy of <https://github.com/kubernetes/examples/tree/master/staging/volumes/nfs/nfs-data>

This container exports /exports with index.html in it via NFS. Based on
../exports. Since some Linux kernels have issues running NFSv4 daemons in containers,
only NFSv3 is opened in this container.

Available as `quay.io/openshift-examples/nfs-server`

## Local container image build 


```bash
export IMAGE='quay.io/openshift-examples/nfs-server:latest'
podman build --platform linux/amd64,linux/arm64  --manifest ${IMAGE}  .
podman manifest inspect ${IMAGE}
podman manifest push ${IMAGE}
skopeo inspect --raw docker://${IMAGE} | jq
```


