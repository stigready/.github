# StigReady

Hardened AWS AMIs with published OpenSCAP scores — and public Ansible roles when you want to remediate yourself.

**Site:** [stigready.com](https://stigready.com) · **X:** [@Stigready](https://x.com/Stigready) · **Contact:** [contact@stigready.com](mailto:contact@stigready.com)

## Products

- **[StigReady Base](https://stigready.com/#base-tier)** — STIG disk layout + cloud hardening on AWS Marketplace. Bring your own CIS/STIG profiles or roles.
- **[StigReady Applied](https://stigready.com/applied/)** — CIS L1/L2 or DISA STIG remediated AMIs with published scores and evidence.
- **[StigForge](https://stigready.com/#stigforge)** — public Ansible role exports (`stigready/*-cis`, `*-stig`), OpenSCAP-verified against ComplianceAsCode/SSG.

RHEL images are **BYOL** — we do not sell Red Hat licenses.

## Public repositories

| Repo | What |
|------|------|
| [stigready-web](https://github.com/stigready/stigready-web) | Source for [stigready.com](https://stigready.com) |
| [rhel9-stig](https://github.com/stigready/rhel9-stig) · [rhel9-cis](https://github.com/stigready/rhel9-cis) | RHEL 9 STIG / CIS roles |
| [rhel8-stig](https://github.com/stigready/rhel8-stig) · [rhel8-cis](https://github.com/stigready/rhel8-cis) | RHEL 8 STIG / CIS roles |
| [rhel10-stig](https://github.com/stigready/rhel10-stig) · [rhel10-cis](https://github.com/stigready/rhel10-cis) | RHEL 10 STIG / CIS roles |
| [ubuntu24-stig](https://github.com/stigready/ubuntu24-stig) · [ubuntu24-cis](https://github.com/stigready/ubuntu24-cis) | Ubuntu 24.04 STIG / CIS roles |
| [ubuntu22-stig](https://github.com/stigready/ubuntu22-stig) · [ubuntu22-cis](https://github.com/stigready/ubuntu22-cis) | Ubuntu 22.04 STIG / CIS roles |
| [al2023-cis](https://github.com/stigready/al2023-cis) | Amazon Linux 2023 CIS role |
| [ol9-stig](https://github.com/stigready/ol9-stig) | Oracle Linux 9 STIG role |
| [debian12-cis](https://github.com/stigready/debian12-cis) | Debian 12 CIS role |

Pin a release tag when you install — do not track `main`.

How-tos: [stigready.com/blog](https://stigready.com/blog/)

The AMI factory and StigForge monorepo stay private. Public role repos are the supported install path.
