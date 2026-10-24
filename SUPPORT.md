# Getting help

| You need help with | Where to go |
|---|---|
| A StigReady image, a Marketplace listing, or evidence for an Applied image | Email [support@stigready.com](mailto:support@stigready.com) with the product name, version, AMI ID and region |
| A StigForge role | Open an issue in that role's repo. Say which tag you used and the OS and version of the host |
| A security problem | Do not open an issue. Follow the [security policy](https://github.com/stigready/.github/blob/main/SECURITY.md) |
| Buying an image | [stigready.com](https://stigready.com) for the catalog and pricing, or [contact@stigready.com](mailto:contact@stigready.com) |

Evidence for an Applied image (OpenSCAP ARF result, HTML report, POA&M, SBOM and CVE scan) is sent on request from support@stigready.com. It is not published on the web. RHEL 10 images have no CVE scan yet.

Before you open a role issue, read the known risks on the [StigReady organization page](https://github.com/stigready) and the role's README. Pin a release tag, never `main`.

## What we do not support

- **Red Hat subscriptions.** RHEL images are BYOL: you supply the Red Hat subscription. StigReady does not provide commercial licenses for Red Hat products. For RHEL itself, go to Red Hat.
- **Ubuntu Pro.** No Ubuntu Pro subscription is included. Ongoing ESM and FIPS updates require your own Ubuntu Pro subscription.
- **Compliance sign-off.** A score measures an image against a profile. It is not a certification, an authorization (ATO) or proof of compliance with any framework. We cannot assess or authorize your system.
- **Your AWS account, EC2 or your network.** Go to AWS Support for those.
- **Changes you make after launch**, and roles applied from `main` or from a tag that is not the latest.
- **Windows.** We make no Windows images or roles.

We do not promise a response time.

Not affiliated with or endorsed by DISA, DoD, NIST, CIS, Red Hat, Canonical, Oracle, Amazon, Debian, the Rocky Enterprise Software Foundation, the AlmaLinux OS Foundation, or the ComplianceAsCode project. Trademark notices are on the [StigReady organization page](https://github.com/stigready).
