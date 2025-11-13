# CTF Pilot's Page Schema

This schema defines the structure for describing static pages used by the platform (for example docs, information pages, or static site pages).  
It is a human-friendly reference of the JSON Schema in `schema.json` and includes examples for YAML and JSON files.

## Quick reference — required fields

At minimum a page object SHOULD include the following properties (the schema lists them as required):

- `enabled` (boolean) — whether the page is enabled. Default: `true`.
- `slug` (string) — machine-friendly slug. Must match `^[a-z0-9-]+$`.
- `title` (string) — human-friendly title of the page.
- `route` (string) — route used for navigation (e.g. `/example-page`).
- `content` (string) — path to the content file for the page (must end with `.md`, `.html`, or `.txt`). Default: `page.md`.
- `format` (string) — either `markdown` or `html` (controls rendering). Default: `markdown`.

## Field constraints and allowed values

This section lists the main validation constraints defined in the schema.

- `version` (string, optional) — schema version (e.g. `1.0.0` or `1`). Fully optional; if omitted the latest schema version is assumed.
- `enabled`: boolean. Default `true`.
- `slug`: string matching regex `^[a-z0-9-]+$`. Min length 1, max length 50.
- `title`: string. Min length 1, max length 100.
- `route`: string. Min length 1, max length 100. Typically starts with a slash, e.g. `/demo`.
- `content`: string matching the pattern `^([a-zA-Z0-9-_.]+\.(md|html|txt))$`. This must point to a file in the repository such as `page.md` or `README.md`. Default `page.md`. Min length 1, max length 255.
- `auth`: boolean. Default `false`. When `true` the page requires authentication to view.
- `draft`: boolean. Default `false`. When `true` the page is a draft and not ready for public viewing.
- `format`: enum with values: `markdown`, `html`. Default `markdown`.

## Field reference (detailed)

- `enabled` (boolean)
  - Description: Whether the page is published/active. Use `false` for unpublished pages.

- `slug` (string)
  - Description: Lowercase slug used to identify the page. Allowed pattern: `^[a-z0-9-]+$`.

- `title` (string)
  - Description: The readable title displayed to users.

- `route` (string)
  - Description: Web route for navigation. Example: `/example-page`.

- `content` (string)
  - Description: Path to the content file relative to the page directory. Must end with `.md`, `.html`, or `.txt`.
  - Default: `page.md`.

- `auth` (boolean)
  - Description: When true, only authenticated users can access the page.
  - Default: `false`.

- `draft` (boolean)
  - Description: Marks the page as a draft. Draft pages are typically not displayed publicly.
  - Default: `false`.

- `format` (string)
  - Allowed values: `markdown`, `html`.
  - Default: `markdown`.

## Examples

YAML example (minimal):

```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/ctfpilot/page-schema/refs/heads/main/schema.json
enabled: true
slug: "demo-page"
title: "Demo Page"
route: "/demo-page"
content: "page.md"
format: "markdown"
```

JSON example (minimal):

```json
{
  "$schema": "https://raw.githubusercontent.com/ctfpilot/page-schema/refs/heads/main/schema.json",
  "enabled": true,
  "slug": "demo-page",
  "title": "Demo Page",
  "route": "/demo-page",
  "content": "page.md",
  "format": "markdown"
}
```

## Linking to the schema

Add the following top-line to your YAML files to enable editor validation and autocompletion:

```yaml
# yaml-language-server: $schema="https://raw.githubusercontent.com/ctfpilot/page-schema/refs/heads/main/schema.json"
```

Add the following to your JSON files to enable editor validation and autocompletion:

```json
{
  "$schema": "https://raw.githubusercontent.com/ctfpilot/page-schema/refs/heads/main/schema.json"
}
```

*You may replace the URL with a local path to `schema.json` or to a specific version/release in the GitHub repository, such as with: `https://raw.githubusercontent.com/ctfpilot/page-schema/refs/tags/vX.X.X/schema.json`.*

## Best practices and notes

- Use `slug` values that are short, lowercase, and hyphen-separated.
- Prefer `content` files in Markdown (`.md`) for ease of editing and portability unless you need raw HTML.
- Use `auth: true` sparingly — prefer to gate only genuinely restricted pages.
- `draft: true` is useful while authoring content to prevent accidental publication.
- When referencing the schema in editors, use the top-line comment for YAML shown above or the `$schema` property for JSON files to enable editor validation and autocompletion.

## Contributing

We welcome contributions of all kinds, from **code** and **documentation** to **bug reports** and **feedback**!

Please check the [Contribution Guidelines (`CONTRIBUTING.md`)](/CONTRIBUTING.md) for detailed guidelines on how to contribute.

To maintain the ability to distribute contributions across all our licensing models, **all code contributions require signing a Contributor License Agreement (CLA)**.
You can review **[the CLA here](https://github.com/ctfpilot/cla)**. CLA signing happens automatically when you create your first pull request.  
To administrate the CLA signing process, we are using **[CLA assistant lite](https://github.com/marketplace/actions/cla-assistant-lite)**.

*A copy of the CLA document is also included in this repository as [`CLA.md`](CLA.md).*  
*Signatures are stored in the [`cla` repository](https://github.com/ctfpilot/cla).*

## License

This schema and repository is licensed under the **EUPL-1.2 License**.  
You can find the full license in the **[LICENSE](LICENSE)** file.

We encourage all modifications and contributions to be shared back with the community, for example through pull requests to this repository.  
We also encourage all derivative works to be publicly available under the **EUPL-1.2 License**.  
At all times must the license terms be followed.

For information regarding how to contribute, see the [contributing](#contributing) section above.

CTF Pilot is owned and maintained by **[The0Mikkel](https://github.com/The0mikkel)**.  
Required Notice: Copyright Mikkel Albrechtsen (<https://themikkel.dk>)

## Code of Conduct

We expect all contributors to adhere to our [Code of Conduct](/CODE_OF_CONDUCT.md) to ensure a welcoming and inclusive environment for all.
