# Security policy

This policy covers StigReady images on AWS Marketplace, their Marketplace listings, the StigForge Ansible role repos under [github.com/stigready](https://github.com/stigready), and [stigready.com](https://stigready.com).

## Report a vulnerability

Email [support@stigready.com](mailto:support@stigready.com). Put "Security" in the subject.

Do not open a public issue, pull request or discussion for a security problem.

Or use GitHub private vulnerability reporting: in any stigready repo, open the **Security** tab and choose **Report a vulnerability**. It is on for every public stigready repo.

We have no PGP key. Do not send passwords, private keys, tokens or customer data by email. Describe the problem, and we will agree with you how to share anything sensitive.

## What to include

- **What it affects:**
  - An image: the Marketplace product name, the version, the AMI ID and region, and the architecture.
  - A role: the repo name and the tag you used.
  - The site: the page URL.
  - A listing: the product name and the text or setting at fault.
- What the problem is, and what an attacker could do with it.
- How to reproduce it: the steps, commands or playbook, and the OS and version of the host.
- For a vulnerable package: the package name and version, and the CVE ID if there is one.
- Whether you plan to publish, and when.

## What we do

1. We reply to say we have your report.
2. We check it and tell you whether we accept it.
3. We fix it at the source, not on a running host:
   - **A role:** the role repos are published from StigForge, which is private. The fix is made there and ships as a new role tag. An image gets the fix only when it is rebuilt with the new tag.
   - **An image:** the fix ships in the next build of the image, as a new Marketplace version.
   - **The site or a listing:** we correct the page or the listing copy.
4. We tell you when the fix is released.

Please keep the problem private until the fix is released, or until we agree a date with you. If we have not agreed a date, you may publish 90 days after your report.

We do not promise a response or fix time. We have no bug bounty and do not pay for reports.

If the problem is in an OS package or in ComplianceAsCode content rather than in our build or our tasks, please report it to that project as well. Our images and roles get an upstream fix only when a new build or a new role tag picks it up.

## Supported versions

| What | Supported |
|---|---|
| A role | The latest release tag of that role repo. Older tags get no fixes. Pin a tag, never `main`. |
| An image | The current Marketplace version of that image. Older versions get no fixes. A fix ships as a new version, and a running instance keeps the version it was launched from. |
| stigready.com | The live site. |

## Known gaps

- RHEL 10 images have no CVE scan yet. Use your own scanner on them.
- The known risks of the current roles are listed on the [StigReady organization page](https://github.com/stigready). You do not need to report those, but new detail is welcome.
- Role release tags are not signed or protected yet. Pin a tag and review the diff before you upgrade.

## Testing

Test only on hosts and AWS accounts you own. Do not run load or denial-of-service tests against stigready.com.
