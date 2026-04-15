---
title: Template Variables
---

# Template Variables

Enterprise Portal content supports Mustache-style templating with `{{ }}` syntax for dynamic rendering. These variables are resolved at render time based on the customer's license and entitlements.

## Available Variables

| Variable | Description |
|---|---|
| `{{ app.name }}` | Your application name |
| `{{ app.slug }}` | URL-friendly app identifier |
| `{{ customer.name }}` | Customer's name |
| `{{ customer.email }}` | Customer's email |
| `{{ customer.id }}` | Customer ID |
| `{{ channel.name }}` | Release channel (Stable, Beta, etc.) |
| `{{ channel.slug }}` | URL-friendly channel identifier |
| `{{ release.version }}` | Current release version |
| `{{ license.* }}` | Any field from the license object (e.g. `{{ license.id }}`, `{{ license.expiresAt }}`) |
| `{{ entitlements.* }}` | Any entitlement value — built-in or custom (see below) |

## Entitlement Variables

Entitlement variables follow the pattern `{{ entitlements.<key> }}` where `<key>` matches the field name defined in your license. For example:

- `{{ entitlements.isHelmInstallEnabled }}` — whether Helm installation is enabled
- `{{ entitlements.isEmbeddedClusterDownloadEnabled }}` — whether embedded cluster download is enabled
- `{{ entitlements.maxSeats }}` — a custom numeric entitlement

## Your License

{{#each license}}
- **{{@key}}**: {{this}}
{{/each}}

## Your Entitlements

{{#each entitlements}}
- **{{@key}}**: {{this}}
{{/each}}

## Conditional Rendering

Use Handlebars-style `{{#if}}` blocks to conditionally show content based on entitlements:

```
{{#if entitlements.isHelmInstallEnabled}}
This content only appears for customers with Helm install enabled.
{{/if}}
```

Negation is also supported:

```
{{#unless entitlements.isHelmInstallEnabled}}
This content appears when Helm install is NOT enabled.
{{/unless}}
```
