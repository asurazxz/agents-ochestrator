# Hosting and access guide

Reviewed: 2026-10-06 (Asia/Singapore). Design guidance only; no application or networking is deployed.

## Who runs what

One operator deploys the shared application and database. Teammates open the dashboard, join a project, and configure their agents to reach the service. They do not each clone this product's source or run its backend. They still keep working copies of the software project they are developing.

Agent setup may need a small local MCP bridge depending on the chosen transport and client authentication. Remote orchestration additionally needs an opt-in device connector. Neither requires hosting a separate context database on each laptop.

## Initial private-network test

Use the existing Twingate network with a laptop, desktop, and shared server. The application's address and port must be permitted by the private-network setup. Validate browser and agent access independently. No public hostname, router port forwarding, or new Cloudflare configuration is needed for this test.

Private connectivity does not replace project authorization. If the server is offline, shared operations pause; cached-context behavior is a proposed future capability.

## Suggested deployment layout

Docker Compose would run the application service and PostgreSQL with persistent storage. The service initially serves the built dashboard and API. Database access stays within the deployment network. An optional Caddy proxy or tunnel provides HTTPS/public routing. Versioned images and backup/restore instructions must be supplied when implementation exists.

Compose supports [single-server production deployments](https://docs.docker.com/compose/how-tos/production/). Caddy documents [automatic HTTPS](https://caddyserver.com/docs/automatic-https). These sources describe available building blocks, not an implemented setup here.

## Access choices

| Approach | Router/public access | Teammate requirements |
| --- | --- | --- |
| Existing private access, initially Twingate | No new public exposure for the test | Existing authorized private-network access |
| Named Cloudflare Tunnel | Outbound server connection; no public origin IP or inbound router forwarding required | Normal HTTPS URL and application authentication |
| Cloudflare Quick Tunnel | Temporary public URL through an outbound connection | Normal browser access; streaming/client restrictions apply |
| Direct public reverse proxy | Reachable public server; home NAT generally needs inbound forwarding | Domain/HTTPS access and application authentication |

Users need a reachable service, not necessarily the home server's public IP. A public tunnel connector runs on the host; ordinary HTTP/HTTPS users do not need their own tunnel software. Future worker connectors should initiate outbound connections to the service so teammates do not need to expose their laptops.

## Cloudflare cost and limitations

[Cloudflare Tunnel](https://developers.cloudflare.com/tunnel/) is available on all plans, including Free, and connects out from the host. A named tunnel's published hostname requires a [domain on Cloudflare](https://developers.cloudflare.com/tunnel/get-started/); registration or renewal is separate. Cloudflare is optional and must not be built into core product identity or storage.

[Quick Tunnels](https://developers.cloudflare.com/tunnel/get-started/quick-tunnels/) require no account or domain but are intended for testing. They have changing hostnames, no uptime guarantee, a 200 in-flight-request limit, and no Server-Sent Events support. Email gating requires a browser and does not support noninteractive clients. Do not use a Quick Tunnel as the baseline for streaming MCP compatibility.

For public agent access, test the actual MCP transport, reconnection, and authentication through the selected route. Interactive browser access gates do not automatically authenticate agent requests. Application login and project permissions are required even when a tunnel is present.

Free software and free tunnel access do not eliminate hardware, electricity, bandwidth, domain, backup-storage, or optional inference costs. Advanced provider services and their pricing are separate; recheck terms before deployment. This product's ordinary context traffic should stay small; bulk media delivery is outside its scope.

## Availability and growth

The private test has no high-availability target. A single server is a useful starting point, not a production availability guarantee. Add monitoring, backups, and verified restores before a public release. Scale based on measured workload using the [technology guidance](TECH_STACK.md).
