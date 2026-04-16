# Pentagon Marketing Skills

Reusable marketing skills for Pentagon agents. Import via `+ Add` → `Import from URL` using raw GitHub URLs.

## Agent → Skills mapping

| Agent | Skills |
|---|---|
| **Scout** | buyer-research, deep-research, scrape-social, transcribe |
| **Copywriter** | write-copy, edit-copy, email-sequence, tiktok-slides |
| **Strategist** | ad-concepts, build-avatars, campaign-brief |
| **SEO Lead** | keyword-research, seo-audit, schema-markup |
| **Ops** | schedule-content, weekly-review, capture-learnings |

## Import URL format

```
https://raw.githubusercontent.com/fuggysense/pentagon-skills/main/<agent>/<skill-name>.md
```

Example for Scout's buyer-research:
```
https://raw.githubusercontent.com/fuggysense/pentagon-skills/main/scout/buyer-research.md
```

## Skill file format

Pentagon expects:
- `name` — becomes the /command-name
- `description` — agent reads this to decide when to auto-invoke
- Body text below frontmatter — the full instructions. Use `$ARGUMENTS` for user input.
