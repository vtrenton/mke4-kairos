# MKE4 + Kairos

## How to use
 - Pull a generic kairos image such as https://github.com/kairos-io/kairos/releases/download/v3.5.3/kairos-rocky-9.6-core-amd64-generic-v3.5.3.iso
 - boot system from iso
 - 8080 will be exposed on the host browse to it
 - paste in kairos.yaml
**make sure to include the #cloud-config comment header - it is required**
 - once all nodes have kairos installed - update mke4.yaml with the proper ssh config
 - mkectl apply -f mke4.yaml
 - ???
 - profit

## Complete hands off provisioning
Kairos images are built via a docker build image. We can inject the cloud config into the base image directly via a flag

We can get Rocky base images here: https://quay.io/repository/kairos/rockylinux?tab=tags&tag=latest
```bash
docker run --rm -v $PWD:/mnt quay.io/kairos/kairos-agent:latest \
  build-iso \
  --image quay.io/kairos/core-rockylinux:latest \
  --cloud-config /mnt/cloud-config.yaml \
  --output /mnt/my-kairos-auto.iso
```

### What about other formats
qcow2 (kvm):
```bash
docker run --rm -v $PWD:/mnt quay.io/kairos/kairos-agent:latest \
  build-image \
  --image quay.io/kairos/core-rockylinux:latest \
  --cloud-config /mnt/cloud-config.yaml \
  --output /mnt/my-kairos-auto.qcow2 \
  --format qcow2
```

raw:
```bash
docker run --rm -v $PWD:/mnt quay.io/kairos/kairos-agent:latest \
  build-image \
  --image quay.io/kairos/core-rockylinux:latest \
  --cloud-config /mnt/cloud-config.yaml \
  --output /mnt/my-kairos-auto.raw \
  --format raw
```

## integration with k0rdent/MKE4

### Check out:
- https://github.com/kairos-io/cluster-api-provider-kairos
- https://github.com/kairos-io/osbuilder
- https://github.com/kairos-io/kairos-operator
