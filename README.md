# Pipeline Defense Matrix

[![Deploy to Pages](https://github.com/hibachirat/pipeline-defense-matrix/actions/workflows/pages.yml/badge.svg)](https://github.com/hibachirat/pipeline-defense-matrix/actions/workflows/pages.yml)
[![Security](https://github.com/hibachirat/pipeline-defense-matrix/actions/workflows/security.yml/badge.svg)](https://github.com/hibachirat/pipeline-defense-matrix/actions/workflows/security.yml)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/hibachirat/pipeline-defense-matrix/badge)](https://scorecard.dev/viewer/?uri=github.com/hibachirat/pipeline-defense-matrix)

A layered-defense reference for CI/CD pipeline and software-supply-chain security:
**21 control layers** mapped to pipeline stages, cross-referenced against **133 tools**
(with zero-cost and enterprise paths for each), and tested against **14 documented
supply-chain incidents** — from Equifax to the 2026 npm worms — with an honest verdict
on which layer would (or would not) have caught each.

Anchored to the **CIS Software Supply Chain Security Guide**, **OWASP CI/CD Top 10**,
**SLSA v1.2**, **NIST SSDF**, and the **EU CRA**. Includes a cross-language map of where
each ecosystem executes dependency code, a private-repo cost model, reference stacks,
and a glossary.

**Premise:** no single control stops everything — so the question for each layer is what
it catches, what it structurally *can't*, and what the next layer has to cover.

**Live site:** https://hibachirat.github.io/pipeline-defense-matrix/

---

An independent reference by **Larry Grill** — https://www.linkedin.com/in/larrygrill

© 2026 Larry Grill. All rights reserved. See [LICENSE](LICENSE). This work is independent
and is not derived from, or affiliated with, any employer's proprietary materials.

---

## This repository applies its own advice

The page argues that seven properties cover the incidents it documents. Four of
them are enforceable on a repository this simple, and are enforced here:

| Property | Where |
|---|---|
| Pin everything by digest | Every action is SHA-pinned; Dependabot proposes bumps as reviewable diffs |
| Hold no standing credentials | Pages deploys via OIDC; there are no repository secrets |
| Quarantine new versions | Dependabot `cooldown: 7 days` before any action bump is offered |
| Lint workflows, least-privilege the runner | zizmor and actionlint on every PR; `permissions: {}` at workflow level, granted per job |

CI also extracts the page's inline `<script>` and runs `node --check` on it. The
page is a single HTML file whose tables all render from one script block, so a
syntax error there empties every table at once and nothing else would catch it.
