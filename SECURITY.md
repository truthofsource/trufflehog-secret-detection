# Security boundaries

Use fictional fixtures only. Never publish raw candidate secrets, private scanner diagnostics, production resource inventories, Terraform state or employee records. A scanner report can itself contain sensitive values and paths.

The local viewer is loopback-only and unauthenticated; it is not a hosted security dashboard. Scanner contract tests do not establish that all current packages, infrastructure or deployed images are secure. Report issues without attaching real secrets or private source records.
