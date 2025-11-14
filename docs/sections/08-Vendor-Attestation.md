# Vendor Checklist & Attestation

Before deployment at scale, vendors should complete the following checklist.

## 1. Product & Integration Details

- [ ] Product name provided
- [ ] Product type selected (website, trade, finance, retailing, chat, call, service, other)
- [ ] Integration type selected (iframe, modal, new_window, redirect)
- [ ] HTML footprint documented (script src, iframe src, container IDs)

## 2. Data Layer Events

- [ ] All events use `dl_` prefixed event names
- [ ] Events include `event_owner` and `product`
- [ ] Events include `product_type` and `integration_type`
- [ ] Load, interaction, and submission events are implemented

## 3. Iframe / Cross-Domain (If Applicable)

- [ ] `postMessage` is implemented in the iframe
- [ ] Parent page listener pushes messages to `window.dataLayer`
- [ ] No attempt to inject ASC GTM into the iframe

## 4. New Window / Redirect (If Applicable)

- [ ] GTM is installed on the vendor domain, or alternate tracking agreement in place
- [ ] `dl_` events are emitted from the vendor environment

## 5. QA & Verification

- [ ] Test site or sandbox provided
- [ ] Sample user flows captured and validated
- [ ] Events visible in GTM preview and GA4 debug view

Vendors should sign off or confirm in writing that they adhere to these requirements and notify ASC of any breaking changes to their integration or event schema.
