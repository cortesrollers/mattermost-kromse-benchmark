# AGENTS.md

Explicitly import subdirectory instruction files that must always be in context:
@server/AGENTS.md

## Translations

Any change that adds or alters a user-facing string must ship its translations
for all 21 non-English locales in the same pull request. There is no external
translation service. See [`i18n/AGENTS.md`](./i18n/AGENTS.md) for the workflow,
the rules CI enforces, and the per-locale plural categories.

## Pull Requests

When creating a pull request, follow `.github/PULL_REQUEST_TEMPLATE.md` exactly:

- Remove all `<!-- -->` comments.
- Omit sections that are not applicable (Ticket Link, Screenshots) — do not write N/A, just remove the header.
- The `#### Release Note` header and its "```release-note" fenced code block **must always be present** (WITHOUT escaping the ``` characters). Write `NONE` if the change has no API, schema, UI, or breaking changes.

## Cursor Cloud Agents

Cursor Cloud Agents must follow `.cursor/AGENTS.md`, materialized by `.cursor/scripts/cloud-agent-start.sh`.

