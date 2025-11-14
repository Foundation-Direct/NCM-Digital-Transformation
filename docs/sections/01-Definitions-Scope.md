# Definitions & Scope

## Definitions

**Dealer Site**  
The primary website owned by the dealership (e.g., `www.exampledealer.com`).

**Vendor Tool / Product**  
Any third-party feature integrated into the dealer site, such as:
- Digital retailing flows
- Trade-in forms
- Chat/Text widgets
- Finance applications
- Service schedulers
- Call tracking overlays

**Integration Type**  
The way your product is technically integrated into the site (iframe, modal, new tab, redirect).

**Data Layer (`window.dataLayer`)**  
The shared JavaScript array used by GTM and GA4 to read event data.

**ASC Events**  
Standardized event structures used for automotive measurement (e.g., form submission, communication engagement).

## Scope

This specification applies to **all vendor tools installed on dealer websites** that are measured under ASC-aligned analytics. It describes requirements for:

- Declaring your product type
- Declaring your integration type
- Emitting events to `window.dataLayer`
- Working with GA4 and GTM
- Handling iframe and cross-domain constraints
