# OpenShock Maintainers

OpenShock is run by volunteers. This file records who is responsible for what, so that
contributors and security researchers know who makes decisions.

## Maintainers

Members of the [`@OpenShock/maintainer`](https://github.com/orgs/OpenShock/teams/maintainer)
team have final say on what is merged and released, and operate the hosted service.

| Maintainer                                   | Focus |
| -------------------------------------------- | ----- |
| [@LucHeart](https://github.com/LucHeart)     |       |
| [@hhvrc](https://github.com/hhvrc)           |       |
| [@nullstalgia](https://github.com/nullstalgia) |     |

<!-- TODO(maintainers): fill in the Focus column (e.g. backend, frontend, firmware, infrastructure) and correct this list if it is out of date. -->

## Security response

Vulnerability reports sent through GitHub private vulnerability reporting or to
[security@openshock.org](mailto:security@openshock.org) are handled by the maintainers listed
above, following the [security policy](https://github.com/OpenShock/.github/blob/main/SECURITY.md).

Checklist for whoever picks up a report:

1. Acknowledge the report within 3 working days.
2. Reproduce and triage within 14 days. Accept it as a draft advisory or close it with an explanation.
3. Develop the fix in the advisory's temporary private fork, not in a public branch or pull request.
4. Patch the hosted service, then release for self-hosters and firmware.
5. Request a CVE through the advisory for medium severity or higher in released software.
6. Publish the advisory with the fixed version set, and credit the reporter if they agreed.
7. Add the reporter to [SECURITY-ACKNOWLEDGMENTS.md](https://github.com/OpenShock/.github/blob/main/SECURITY-ACKNOWLEDGMENTS.md).

Maintainers must watch the repositories with **Custom → Security alerts** enabled. GitHub does
not notify anyone about private vulnerability reports otherwise.

## Decision making

Day-to-day decisions are made by the maintainers of the affected repository through pull request
review. Changes that affect several components, the hosted service or project policy are agreed
among the maintainers.

## Becoming a contributor or maintainer

Regular contributors may be invited to the organization by the maintainers. There is no formal
process; sustained, good-quality contributions and constructive behaviour in the community are
what count.
