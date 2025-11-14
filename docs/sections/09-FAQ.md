# FAQ

## Why do we need `dl_` event names?

Using `dl_` ensures that vendor-originated dataLayer events do not conflict with GA4 events emitted via `gtag()`. This prevents duplicate events and stale parameter re-use.

## Can we send events directly to GA4 instead of dataLayer?

You may use `gtag()` or server-side APIs, but for ASC automation and shared reporting, you **must also** emit standardized events into `window.dataLayer` using the pattern described in this spec.

## What if our product runs entirely in an iframe?

You must use `postMessage` to notify the parent page of key events, and the parent page should push those events into `window.dataLayer`. Direct access from the parent to the iframe DOM is not reliable or recommended.

## Do we have to support all three event types (load, interaction, submission)?

Yes, for complete funnel analytics we require at least one event for each of:
- Load/Open
- First meaningful interaction
- Submission/Conversion

## Can we include PII in the dataLayer?

You must **not** include raw PII (e.g., full names, emails) in event parameters. Instead, send:
- Flags (e.g., `pii_collected: "name,email"`)
- Anonymized or hashed identifiers if applicable and compliant with privacy policies.

## Who should we contact if our implementation changes?

Vendors should notify the ASC measurement team or designated contact whenever:
- Event names change
- Event parameters change
- Integration type changes (e.g., iframe → redirect)
- Domains or hosting environments change
