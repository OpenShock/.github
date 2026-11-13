# OpenShock Security Policy

OpenShock lets people control shock collars and similar devices over the internet. A security
bug here can end with a device activating on someone's body without their consent, so we take
vulnerability reports seriously and want them to be easy to make.

This policy covers every repository in the [OpenShock organization](https://github.com/OpenShock)
and the services we host. Individual repositories may add component-specific notes in their own
`SECURITY.md`; where they are silent, this document applies.

- [Reporting a vulnerability](#reporting-a-vulnerability)
- [What to expect from us](#what-to-expect-from-us)
- [Coordinated disclosure](#coordinated-disclosure)
- [Scope](#scope)
- [Rules for testing](#rules-for-testing)
- [Findings that do not qualify](#findings-that-do-not-qualify)
- [Supported versions](#supported-versions)
- [Safe harbor](#safe-harbor)
- [Recognition](#recognition)

## Reporting a vulnerability

**Do not report security vulnerabilities in public issues, pull requests, discussions or on Discord.**

Use one of these private channels:

1. **GitHub private vulnerability reporting (preferred).** Open the affected repository, go to
   its **Security** tab and choose **Report a vulnerability**. Direct links for the main
   components:
   - Backend API and gateway: <https://github.com/OpenShock/API/security/advisories/new>
   - Web frontend: <https://github.com/OpenShock/Frontend/security/advisories/new>
   - Firmware: <https://github.com/OpenShock/Firmware/security/advisories/new>
2. **Email:** [security@openshock.org](mailto:security@openshock.org). Use this if you do not
   have a GitHub account, if the issue is in the hosted service rather than in a repository, or
   if you are not sure which component is affected.

Please write in English and include as much of the following as you can:

- The affected component and version (release tag, commit, firmware version and board, or the
  hostname of the hosted service).
- A description of the vulnerability and the impact a realistic attacker could achieve.
- Step-by-step reproduction instructions or a proof of concept.
- Any mitigation or fix you are aware of.
- A CVSS vector (v4.0 or v3.1) if you have scored it. This is optional.
- Whether you want public credit, and the name or handle and link to use.

Reports produced with the help of AI tools or scanners are welcome only if you have confirmed
the behaviour yourself and include a reproduction you have actually run. Unverified tool output
will be closed without further analysis.

## What to expect from us

OpenShock is maintained by volunteers. The times below are commitments we believe we can keep,
not best-case figures.

| Step                                    | Target                                                      |
| --------------------------------------- | ----------------------------------------------------------- |
| Acknowledgement of your report          | Within 3 working days, and no later than 7 days             |
| Triage result (accepted, declined, or a request for more detail) | Within 14 days of the report       |
| Status updates while the issue is open  | At least every 30 days, and whenever the status changes     |

Fix targets, counted from the day we confirm the vulnerability. These are goals rather than
guarantees:

| Severity | Target for a fix                     |
| -------- | ------------------------------------ |
| Critical | 14 days                              |
| High     | 30 days                              |
| Medium   | 60 days                              |
| Low      | Best effort, usually the next regular release |

Anything that allows controlling another person's device without authorization is treated as
critical regardless of its calculated score.

The hosted service is normally patched first. Releases for self-hosters and firmware updates
follow as soon as they can be built and tested.

If you have not received an acknowledgement after 7 days, please send a reminder to
[security@openshock.org](mailto:security@openshock.org).

## Coordinated disclosure

We follow coordinated vulnerability disclosure with a default deadline of **90 days** from the
date of your report.

- We ask you to keep the details private until a fix is released or the 90 days have passed,
  whichever comes first.
- When a fix is released we publish a GitHub Security Advisory in the affected repository. For
  vulnerabilities of medium severity or higher in released software we request a CVE through
  GitHub.
- For issues that need users to act (updating a self-hosted instance or device firmware) we may
  ask to hold back technical details for up to 30 more days after the fix is available.
- If a vulnerability is being actively exploited we may publish sooner, with whatever mitigation
  is available.
- If we need more than 90 days we will tell you why and propose a new date. If we cannot agree,
  you are free to publish after the deadline. We ask for a few days of notice before you do.

## Scope

### In scope

- Source code in non-archived repositories of the [OpenShock organization](https://github.com/OpenShock),
  including the backend, frontend, firmware, desktop applications, SDKs and integrations.
- Official release artifacts: container images, firmware binaries and installers published by
  the OpenShock organization.
- The hosted service operated by the OpenShock maintainers:
  - `openshock.app` (web application)
  - `api.openshock.app` (API)
  - `*.openshock.app` live control gateways, for example `de1-gateway.openshock.app`
  - `openshock.org` and `wiki.openshock.org` (website and documentation)
- Firmware running on **hardware you own**.
- Instances you host yourself from our code and default configuration.

We are particularly interested in:

- Controlling, pairing with or reading data from devices that are not yours or not shared with you.
- Bypassing share limits (intensity, duration, permissions, pause state) or share-link restrictions.
- Authentication and session flaws, account takeover, and API token scope bypasses.
- Access to another user's personal data.
- Compromise of the firmware update path or of release artifacts.
- Remote code execution, injection, or server-side request forgery in the backend.

### Out of scope

- Instances hosted by anyone other than the OpenShock maintainers. Report those to their operator.
- Third-party services we depend on, such as Cloudflare, GitHub, Discord and our email provider.
  Report those to the vendor. A misconfiguration of such a service on our side is in scope.
- Forks, community modifications, archived repositories and third-party integrations not
  published by the OpenShock organization.
- The radio protocols of supported shock collars. They are designed by the hardware
  manufacturers, and their lack of encryption and replay protection cannot be fixed by OpenShock.
- Any host or service not listed above. If you are unsure, ask before testing.

## Rules for testing

These rules exist because real people wear the devices connected to the hosted service.

- **Only test against accounts, hubs and shockers that you own** or have explicit permission to use.
- **Never send, or attempt to send, a control command to another person's device**, not even to
  prove impact. Demonstrate cross-account access with a second account you control.
- If you find that you could control someone else's device or read someone else's data, stop,
  do not go further, and report immediately.
- Do not access, modify, store or delete data that is not yours beyond the minimum needed to
  show the vulnerability. Do not share such data with anyone but us.
- No denial-of-service testing, load testing or brute forcing against the hosted service.
- No automated scanning that generates significant traffic. Keep automated requests slow.
- No social engineering, phishing or physical attacks against maintainers, users or infrastructure.
- No spam: do not use the hosted service to send email or notifications to people who did not ask.
- Do not use a vulnerability to persist access or to move to other systems.
- Stop and tell us if you believe your testing has affected the availability of the service.

For anything destructive or noisy, run your own instance. The backend and frontend are easy to
[self-host](https://github.com/OpenShock/API#deployment--self-hosting) and the firmware runs on
inexpensive ESP32 boards.

## Findings that do not qualify

Unless you can demonstrate a concrete security impact, we do not treat the following as
vulnerabilities:

- Output of automated scanners without a working proof of concept.
- Missing security headers, cookie flags or TLS settings without a demonstrated attack.
- Missing rate limits, and volumetric or network-level denial of service.
- Email configuration findings (SPF, DKIM, DMARC) and email or username enumeration.
- Self-XSS and other attacks that require the victim to follow the attacker's instructions.
- Clickjacking on pages without sensitive actions.
- Attacks that require a compromised device, a malicious browser extension, an outdated browser,
  or the ability to intercept or modify the victim's network traffic.
- Attacks that require physical access to an unlocked hub, including reflashing it over USB.
- Actions available to an instance administrator, and insecure settings chosen by a self-hoster
  against our documentation.
- Reports that a dependency has a known vulnerability, without showing that OpenShock is affected.
- Version or software disclosure, and other informational findings.
- Bugs without a security impact. Report those as regular issues.

## Supported versions

| Component                       | Versions that receive security fixes                         |
| ------------------------------- | ------------------------------------------------------------ |
| Hosted service                  | Always current                                               |
| Backend (API, gateway, cron)    | The latest release                                           |
| Frontend                        | The latest release                                           |
| Firmware                        | The latest stable release                                    |
| Other OpenShock software        | The latest release                                           |

Older releases are not patched; the fix is to update. Firmware fixes are delivered as a new
release through the normal update mechanism (over-the-air or the web flasher). Reports against
pre-release and development builds are welcome, but they are handled as regular bugs unless the
flaw also affects a supported release.

Security fixes are announced through GitHub Security Advisories in the affected repository and
in the release notes. Watch a repository with **Custom → Security alerts** to be notified.

## Safe harbor

We consider security research carried out in line with this policy to be authorized, lawful and
helpful. If you make a good-faith effort to follow this policy, the OpenShock maintainers:

- will not initiate or support legal action against you, and will not report you to law
  enforcement, for accidental, good-faith violations of this policy;
- will not bring a claim against you for circumventing technology controls in OpenShock software
  or services;
- waive, for the purpose of that research, any restriction in our
  [terms and conditions](https://wiki.openshock.org/home/legal/terms-and-conditions) that would
  conflict with it; and
- will, if a third party takes legal action against you over research that complied with this
  policy, make it known that your actions were conducted in compliance with it.

This commitment is made by the maintainers of OpenShock for the software they publish and the
services they operate. It does not bind third parties, such as hosting providers, hardware
manufacturers, operators of self-hosted instances or other users, and it does not authorize
testing of systems that are not ours. You remain responsible for complying with applicable law.

If you are unsure whether something you plan to do is covered, ask us at
[security@openshock.org](mailto:security@openshock.org) before going further.

## Recognition

OpenShock is a volunteer project and does not pay bug bounties. What we offer:

- Credit in the published security advisory and CVE record, with your consent.
- A place in our [security acknowledgments](https://github.com/OpenShock/.github/blob/main/SECURITY-ACKNOWLEDGMENTS.md).
- A prompt, respectful response, and a clear account of what we did with your report.

Tell us in your report how you would like to be credited, or that you prefer to stay anonymous.
