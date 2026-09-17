## APIBreak

**7 breaking**, 1 deprecation, 9 advisory, 19 not compared — 10 endpoints checked, 210 additive changes not listed.

### Findings

| Severity | Vendor | Endpoint | What changed |
| --- | --- | --- | --- |
| **breaking** | github | `GET /orgs/{org}/copilot/metrics` | present in the baseline, absent from the current spec |
| **breaking** | stripe | `POST /v1/checkout/sessions` | `requestBody.ui_mode` — "ui_mode" no longer accepts "custom", "embedded", "hosted" (it now accepts "elements", "embedded_page", "hosted_page") |
| **breaking** | stripe | `POST /v1/checkout/sessions` | `requestBody.line_items[].dynamic_tax_rates` — request field "line_items[].dynamic_tax_rates" no longer appears in the schema (and its 1 nested field) |
| **breaking** | stripe | `POST /v1/checkout/sessions` | `response.200.line_items.data[].discounts[].discount.coupon` — response field "line_items.data[].discounts[].discount.coupon" no longer appears in the schema (and its 17 nested fields) |
| **breaking** | stripe | `POST /v1/promotion_codes` | `requestBody.promotion` — "promotion" is a new required request field |
| **breaking** | stripe | `POST /v1/promotion_codes` | `requestBody.coupon` — request field "coupon" no longer appears in the schema |
| **breaking** | stripe | `POST /v1/promotion_codes` | `response.200.coupon` — response field "coupon" no longer appears in the schema (and its 19 nested fields) |
| deprecation | github | `GET /repos/{owner}/{repo}/dependency-graph/sbom` | marked deprecated since the baseline |
| advisory | github | `GET /repos/{owner}/{repo}/issues` | `response.200.[].issue_field_values[].data_type` — "[].issue_field_values[].data_type" may now return "multi_select", which the baseline did not list |
| advisory | github | `POST /repos/{owner}/{repo}/issues` | `response.201.issue_field_values[].data_type` — "issue_field_values[].data_type" may now return "multi_select", which the baseline did not list |
| advisory | stripe | `GET /v1/invoices` | `response.200.data[].customer_tax_ids[].type` — "data[].customer_tax_ids[].type" may now return "fo_vat", "gi_tin", "ic_nif", "it_cf", "lk_vat", "pl_nip", "py_ruc", which the baseline did not list |
| advisory | stripe | `GET /v1/invoices` | `response.200.data[].default_tax_rates[].tax_type` — "data[].default_tax_rates[].tax_type" may now return "mass_transit_parking_tax", "parking_tax", which the baseline did not list |
| advisory | stripe | `GET /v1/invoices` | `response.200.data[].payment_settings.payment_method_types[]` — "data[].payment_settings.payment_method_types[]" may now return "alipay", "billie", "custom", "mb_way", "pay_by_bank", "payto", "pix", "satispay", "twint", "upi", which the baseline did not list |
| advisory | stripe | `GET /v1/invoices` | `response.200.data[].payments.data[].payment.type` — "data[].payments.data[].payment.type" may now return "payment_record", which the baseline did not list |
| advisory | stripe | `POST /v1/checkout/sessions` | `response.200.line_items.data[].taxes[].rate.tax_type` — "line_items.data[].taxes[].rate.tax_type" may now return "mass_transit_parking_tax", "parking_tax", which the baseline did not list |
| advisory | stripe | `POST /v1/checkout/sessions` | `response.200.ui_mode` — "ui_mode" may now return "elements", "embedded_page", "hosted_page", which the baseline did not list |
| advisory | stripe | `POST /v1/payment_intents` | `response.200.excluded_payment_method_types[]` — "excluded_payment_method_types[]" may now return "bizum", "mb_way", "payto", "scalapay", "sunbit", "upi", which the baseline did not list |
| not_compared | github | `GET /repos/{owner}/{repo}/issues` | `response.200` — 4 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at [].issue_field_values[].value, [].labels[], [].performed_via_github_app.owner and elsewhere |
| not_compared | github | `POST /repos/{owner}/{repo}/check-runs` | `requestBody` — not compared in the baseline: an anyOf/oneOf union, which this check does not compare |
| not_compared | github | `POST /repos/{owner}/{repo}/check-runs` | `response.201` — 2 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at app.owner, deployment.performed_via_github_app.owner |
| not_compared | github | `POST /repos/{owner}/{repo}/issues` | `requestBody` — 3 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at labels[], milestone, title |
| not_compared | github | `POST /repos/{owner}/{repo}/issues` | `requestBody.issue_field_values[].value` — not compared in the current spec: an anyOf/oneOf union, which this check does not compare |
| not_compared | github | `POST /repos/{owner}/{repo}/issues` | `response.201` — 4 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at issue_field_values[].value, labels[], performed_via_github_app.owner and elsewhere |
| not_compared | stripe | `GET /v1/invoices` | `response.200` — 37 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at data[].account_tax_ids[], data[].application, data[].automatic_tax.liability and elsewhere |
| not_compared | stripe | `GET /v1/invoices` | `response.200.data[].payments.data[].payment.payment_record` — not compared in the current spec: an anyOf/oneOf union, which this check does not compare |
| not_compared | stripe | `POST /v1/checkout/sessions` | `requestBody` — 11 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at custom_text.after_submit, custom_text.shipping_address, custom_text.submit and elsewhere |
| not_compared | stripe | `POST /v1/checkout/sessions` | `requestBody` — 6 fields were not compared in the current spec — an anyOf/oneOf union, which this check does not compare — at branding_settings.background_color, branding_settings.button_color, payment_method_options.payto.mandate_options.amount and elsewhere |
| not_compared | stripe | `POST /v1/checkout/sessions` | `response.200` — 35 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at adaptive_pricing, after_expiration, automatic_tax.liability and elsewhere |
| not_compared | stripe | `POST /v1/checkout/sessions` | `response.200.line_items.data[].discounts[].discount.coupon.applies_to.products` — not compared in the baseline: the schema nests deeper than this check follows (8 levels) |
| not_compared | stripe | `POST /v1/checkout/sessions` | `response.200` — 5 fields were not compared in the current spec — an anyOf/oneOf union, which this check does not compare — at branding_settings.icon, branding_settings.logo, line_items.data[].adjustable_quantity and elsewhere |
| not_compared | stripe | `POST /v1/payment_intents` | `requestBody` — 56 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at mandate_data, off_session, payment_method_data.billing_details.address and elsewhere |
| not_compared | stripe | `POST /v1/payment_intents` | `requestBody` — 16 fields were not compared in the current spec — an anyOf/oneOf union, which this check does not compare — at amount_details.discount_amount, amount_details.line_items, amount_details.shipping and elsewhere |
| not_compared | stripe | `POST /v1/payment_intents` | `response.200` — 15 fields were not compared in the baseline — an anyOf/oneOf union, which this check does not compare — at amount_details, application, automatic_payment_methods and elsewhere |
| not_compared | stripe | `POST /v1/payment_intents` | `response.200.managed_payments` — not compared in the current spec: an anyOf/oneOf union, which this check does not compare |
| not_compared | stripe | `POST /v1/promotion_codes` | `response.200.customer` — not compared in the baseline: an anyOf/oneOf union, which this check does not compare |
| not_compared | stripe | `POST /v1/promotion_codes` | `response.200.promotion.coupon` — not compared in the current spec: an anyOf/oneOf union, which this check does not compare |

### Sources

- `github` — https://raw.githubusercontent.com/github/rest-api-description/29bcb5569205519836ea9abf0c954e737ae71029/descriptions/api.github.com/api.github.com.json, baseline 1.1.4 (commit@33b621b, 2026-03-19T01:00:10Z) → current 1.1.4 (commit@29bcb55, 2026-09-16T21:57:32Z), fetched 2026-09-17T06:02:30.692Z
- `stripe` — https://raw.githubusercontent.com/stripe/openapi/30d3391cc09a0f67ad29bee002f570811b19e1da/openapi/spec3.json, baseline 2025-08-27.basil (commit@62fbe07, 2025-08-19T19:54:23Z) → current 2026-08-26.dahlia (commit@30d3391, 2026-08-26T17:57:44Z), fetched 2026-09-17T06:02:32.361Z

Only the endpoints in your apibreak.json were compared. An endpoint this check could not read at all is listed as unknown and fails the run. A part of a schema outside what it compares — an anyOf/oneOf union, a chain deeper than it follows, an object whose fields the vendor does not enumerate — is listed as not compared, on every run, and never fails one.
