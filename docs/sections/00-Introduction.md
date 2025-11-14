# Introduction

Dealership websites frequently integrate third-party tools such as trade-in widgets, digital retailing flows, chat widgets, service schedulers, and calculators.

To accurately measure performance across thousands of dealers, we require a consistent way to:

- Detect **when your product is installed**
- Detect **when it loads**
- Track **interactions and submissions**
- Reconcile data across iframe, modal, new window, or full-redirect flows
- Prevent **tracking duplication** caused by `gtag()` and `window.dataLayer` collisions

This document describes the **ASC Technical Tracking Standard** for third-party tools.

## Goals

- Provide a single, canonical specification for vendor integrations
- Enable automated deployment of tracking logic via Google Tag Manager (GTM)
- Ensure compatibility with Google Analytics 4 (GA4) and ASC event models
- Support embedded, redirected, and cross-domain workflows

## Audience

- Vendor product & engineering teams
- Internal analytics and integrations engineers
- QA and implementation specialists
