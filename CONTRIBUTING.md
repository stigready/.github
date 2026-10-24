# Contributing

Thank you for wanting to help.

## Role repos: open an issue, not a pull request

The StigForge role repos are published from StigForge, which is private. The STIG and CIS roles are generated from ComplianceAsCode content; stigready-baseline is hand-written. Each release replaces the contents of the role repo. A pull request to a role repo cannot be merged there, because the next release would overwrite it.

So please open an issue in the role's repo instead. Use the **Role bug** form for a bug. Describe the change you want and why, and paste a patch in the issue if you have one. If we take it, the change is made in StigForge and ships in a later role tag.

If the problem is in a task that comes from ComplianceAsCode, it may be best fixed upstream in [ComplianceAsCode/content](https://github.com/ComplianceAsCode/content). A role gets an upstream fix only when a later role release picks it up.

## Other repos

Open an issue before you start a pull request, so we can agree the change first.

## Security problems

Do not open an issue or a pull request. Follow the [security policy](https://github.com/stigready/.github/blob/main/SECURITY.md).
