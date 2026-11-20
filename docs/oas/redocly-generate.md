### Regenerate the API docs

From the root of the developer hub repo, run both commands in this order:

1. Bundle the OpenAPI specification into one file. It's offered as a download on the API docs page, so it must have no external `$ref`s:
   ```
   npx @redocly/cli bundle docs/oas/oas.json --output docs/oas/tax-agile-api.json
   ```
2. Build the docs page:
   ```
   npx @redocly/cli build-docs docs/oas/oas.json --output=redoc-static.html --template=docs/oas/template.html
   ```

The download buttons are set in `redocly.yaml` (`downloadUrls`). Colours and fonts are in `docs/oas/template.html`.
