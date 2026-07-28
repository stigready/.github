# StigReady

STIG- and CIS-ready cloud images, built and scored with OpenSCAP — so compliance is met in the AMI, not bolted on after launch.

**Site:** [stigready.com](https://stigready.com)

## What we build

- **Golden images** — Ubuntu, RHEL, Rocky, Alma (x86_64 + aarch64) as base, CIS Level 1/2, and STIG (FIPS where the profile requires it)
- **StigForge** — CIS/STIG Ansible roles from published DISA STIGs, verified against ComplianceAsCode/SSG
- **Evidence** — OpenSCAP reports, SBOMs, and delivery manifests with every scored image

## Public

| Repo | What |
|------|------|
| [stigready-web](https://github.com/stigready/stigready-web) | Marketing site source for [stigready.com](https://stigready.com) |

Image factory and StigForge sources are private.
