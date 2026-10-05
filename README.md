# johnsathya-fyi-public

This repo holds no application code on purpose.

It exists only because GitHub Actions minutes are billed on private repos
but free and unlimited on public ones. The actual code for johnsathya.fyi
lives in a private repo and never gets pushed here.

Each workflow in `.github/workflows/` checks out the **private** repo at
build time (using a repo-scoped token stored as a secret here), builds it,
and deploys it to Cloudflare. The checked-out code only ever exists inside
the ephemeral GitHub Actions runner for that one run — it is not committed
or stored in this repo, so nothing proprietary is ever visible here.

Triggered by a `repository_dispatch` event sent from the private repo's
Cloudflare Worker right after it commits a change (publish/unpublish), or
manually via `workflow_dispatch`.
