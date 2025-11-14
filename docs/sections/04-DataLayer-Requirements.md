# Data Layer Requirements

All vendor events must be pushed into `window.dataLayer`. This is how GTM and GA4 receive and standardize your data.

## Why Use `dl_` Event Names

If you use `gtag("event", ...)`, GA4 automatically mirrors those events into `window.dataLayer`. Reusing the *same* event names in custom pushes can cause:

- **Duplicate events**
- **Stale parameter values** being reused unexpectedly

To avoid this:

- All vendor-originated events must use a **custom event name**.
- Prepend `dl_` to event names.
- Do **not** reuse GA4 event names for your `event` property.

### Correct Pattern

```js
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: "dl_asc_comm_engagement",
  comm_outcome: "start",
  event_owner: "example_company",
  product: "cool chat"
});
```

### Incorrect Pattern

```js
// May cause duplication and circular logic
gtag("event", "asc_comm_engagement");
```

## Required Identification Fields

Each event should include:

- `event_owner` – Your company name or vendor identifier
- `product` – Product name as used in contracts / marketing
- `product_type` – One of the defined product types
- `integration_type` – One of: `iframe`, `modal`, `new_window`, `redirect`

## Optional but Recommended Fields

Where possible, include:

- `page_type` – e.g., `vdp`, `srp`, `homepage`
- `vin` – For vehicle-detail contexts
- `dealer_id` or `account_id` – If known
- `session_id` – If your system uses one

These fields can be added even if your UI is running inside an iframe by using `postMessage` from the iframe to the parent page.
