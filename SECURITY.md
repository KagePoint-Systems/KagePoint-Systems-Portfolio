# Security Policy

Last updated: 2026-08-07

---

## Scope

This repository contains **public, sanitized documentation only**. It contains no source code
that runs, no infrastructure configuration, and no credentials.

## What is deliberately not published here

- Credentials, tokens, keys, passwords, recovery codes, certificate material
- IP addresses, subnets, and network zone identifiers
- Hostnames, device serial numbers, MAC addresses
- Firewall rule exports and configuration backups
- Private or internal administrative URLs
- Vendor account identifiers
- Customer, client, or employee data
- Personal contact information
- Internal operational evidence

Conceptual zone names and design principles are published. Implementation specifics are not.

## Reporting a concern

If you believe this repository contains sensitive information that should not be public - a
credential, an infrastructure identifier, personal data, or anything else that looks like a
leak - please report it privately.

**Preferred:** open a [GitHub security advisory](https://github.com/KagePoint-Systems/KagePoint-Systems-Portfolio/security/advisories/new)
on this repository.

Please do **not** open a public issue for a suspected exposure. A public issue advertises the
finding before it can be addressed.

Please include what you found and where. Please do **not** include the sensitive value itself
in the report.

## What to expect

Reports are reviewed by the repository owner. If something sensitive was published in error, it
will be removed and - where a credential is involved - treated as compromised and rotated,
because removing a commit does not undo publication.

## Capability disclaimer

KagePoint Systems does not currently operate a security operations centre, offer managed
detection and response, hold any compliance certification, or provide 24x7 coverage. No such
capability should be inferred from this repository. Reports are handled on a best-effort basis
by an individual owner.

## Scope exclusions

This repository is documentation. There is no application, endpoint, or service here to test.
Vulnerability scanning, penetration testing, and automated exploitation attempts against
KagePoint Systems infrastructure are **not authorised** and are out of scope.
