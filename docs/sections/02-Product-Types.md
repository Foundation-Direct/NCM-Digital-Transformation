# Product Types

Each tool must declare a **single primary Product Type**. This enables standardized analysis and benchmarking.

## Product Type Options

Select one:

- **Website**  
  Full website provider or platform.

- **Trade**  
  Trade-in valuation tools, vehicle appraisal, or equity calculators.

- **Finance**  
  Finance applications, pre-approval forms, credit applications, loan calculators.

- **Retailing**  
  Digital retailing flows such as deal builders, payment calculators, or desking flows.

- **Chat/Text**  
  Chat widgets, texting tools, conversational assistants.

- **Call**  
  Call tracking overlays, click-to-call connectors, or call routing UIs.

- **Service**  
  Service schedulers, maintenance booking tools.

- **Other**  
  Any tool that does not fit the above categories. Must include a short description.

## Data Layer Field

Your events should include a `product_type` field that matches one of these values.

**Example:**

```js
window.dataLayer.push({
  event: "dl_tool_load",
  event_owner: "example_company",
  product: "cool chat",
  product_type: "chat"
});
```
