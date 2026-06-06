# SABnzbd

SABnzbd is deployed through the `overlays` Kustomize overlay.

## Network

The production overlay exposes SABnzbd through MetalLB:

```text
http://192.168.50.211:8080
```

## Storage

The base creates a `sabnzbd-config` PVC using the `ceph-rbd` StorageClass.
