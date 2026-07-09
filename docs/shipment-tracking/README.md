# Shipment Tracking

Process for tracking hardware shipments from order to received.

## Workflow

```
PO Placed → Tracking # Received → Carrier Monitoring → Delivery → Receiving Inspection → Asset Created
```

## Tracking Fields

Snipe-IT doesn't have dedicated shipment tracking fields. Use the asset's **Order Number** and **Notes** fields as follows:

| Snipe-IT Field | What to store |
|----------------|---------------|
| `order_number` | PO number or order confirmation ID |
| `purchase_order` | Internal PO reference |
| `purchase_date` | Date order was placed |
| `notes` | Tracking URL, carrier, ETA, receiving notes |
| `expected_checkin_date` | Estimated delivery date |

## Shipment Log Template

Use this format in asset notes or a separate spreadsheet:

```
Order: PO-2026-0042
Carrier: FedEx
Tracking: 7945-1234-5678
https://www.fedex.com/fedextrack/?trknbr=7945-1234-5678
Ordered: 2026-06-15
ETA: 2026-06-22
Received: 2026-06-21
Condition: Good
Received by: jdoe
```

## Discrepancy Handling

| Issue | Action |
|-------|--------|
| Wrong item | Refuse delivery, contact vendor immediately |
| Damaged | Photo documentation, file claim, initiate RMA |
| Short quantity | Verify packing slip, request shortage fulfillment |
| Late | Check carrier portal, escalate to vendor if >5 days past ETA |

## Carrier Quick Reference

| Carrier | Tracking URL Pattern |
|---------|---------------------|
| FedEx | `https://www.fedex.com/fedextrack/?trknbr={number}` |
| UPS | `https://www.ups.com/track?tracknum={number}` |
| USPS | `https://tools.usps.com/go/TrackConfirmAction?tLabels={number}` |
| DHL | `https://www.dhl.com/en/express/tracking.html?AWB={number}` |
