# StigReady

Hardened Linux AMIs on AWS Marketplace, and the open Ansible roles behind them.

[stigready.com](https://stigready.com) · [AWS Marketplace seller page](https://aws.amazon.com/marketplace/seller-profile?id=seller-h3qxnolnrqakk) · [contact@stigready.com](mailto:contact@stigready.com)

## Images on AWS Marketplace

- **[StigReady Base](https://stigready.com/#base-tier)** (24 listings): the STIG disk layout (separate `/home`, `/tmp`, `/var`, `/var/log`, `/var/log/audit` and `/var/tmp` on the images built from the OS installer; Amazon Linux 2023 is built from Amazon's prebuilt image and gets a separate `/var/log/audit`, the one partition its STIG requires), key-only SSH, IMDSv2 required and the SSM Agent installed. No benchmark profile is applied; bring your own. Rocky Linux, AlmaLinux and RHEL 8, 9 and 10; Ubuntu 24.04 and 26.04; Amazon Linux 2023. $0.02/hr or $149/yr per instance.
- **[StigReady Applied](https://stigready.com/applied/)** (56 listings): Base plus DISA STIG (FIPS mode) or CIS Benchmark Level 1 / Level 2 remediation, on Rocky Linux, AlmaLinux and RHEL 8 to 10, and Ubuntu 24.04. Not every profile exists for every OS. $0.08/hr or $649/yr per instance.

Both tiers come in x86_64 and arm64 (Graviton). The fee is per instance, on top of EC2. RHEL images are BYOL: you supply the Red Hat subscription. No Ubuntu Pro subscription is included. Ongoing ESM and FIPS updates require your own Ubuntu Pro subscription.

**How Applied is scored.** OpenSCAP scores each image during its build against the unmodified ComplianceAsCode (SSG) profile. A build that scores below 90% does not ship. Rules that do not apply to a cloud AMI are listed in a POA&M. STIG images run in FIPS mode using the OS vendor's FIPS cryptographic modules.

**Evidence is on request.** For an Applied image, email [support@stigready.com](mailto:support@stigready.com) for its OpenSCAP ARF result, HTML report, POA&M, SBOM and CVE scan. RHEL 10 images have no CVE scan yet. Evidence is not published on the web.

A score measures an image against a profile. It is not a certification, an authorization (ATO) or proof of compliance with any framework.

## StigForge: the Ansible roles

Public role repos, generated from ComplianceAsCode (SSG 0.1.82) remediation content. Some add StigForge-written tasks under `tasks/supplement/`. No OpenSCAP results ship with a role: scan your own host after you apply it. Pin the latest release tag shown in each repo, never `main`, and review the diff before you upgrade; tags are not yet signed or protected. Test on a non-production host and take a snapshot first, because the roles have no rollback.

Known risks in the current roles, not yet described in their READMEs: the ubuntu24-stig firewall can block SSH, depending on which rules are turned on; stigready-baseline and the RHEL-family STIG roles can rewrite `/etc/fstab` entries to device names, which can stop a host booting; a failed task, including FIPS enablement, can still let the play report success; some roles, rhel9-stig among them, set auditd to halt the host when its log disk fills; and the RHEL-family STIG roles lock root after failed logins with no automatic unlock.

Versions below are the publisher versions as SSG 0.1.82 renders them. CIS may have published newer benchmarks; these roles follow SSG.

| OS | STIG content | CIS content | Built into a released image? |
|---|---|---|---|
| RHEL 9 | [rhel9-stig](https://github.com/stigready/rhel9-stig): DISA STIG V2R9 | [rhel9-cis](https://github.com/stigready/rhel9-cis): CIS RHEL 9 v2.0.0 | Yes, from an earlier role release |
| RHEL 8 | [rhel8-stig](https://github.com/stigready/rhel8-stig): DISA STIG V2R8 | [rhel8-cis](https://github.com/stigready/rhel8-cis): CIS RHEL 8 v4.0.0 | Yes, from an earlier role release |
| RHEL 10 | [rhel10-stig](https://github.com/stigready/rhel10-stig): DISA STIG V1R2 | [rhel10-cis](https://github.com/stigready/rhel10-cis): CIS RHEL 10 v1.0.1 | Yes, from an earlier role release |
| Ubuntu 24.04 | [ubuntu24-stig](https://github.com/stigready/ubuntu24-stig): DISA STIG V1R5 | [ubuntu24-cis](https://github.com/stigready/ubuntu24-cis): CIS Ubuntu 24.04 v1.0.0 | Yes, from an earlier role release |
| Ubuntu 22.04 | [ubuntu22-stig](https://github.com/stigready/ubuntu22-stig): DISA STIG V2R7 | [ubuntu22-cis](https://github.com/stigready/ubuntu22-cis): CIS Ubuntu 22.04 v2.0.0 | Not yet |
| Oracle Linux 9 | [ol9-stig](https://github.com/stigready/ol9-stig): DISA STIG V1R6 | none | Not yet |
| Oracle Linux 10 | [ol10-stig](https://github.com/stigready/ol10-stig): SSG's DRAFT profile, not based on a DISA STIG | none | Not yet |
| CentOS Stream 9 | [cs9-stig](https://github.com/stigready/cs9-stig): RHEL 9 STIG V2R9 | [cs9-cis](https://github.com/stigready/cs9-cis): CIS RHEL 9 v2.0.0 | Not yet |
| CentOS Stream 10 | [cs10-stig](https://github.com/stigready/cs10-stig): RHEL 10 STIG V1R2 | [cs10-cis](https://github.com/stigready/cs10-cis): CIS RHEL 10 v1.0.1 | Not yet |
| Amazon Linux 2023 | none | [al2023-cis](https://github.com/stigready/al2023-cis): CIS Amazon Linux 2023 v1.0.0 | Not yet |
| Debian 12 | none | [debian12-cis](https://github.com/stigready/debian12-cis): CIS Debian 12 v1.1.0 | Not yet |

DISA and CIS publish no STIG or benchmark for CentOS Stream; those roles apply the RHEL content. [stigready-baseline](https://github.com/stigready/stigready-baseline) is a small hand-written role (sshd, kernel sysctls, mount options). It is not a STIG or CIS profile and not SSG content.

**stigvalidated (coming soon):** a second check of each hardened image with CINC Auditor profiles, compared rule by rule with the OpenSCAP result. The comparison will be published per role.

## Where to start

- Buying an image: [stigready.com](https://stigready.com) for the catalog and pricing, then the [seller page](https://aws.amazon.com/marketplace/seller-profile?id=seller-h3qxnolnrqakk).
- Hardening your own hosts: pick a role repo above, read the known risks above and its README, and try it on a test host first.
- Source of the website: [stigready-web](https://github.com/stigready/stigready-web).

## Report a problem

- An image, a listing or evidence: [support@stigready.com](mailto:support@stigready.com).
- A role: open an issue in that role's repo.
- A security problem: these repos have no private vulnerability reporting yet. Email [support@stigready.com](mailto:support@stigready.com) instead of opening a public issue.

## Notices

Not affiliated with or endorsed by DISA, DoD, NIST, CIS, Red Hat, Canonical, Oracle, Amazon, Debian, the Rocky Enterprise Software Foundation, the AlmaLinux OS Foundation, or the ComplianceAsCode project. Task bodies in the SSG-generated roles come from [ComplianceAsCode/content](https://github.com/ComplianceAsCode/content) (BSD-3-Clause, Copyright (c) 2012-2017, Red Hat, Inc.). CIS® and CIS Benchmarks™ are trademarks of the Center for Internet Security, Inc. Red Hat®, Red Hat Enterprise Linux® and CentOS are trademarks of Red Hat, Inc. Rocky Linux is a trademark of the Rocky Enterprise Software Foundation. AlmaLinux is a trademark of the AlmaLinux OS Foundation. Ubuntu® is a trademark of Canonical Ltd. Oracle Linux is a trademark of Oracle. Amazon Linux is a trademark of Amazon.com, Inc. Debian is a trademark of Software in the Public Interest, Inc. All trademarks are the property of their respective owners. StigReady does not provide commercial licenses for Red Hat products.
