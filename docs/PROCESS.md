# Scope, trust and integration

1. Select the exact target: source commit/lockfiles, selected image or bounded Git history as appropriate.
2. Run trusted scanner tooling and policy outside candidate-controlled execution. Validate the pinned executable/image/version.
3. Keep credentials and unrelated private work outside staged inputs. Scan completion must be explicit.
4. Validate the report shape, inventory/coverage and scanner status before interpreting findings.
5. Apply the actual mode's policy: record advisory findings or enforce an explicitly selected threshold. Never confuse execution failure with an ordinary findings exit code.
6. Repair/retest, preserve remaining issues and bind the result to the selected target.

The actual platform integration is included as [an inert example](../reference/workflows/trufflehog-pr.yml.example). It references the complete platform tooling/paths and is not a drop-in deployment workflow for this smaller repository. Its automatic triggers do not run because it is outside .github/workflows. The new public validation workflow runs contracts only and requires manual dispatch; it was not dispatched here.

No Azure login, new cloud role or Terraform apply is necessary for these local checks. Scanning permission and deployment permission should remain separate. GitHub policy entitlement, branch enforcement and approved release identity need their own verification; a YAML file alone does not prove repository-wide admission.
