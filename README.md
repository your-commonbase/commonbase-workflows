# CommonBase Workflows

This repository is called by all other services workflows to simply tag the private [Commonbase-Helm](https://github.com/your-commonbase/commonbase-helm) repository for release to either the development or production Kubernetes clusters.

When called, this workflow will use a PAT with access to the private Commonbase-Helm repository to do the following:
- Clone the repository
- Use `yq` to update the `development-values.yaml` or `production-values.yaml` file with the new service's image tag.
- Commit the change
- Tag it for release, e.g. `development-2025-02-10-19-48`

This final tagging triggers Commonbase-Helm to run.

> **NOTE: This repository must remain public so that it is discoverable and usable by other services Github Workflows.** <span style="color:red">**Notice**</span>