# Traefik

| Label | Value | Comment |
|--|--|--|
| Application Name * | `traefik` | name is important for DNS link |
| Entrypoints Port HTTP | `80` |  |
| Entrypoints Port HTTPS | `443` |  |
| **Configure forwardAuth** |||
| Name * | `authelia` | name of middleware |
| Address * | `http://authelia.ix-authelia.svc.cluster.local:9091/api/verify?rd=https://sso.mydomain.com/` | Please adjust the domain name |
| **Configure authResponseHeaders** |||
| Remote-User |  |  |
| Remote-Groups |  |  |
| Remote-Name |  |  |
| Remote-Email |  |  |
