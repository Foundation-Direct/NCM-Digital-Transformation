# Implementation Examples

This section provides implementation samples for common integration patterns.

## 1. Iframe Using postMessage → dataLayer

### Iframe Page (Vendor Domain)

```js
// Called when user submits the tool
function notifyParentOfSubmission() {
  window.parent.postMessage({
    event: "dl_tool_submit",
    event_owner: "example_company",
    product: "cool chat",
    product_type: "chat",
    submission_status: "success"
  }, "*");
}
```

### Dealer Page Listener

```js
window.addEventListener("message", function(e) {
  if (!e.data || !e.data.event) return;
  window.dataLayer = window.dataLayer || [];
  window.dataLayer.push(e.data);
});
```

---

## 2. Modal Integration Pushing Directly to dataLayer

```js
function openToolModal() {
  // ... open the modal UI ...
  window.dataLayer = window.dataLayer || [];
  window.dataLayer.push({
    event: "dl_tool_load",
    event_owner: "example_company",
    product: "cool finance",
    product_type: "finance",
    integration_type: "modal"
  });
}

function onFirstInteraction() {
  window.dataLayer.push({
    event: "dl_tool_interaction",
    event_owner: "example_company",
    product: "cool finance",
    interaction_type: "input"
  });
}

function onSubmitSuccess() {
  window.dataLayer.push({
    event: "dl_tool_submit",
    event_owner: "example_company",
    product: "cool finance",
    submission_status: "success",
    pii_collected: "name,email"
  });
}
```

---

## 3. New Window / Redirect with GTM on Vendor Domain

On your own domain, include GTM and emit the same `dl_` events:

```js
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: "dl_tool_load",
  event_owner: "example_company",
  product: "cool retailing",
  product_type: "retailing",
  integration_type: "redirect"
});
```

ASC GTM configurations can be mirrored to your environment if needed.
