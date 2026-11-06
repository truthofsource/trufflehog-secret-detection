# TruffleHog: strengths and tradeoffs

**Terms used here:** An artifact is a file produced for a release, such as an application ZIP or container image.

| Strength | Why it is useful in this implementation |
| --- | --- |
| **Deleted-history coverage** | Git scanning can find possible credentials in reachable commits even when the current file has been removed. |
| **Credential-focused detectors** | Purpose-built detectors identify credential formats. Provider verification is an optional tool capability; this implementation disables it and treats matches as candidates. |
| **Safer PR trust boundary** | Trusted scripts/policy, exact base/head coverage and reports containing summary counts only prevent a candidate change from selecting its own scanner decision or leaking raw output. |

| Limit | Practical response |
| --- | --- |
| A candidate needs review | A detector match is not proof of a live credential; a public package hash can require independent classification. |
| Scope is explicit | A main-history or PR-range scan is not every branch, ref, artifact, image or external mailbox. |
| Offline means no live validity test | Network none and no-verification reduce exposure, but cannot establish whether a candidate works against a provider. |

## Choosing the right layer

Trivy inventories/scans supported packages and images, with separate configuration capability. TruffleHog focuses on possible credentials and Git-history coverage. Checkov focuses on infrastructure definitions and policy rules. ZAP, used separately by the platform, exercises HTTP behavior; it is not replaced by any of these source scans.

Keep all three outputs tied to an explicit target and date. Tool severity, an organization's release threshold, exploitability and a business risk-acceptance decision are different concepts. A passing narrow check does not certify the entire environment.

The upstream tool documentation describes broader capabilities than every mode used here. The implemented mode and its privacy/network restrictions are established by mapped source and dated tests. [Official TruffleHog reference](https://github.com/trufflesecurity/trufflehog).
