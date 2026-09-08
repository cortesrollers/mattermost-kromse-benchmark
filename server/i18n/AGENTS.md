# AGENTS.md

These are the shipped server translation catalogs, one go-i18n
`[{"id", "translation"}]` JSON file per locale. **Read
[`i18n/AGENTS.md`](../../i18n/AGENTS.md) at the repository root before editing
any of them** — it covers the whole workflow, the rules CI enforces, and the
plural categories per locale.

The short version:

- Translations ship in the same PR as the English string. All 21 non-English
  catalogs, every time.
- `en.json` holds the English and is edited by hand; run `make i18n-extract`
  from `server` afterwards to restore its order.
- Each id in `en.json` carries a `description` of where the string appears.
  Read it before translating, and write one for ids you add.
- Messages are Go `text/template`. `{{.Field}}` tokens must match the source
  exactly, in both directions.
- A plural translation must define **exactly** the categories its locale uses in
  the server's vendored go-i18n — which for `es`, `fr`, `it` and `pt-BR` is
  `one, other`, with no `many`, unlike current CLDR. See the table in the root
  guide.
- Check your work with `make i18n-verify`.
- Only locale catalogs belong in this directory. The server registers every
  supported-locale `.json` here at startup, and `mmgotool i18n clean-empty`
  rewrites them.
