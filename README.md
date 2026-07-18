# ai-news-digest

An automated digest blog. A scheduled Claude Code cloud agent (a "routine")
runs daily, checks official Anthropic and OpenAI announcement sources, writes
plain-language digest posts, and pushes them here. GitHub Actions builds the
static site and deploys it to GitHub Pages.

- **Agent instructions:** [AGENT.md](AGENT.md) — edit this to change the
  agent's sources, style, or workflow. No routine change needed.
- **Dedup journal:** [journal/covered.json](journal/covered.json) — every
  covered announcement URL; prevents duplicate posts.
- **Build:** `npm install && npm run build` → static site in `dist/`.
  Only dependency is [marked](https://github.com/markedjs/marked)
  (markdown → HTML).
- **Deploy:** [.github/workflows/deploy.yml](.github/workflows/deploy.yml) —
  every push to `main` rebuilds and deploys Pages.

Posts are markdown files in `posts/` named `YYYY-MM-DD-slug.md` with
`title` / `date` / `description` front-matter.
