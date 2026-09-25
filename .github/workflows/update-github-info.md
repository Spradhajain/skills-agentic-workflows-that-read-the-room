---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
---

# Update GitHub Info

Keep `site/content/github-info.md` current with useful, practical GitHub guidance for developers.

Before making any changes:

1. Use the GitHub repository API tools to read `notes/mona-notes.md`, `site/content/github-info.md`, and any relevant repository guidance or reference files. Do not use terminal, CLI, or sandboxed commands to read repository guidance or reference files.
2. Use `web-fetch` to read https://github.blog/latest/.
3. Use `web-fetch` to read https://github.blog/changelog/.

Use the official GitHub Blog and Changelog pages as sources for any new information. Keep summaries short and practical, and include the source URL for each update. Update only `site/content/github-info.md`; preserve its existing editorial structure and avoid unrelated changes.

When the content needs an update, use the edit tool to modify the file, then use the `create-pull-request` safe output to open one pull request for Mona to review. The pull request should summarize the updates and cite the official sources. Never write directly to `main`, and do not open a pull request when no meaningful update is needed.