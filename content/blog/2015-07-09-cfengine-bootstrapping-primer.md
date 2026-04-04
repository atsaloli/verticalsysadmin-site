---
title: "CFEngine Bootstrapping Primer"
date: 2015-07-09
author: "Aleksey Tsalolikhin"
---

## Key Definitions

- **Managed server:** A server controlled by CFEngine within a fleet
- **Policy server:** Distributes configuration policy centrally to managed servers
- **Hub:** Commercial CFEngine component collecting reports via Web UI
- **Bootstrapping:** Establishes secure connections enabling policy downloads and report collection

Bootstrap command: `cf-agent -B 1.2.3.4` — accepts the policy server's cryptographic key.

## Architecture

Pull-based — managed nodes pull policy from servers; hubs pull reports from managed nodes. cf-serverd handles inter-node communication on TCP port 5308.

## Troubleshooting

Common failures involve cf-serverd not running or network connectivity to port 5308.
