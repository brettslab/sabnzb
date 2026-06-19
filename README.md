# SABnzbd

SABnzbd is deployed through the `overlays` Kustomize overlay.

## Network

The production overlay exposes SABnzbd through MetalLB:

```text
http://192.168.50.211/
```

## Storage

The base creates a `sabnzbd-config` PVC using the `ceph-rbd` StorageClass.

## News Server Secret

News server credentials are synced from Vault into the Kubernetes Secret
`sabnzbd-news-server` in the `media` namespace.

Vault path:

```text
kv/media/sabnzbd/news-server
```

## VPN Sidecar

SABnzbd runs with a Gluetun sidecar in the same pod so outbound traffic uses the
Windscribe WireGuard tunnel. The sidecar reads credentials from Vault path:

```text
kv/vpn/gluetun/windscribe
```
