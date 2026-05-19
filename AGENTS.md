# Guidance for coding agents

This repo is the Amber Network pfSense fork workspace mounted at `/mnt/pfsense`.

## Boundary

- Treat pfSense as its own firewall/router perimeter authority, not as a Guardian-owned adapter and not as an AdGuardHome child.
- The workspace is mounted from `pfsense.amber.com:/opt/pfsense`.
- At onboarding, `pfsense.amber.com` resolved to `192.168.0.5` and the host presented as an Ubuntu VM staging surface over SSH. Do not assume a live pfSense/FreeBSD firewall runtime is active until you verify it.
- The fork remote is `origin=https://github.com/ithorn500/pfsense.git`; keep `upstream=https://github.com/pfsense/pfsense.git` for upstream comparison.

## Guardrails

- No default gateway, DHCP, DNS listener, VLAN, NAT, WAN, VPN, packet-filter rule, port-forward, interface assignment, or production firewall cutover change without an explicit maintenance plan and operator approval.
- First Amber integration should be read-only inventory/status/telemetry only.
- Guardian may express policy intent and approval UX through Amber Bus, but pfSense remains the packet-enforcement authority.
- Logger should receive high-signal firewall/perimeter events, not raw packet floods.
- Prefer narrow fork changes with clear upstream boundaries. Avoid broad formatting or vendored-source churn.

## First Safe Slice

- Read-only host and repo inventory.
- Amber Bus manifest and connector contract draft.
- Read-only functions such as firewall status, interface summary, gateway status, DHCP lease listing where assigned, VPN status, rule inventory, and recent high-signal events.
- No runtime behavior change.
