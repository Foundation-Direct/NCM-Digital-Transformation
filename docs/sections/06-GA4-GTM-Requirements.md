# GA4 & GTM Requirements

Our tracking standard assumes GA4 and GTM are used as the primary analytics stack.

## Baseline Requirements

- The dealer site must have **Google Tag Manager** installed.
- GA4 must be configured via GTM or gtag.
- ASC-managed containers will read events from `window.dataLayer`.

## Vendor Responsibilities by Integration Type

### Iframe Integrations

- You must emit events that can be captured at the **parent page** level.
- Use `postMessage` from the iframe → parent listener → `window.dataLayer.push()`.
- We will not inject GTM into your iframe.

### Modal Integrations

- You may push events directly into `window.dataLayer` from your modal JS.
- GTM can also observe DOM interactions if necessary.

### New Window / New Tab

- Your hosted environment should include GTM where possible.
- Emit the same `dl_` events from your own page context.

### Full Redirect (Same Tab)

- Your hosted environment should include GTM where possible.
- If GTM cannot be added, coordinate an alternate mechanism for sending events or server-side notifications.

## Important: Do Not Place ASC GTM in an Iframe

We do **not** recommend or support placing shared GTM containers inside vendor iframes. All shared tracking should flow through the dealer's main GTM container and the dataLayer on the parent page.
