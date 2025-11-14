# Event Specification

We require three major event categories for consistent measurement:

1. Load / Open (Start)
2. First Interaction
3. Submission / Conversion

If you already use ASC event names, you can mirror them by prefixing the event with `dl_`.

---

## 1. Load / Open (Start Event)

Triggered when your product becomes visible or usable (e.g., widget appears, modal opens, iframe is shown).

### Example

```js
window.dataLayer.push({
  event: "dl_tool_load",
  event_owner: "example_company",
  product: "cool chat",
  product_type: "chat",
  integration_type: "iframe",
  page_type: "vdp",
  vin: "1HGCM82633A004352"
});
```

---

## 2. First Interaction Event

Triggered on the first meaningful interaction such as:

- First click inside the widget
- First keystroke or input
- Chat session start
- Dropdown selection

### Example

```js
window.dataLayer.push({
  event: "dl_tool_interaction",
  event_owner: "example_company",
  product: "cool chat",
  product_type: "chat",
  interaction_type: "input", // e.g., click | input | selection
  page_type: "vdp"
});
```

---

## 3. Submission / Conversion Event

Triggered when the user submits information (often PII) or completes a key action.

### Example

```js
window.dataLayer.push({
  event: "dl_tool_submit",
  event_owner: "example_company",
  product: "cool chat",
  product_type: "chat",
  submission_status: "success", // success | error | partial
  pii_collected: "name,email",  // do not include raw values
  page_type: "vdp"
});
```

---

## Recommended Naming Alignment with ASC

If you are ASC-aligned, you may also emit these events as logical equivalents:

- `dl_asc_comm_engagement`
- `dl_asc_form_submission`

The underlying parameters (e.g., `comm_outcome`, `form_name`, `event_owner`) should remain ASC-compliant.
