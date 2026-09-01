# Railway Multi-Site Test Service

One Railway Caddy service returns different responses based on the requested hostname.

## Hostnames

- `site1.rana.dpdns.org` → `Site 1`
- `site2.rana.dpdns.org` → `Site 2`
- `site3.rana.dpdns.org` → `Site 3`

All three can resolve through the existing wildcard:

`*.rana.dpdns.org -> Railway`

## Railway setup

1. Connect this repo to one Railway service.
2. Railway should detect the root `Dockerfile`.
3. Set the public networking target port to `8080`.
4. Keep your wildcard custom domain `*.rana.dpdns.org` on this service.
5. Redeploy.

## Test

```bash
curl -vk https://site1.rana.dpdns.org/
curl -vk https://site2.rana.dpdns.org/
curl -vk https://site3.rana.dpdns.org/
```

Expected responses:

```text
Site 1
Site 2
Site 3
```

Note: this provides three logical hostnames/upstreams through one Railway service. It does not guarantee three different public IP addresses.
