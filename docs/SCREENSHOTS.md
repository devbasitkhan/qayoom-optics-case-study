# Screenshot Capture Guide

The case study should use real product screenshots, but production screenshots must be curated carefully because the application contains customer and business data.

## Capture Set

Recommended public screenshots:

1. **Homepage** — desktop hero / featured product experience
2. **Catalog** — product grid and faceted filtering
3. **Product detail** — product presentation without customer data
4. **Prescription configuration** — use empty or clearly synthetic values
5. **Cart** — synthetic cart contents
6. **Checkout** — blank or synthetic customer details only
7. **Order tracking** — synthetic/test order only
8. **Admin dashboard** — only after removing customer/order identifiers and sensitive financial figures
9. **Order management** — synthetic/test order or heavily redacted production data
10. **Product management** — safe product/catalog information
11. **Analytics** — only if business-sensitive numbers are removed or approved for publication
12. **POS terminal** — synthetic sale
13. **Sales history** — synthetic/test records or redacted data
14. **80mm receipt** — test transaction only
15. **A4 packing slip** — test transaction only

## Never Publish

Do not commit screenshots containing:

- customer names without explicit permission
- phone numbers
- email addresses
- home/delivery addresses
- order identifiers that expose customer records
- uploaded bank-transfer receipts
- authentication codes or tokens
- internal credentials
- API keys
- courier credentials
- private financial/ledger information
- private staff information
- browser developer tools showing secrets or environment variables

## Preferred Capture Method

Use dedicated test data wherever possible instead of blurring real customer information after capture.

A screenshot that never contained private data is safer than a production screenshot that relies on visual redaction.

## File Structure

When ready, add images using descriptive filenames:

```text
assets/
└── screenshots/
    ├── 01-homepage.png
    ├── 02-catalog.png
    ├── 03-product-detail.png
    ├── 04-prescription-config.png
    ├── 05-cart.png
    ├── 06-checkout.png
    ├── 07-order-tracking.png
    ├── 08-admin-dashboard.png
    ├── 09-admin-orders.png
    ├── 10-product-management.png
    ├── 11-analytics.png
    ├── 12-pos-terminal.png
    ├── 13-sales-history.png
    ├── 14-thermal-receipt.png
    └── 15-packing-slip.png
```

## Presentation

The final README should not become a gallery of fifteen full-width images. Use approximately 5–8 of the strongest screenshots in the main README and place additional screens in a dedicated gallery document if needed.

The strongest visual sequence is likely:

**Storefront → Prescription Product → Checkout → Admin Dashboard → Order Operations → POS → Receipt / Packing Slip**

That sequence demonstrates that this is an end-to-end operational system rather than only a storefront design.
