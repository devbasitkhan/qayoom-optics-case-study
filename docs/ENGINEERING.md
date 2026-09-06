# Engineering Notes

This document highlights selected engineering decisions behind Qayoom Optics without exposing proprietary production source code.

## 1. Model the Retail Domain, Not Just Pages

The project was treated as an operational system rather than a collection of storefront pages.

The data model covers products, categories, images, stock batches, orders, order items, prescriptions, customer prescription records, payments/disputes, reviews, inquiries, shop ledger data and configuration.

This matters because workflows such as checkout, stock administration, POS sales and order fulfillment need to operate on the same underlying business state.

## 2. Prescription Data as Structured Commerce Data

Optical prescriptions contain multiple values for each eye and additional measurements such as PD. Storing this as a generic order note would make validation, display, administration and historical interpretation fragile.

The application therefore treats prescription information as structured domain data that participates in the product/order lifecycle.

Representative measurements include:

- OD / OS
- SPH
- CYL
- AXIS
- ADD
- PD

Lens selection and pricing are integrated into the purchase workflow rather than bolted on after checkout.

## 3. Shared Online and POS Workflows

A physical retailer with an online store can easily end up with two conflicting views of stock and sales.

Qayoom Optics instead uses a unified application/data domain for online and physical-shop operations. Staff can work with products, inventory, orders and sales from the same operational system.

## 4. Historical Receipt Integrity

A receipt represents a transaction at a specific moment in time. If a product title, price or other mutable record changes later, a historical reprint should not silently change with it.

The POS workflow therefore preserves frozen receipt data for completed sales, allowing historical receipts to be reproduced reliably.

## 5. Courier City Resolution

External courier systems have their own canonical city catalog. Real customers may enter variations, alternate spellings or location names that do not exactly match that catalog.

The integration uses a staged matching approach rather than direct equality alone. This reduces avoidable booking failures while keeping courier-specific normalization out of the customer experience.

## 6. Protected Document Delivery

Some application documents should be public, while others should not.

Product imagery can be publicly accessible, but customer uploads and operational documents require different controls. Protected file-serving and proxy workflows are used where direct public storage URLs would create an inappropriate access model.

## 7. Authentication Separation

Customer and staff authentication have different threat models and UX requirements.

The system therefore separates administrative access from customer OTP/session workflows rather than pretending one authentication flow fits both contexts.

Selected controls include signed sessions, route protection, rate limiting, authorization checks and timing-safe comparisons where appropriate.

## 8. Print Is a First-Class Interface

Retail software does not end at the browser viewport.

Qayoom Optics has print-specific output for:

- 80mm thermal receipts
- A4 packing slips

These require dedicated layout behavior, typography and print CSS instead of simply printing the normal web page.

## 9. Server-Oriented Application Design

The Next.js application makes extensive use of server-rendered routes, server components and server actions. Client-side state is used where it makes sense for interactive workflows such as the cart, while sensitive/business operations remain server-side.

## 10. Production Scope Discipline

A case study is useful only if it distinguishes what exists from what was merely explored.

Current production does **not** claim:

- AR / virtual frame try-on
- online card-gateway processing
- complete application-wide Urdu localization

Earlier experimentation with virtual try-on is separate from this production system.

## Engineering Ownership

As sole full-stack developer, I handled the system across requirements analysis, architecture, database design, frontend/backend implementation, integrations, authentication, operational tooling, debugging and deployment.

The production implementation remains private commercial source. These notes document the engineering approach without exposing client data or proprietary code.
