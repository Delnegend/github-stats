<div align="center">

# github-stats

**Profile-ready charts of your GitHub activity — contribution overview plus language breakdown — rebuilt by a daily workflow and served straight from this repo.**

[![License](https://img.shields.io/github/license/Delnegend/github-stats?style=flat-square)](LICENSE)

</div>

---

## Quick Start

```bash
# 1. Generate the token: a classic personal access token with
#    read:user, user:email, and repo — save it as an Actions secret named ACCESS_TOKEN
# 2. Run the "Generate Stats Images" workflow (or wait for its daily 00:05 UTC schedule)
# 3. Read the charts from the `generated` branch: overview.svg and languages.svg
```

```markdown
![](https://github.com/Delnegend/github-stats/blob/generated/overview.svg#gh-dark-mode-only)
![](https://github.com/Delnegend/github-stats/blob/generated/overview.svg#gh-light-mode-only)
![](https://github.com/Delnegend/github-stats/blob/generated/languages.svg#gh-dark-mode-only)
![](https://github.com/Delnegend/github-stats/blob/generated/languages.svg#gh-light-mode-only)
```

## Highlights

- **Theme-aware images** — `overview.svg` and `languages.svg` swap automatically between GitHub light and dark mode.
- **Private work counts too** — the token lets the analysis include private repositories and repos you contributed to but don't own.
- **A maintained fork** — the generator was ported from [jstrieb/github-stats](https://github.com/jstrieb/github-stats) (Python) to **Zig**, with builds for Linux, macOS and Windows.
- **JSON on the side** — the same workflow can dump the raw statistics for analysis with `jq`.

## Configuration

```bash
# Optional: keep repos, languages, or private activity out of the charts
EXCLUDE_REPOS="Delnegend/github-stats"   # names or globs, e.g. "Vessel9457/*"
EXCLUDE_LANGS="HTML,CSS"
EXCLUDE_PRIVATE="true"
```

Set them as Actions secrets (private names stay private) or as workflow env vars. Raising the retry count helps during GitHub API brownouts (`MAX_RETRIES`, default 5).

## Build locally

```bash
zig build          # ./zig-out/bin/github-stats
zig build release  # release binaries for tagging
```

## Credits

Upstream project by [jstrieb](https://github.com/jstrieb/github-stats) — ported here from Python to Zig. The `generated` branch holds only the rendered charts.

## License

[MIT](LICENSE)
