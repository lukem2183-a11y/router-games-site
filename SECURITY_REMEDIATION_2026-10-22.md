# Security hardening — October 22, 2026

This change adds read-only security CI on pushes, pull requests, manual runs and a weekly schedule. Checkout is pinned to a reviewed full commit SHA, fetches available history and does not persist credentials. The workflow downloads Gitleaks v8.30.1 from its official release, verifies its published SHA-256 checksums and scans Git history with redacted output. No secret allowlist is needed in this repository.

Dependabot checks GitHub Actions weekly. This static repository has no npm manifest or lockfile, so no artificial npm audit/install job is added. GitHub Dependabot alerts have been enabled separately. No site content, hosting, deployment or access permissions are changed.

The baseline history scan found no verified privileged secrets. A clean scan is not a guarantee covering deleted/unreachable commits, Git LFS objects, release attachments, workflow artifacts, hosting credentials or runtime security. Scanners do not prove that live hosting headers or server configuration are secure. Review proposed action updates before merging.

Local validation: workflow/configuration syntax, full available Git history with the checked-in Gitleaks configuration, and whitespace checks. GitHub Actions results must also be reviewed on the draft pull request. No repository application scripts are executed by this change.
