# Vendor Scoping

Process for evaluating, selecting, and managing vendors for IT asset procurement.

## Vendor Evaluation Checklist

- [ ] **Business legitimacy** — registered company, tax ID, references
- [ ] **Product availability** — lead time, stock levels, backorder policy
- [ ] **Pricing & terms** — quoted price vs MSRP, volume discounts, Net30/60
- [ ] **Warranty & support** — length, coverage (advanced replacement?), SLA
- [ ] **Compliance** — GDPR, SOC2, ISO 27001 (if handling data)
- [ ] **EOL/EOSL policy** — how long will they support the product?
- [ ] **Return policy** — DOA window, RMA process, restocking fees
- [ ] **Shipping** — carrier used, insurance, tracking availability

## Vendor Records in Snipe-IT

Add vendors via **Suppliers** in Snipe-IT. Key fields to populate:

| Field | Purpose |
|-------|---------|
| Name | Legal business name |
| Contact | Primary sales/support contact |
| Email | Order & support correspondence |
| Phone | Urgent escalation |
| Fax / Address | PO & shipping |
| URL | Vendor portal or catalog |
| Notes | Account number, discount terms, rep notes |

## RFx Process

1. **RFI** — Request Information: capability, roadmap, compliance docs
2. **RFQ** — Request Quote: pricing, volume discounts, T&Cs
3. **RFP** — Request Proposal: detailed solution, implementation plan, SLA

Store RFx documents in `assets/templates/rfx/` with naming convention:
```
RFQ-{VENDOR}-{DATE}-{PRODUCT}.pdf
```

## Notes

- Link the supplier record to purchase orders in Snipe-IT via `order_number` and `purchase_order` fields
- For multi-year contracts, set `maintained` on licenses and track expiration
