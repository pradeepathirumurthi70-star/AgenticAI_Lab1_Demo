---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

tools:
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
---

# Update GitHub Information

Keep `site/content/github-info.md` current for Mona using GitHub's official updates.

1. Read `notes/mona-notes.md` and follow its guidance about the page and Mona's preferences.
2. Read the current `site/content/github-info.md` to understand its structure and existing content.
3. Use the web-fetch tool to fetch https://github.blog/latest/ and https://github.blog/changelog/.
4. Update only `site/content/github-info.md` with relevant, verified information. Preserve its existing structure and voice, avoid duplicating current content, and include source links for new claims.
5. If there are meaningful changes, use the `create-pull-request` safe output to open a pull request for Mona to review. Summarize the update and cite the fetched sources in the pull request description. Do not write changes directly to the default branch.

If the fetched pages provide no relevant new information, leave the file unchanged and do not open a pull request.