# Integration Types

Integration type describes *how* your product appears on the dealer site. This determines what tracking is technically possible.

## Integration Type Options

Select one:

### 1. Embedded Inline (Iframe)

Your product loads inside the dealer site as an iframe, overlay, drawer, or embedded widget.

**Characteristics**

- Hosted on your domain
- Rendered inside a `<iframe>` within the dealer site
- Parent page cannot directly access iframe DOM if cross-domain

**Implications**

- Use `postMessage` → parent listener → `window.dataLayer.push()`
- GTM will run on the parent page and must receive events there
- ASC will not inject GTM into your iframe

---

### 2. Modal (On-Page HTML, Not an iframe)

Your product renders as an HTML modal or component in the dealer DOM.

**Characteristics**

- No iframe involved
- Uses standard HTML, CSS, and JavaScript in the dealer's page context

**Implications**

- GTM can observe DOM changes and clicks directly
- You can push events directly to `window.dataLayer`

---

### 3. New Window / New Browser Tab

Your tool opens in a new browser window or tab.

**Characteristics**

- Dealer site remains open
- User interacts with your tool in a separate tab or window

**Implications**

- All tracking for interactions and submissions must originate from your environment
- GTM should be installed on your hosted domain if possible

---

### 4. Full Redirect (Same Tab Navigation)

The dealer site navigates directly to your domain in the same tab.

**Characteristics**

- Dealer site is replaced by your domain
- The user flow continues on your hostname

**Implications**

- GTM must run in your environment or alternate event passbacks must exist
- UTM parameters and cross-domain logic may be required

## Data Layer Field

Include an `integration_type` field in your events:

```js
window.dataLayer.push({
  event: "dl_tool_load",
  event_owner: "example_company",
  product: "cool chat",
  product_type: "chat",
  integration_type: "iframe" // iframe | modal | new_window | redirect
});
```
