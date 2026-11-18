# Boring Data Platform for Cursor

Research public federal procurement records with source references. This plugin
connects Cursor to the Boring Data Platform™ MCP service, operated by
Parsevia LLC.

## What you can research

Use the connection to research:

- SAM.gov opportunities and DLA DIBBS RFQs, with source notices and available
  solicitation documents and extracted text.
- Federal contract awards and reported subawards.
- SAM entity registrations, entity profiles, exclusions and integrity records.
- GSA acquisition vehicle contracts and CALC+ labor ceiling rates.
- DHS and DOJ procurement forecasts and SBA mentor-protege agreements.
- Federal Register notices, federal assistance listings, SBA size standards,
  and wage determinations.
- The DLA PUB LOG NSN catalog and DLA last-paid prices.
- Dataset coverage and source dates.

Source coverage varies. Forecasts are plans that may change or be canceled.
Subaward data covers first-tier subawards reported from October 1, 2024, and
does not show every subcontracting relationship.
CALC+ rates are ceiling rates, not salaries or actual prices paid. Global
document search is in beta. Check source references and the
[availability notes](https://www.boringdataplatform.com/developers) before relying
on a result.

## Account and pricing

The plugin is free to install. An active Boring Data Platform account is required
to use the hosted service. The free plan includes 5,000 requests per month with
no credit card. Optional paid plans provide higher request limits. MCP calls
share the account's plan allowance with API requests. See
[pricing and limits](https://www.boringdataplatform.com/pricing).

The MIT license covers the files in this repository. It does not replace the
[hosted service terms](https://www.boringdataplatform.com/terms) or grant
unlimited service access.

## Connect in Cursor

1. Load the plugin in Cursor. For local testing, place this directory at
   `~/.cursor/plugins/local/boring-data-platform`, reload Cursor, and check
   Customize for its MCP server. Local imports must already be permitted by your
   organization. Do not replace an existing installation without reviewing it.
2. Use Cursor's authentication control for the Boring Data Platform server.
   Finish Boring Data Platform sign-in and review the requested access before
   approving it. No manually supplied API key or client secret is required.
3. Verify a read with a small request, such as the example below. A tool appearing
   in the catalog does not by itself prove that data access works.

The configured resource is:

```text
https://www.boringdataplatform.com/api/mcp
```

The package uses Cursor's remote OAuth discovery. BDP's protected-resource
metadata advertises `offline_access` for the connection. This permits token
refresh until access is revoked. The sign-in flow may also display standard
identity scopes. Review the actual consent screen; this package does not supply
credentials or add an API-key fallback.

See [Cursor's plugin instructions](https://cursor.com/docs/plugins) and
[MCP documentation](https://cursor.com/docs/mcp).

## Access and permissions

The MCP procurement tools are read-only. This OAuth connection cannot manage BDP
API keys or webhooks and cannot submit bids or change government source records.

Signing in gives read-only access to procurement data and keeps the connection signed in. It can't change your account.

Revoke the connection in Boring Data Platform Console -> Profile -> Connected
applications.

## Example prompts

- "Which procurement datasets can I research here, and what dates does each one
  cover?"
- "Use search_opportunities with limit 1 to show one opportunity and its source
  reference. Do not make another call unless needed to explain the result."
- "Find DHS procurement forecasts for engineering services. Explain one plan
  using its source reference, and distinguish it from a published solicitation."

## Support and policies

- [Documentation](https://www.boringdataplatform.com/developers)
- [Contact support](https://www.boringdataplatform.com/contact) or
  support@boringdataplatform.com
- [Privacy policy](https://www.boringdataplatform.com/privacy)
- [Service terms](https://www.boringdataplatform.com/terms)

Publisher: Parsevia LLC.
