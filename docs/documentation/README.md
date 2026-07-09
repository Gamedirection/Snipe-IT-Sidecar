# Documentation

Standards for documenting IT assets in Snipe-IT and supporting systems.

## What to Document

Every asset should have these fields populated in Snipe-IT:

| Field | Required | Example |
|-------|----------|---------|
| `name` | Yes | "Primary Web Server" |
| `asset_tag` | Yes | "SRV001" |
| `serial` | Yes | SN-12345-ABCDE |
| `model` | Yes | Dell PowerEdge R740 |
| `purchase_date` | Yes | 2026-01-15 |
| `purchase_cost` | Yes | $8,499.99 |
| `supplier` | Yes | Sierputowski IT Supply |
| `order_number` | Yes | PO-2026-001 |
| `notes` | Recommended | Purpose, config, quirks |
| `location` | Recommended | Data Center, Rack 4, U12 |
| `warranty_expires` | Recommended | 2029-01-15 |

## Asset Naming Convention

```
{TYPE}{NUMBER}
```

Examples: `SRV001`, `UPS001`, `SW001`, `FW001`, `LAP001`, `DESK001`

For multi-site: `{SITE}-{TYPE}{NUMBER}` — e.g., `NYC-SRV001`, `LON-SRV001`

## Documentation Standards

### In Snipe-IT Notes Field

Use this structure for the notes field:

```
=== Purpose ===
Primary web server hosting company website and API

=== Configuration ===
- 2x Xeon Silver 4310 CPU
- 128 GB RAM (4x 32GB)
- 2x 2TB SSD RAID1 (OS), 4x 4TB SSD RAID10 (data)
- Network: bonded eth0+eth1 (LACP), VLAN 100

=== Dependencies ===
- Upstream: Load balancer (LB001)
- Downstream: Database cluster (DB pool)
- Backup: Backup server (BK001)

=== Runbook ===
https://wiki.sierputowski.com/servers/srv001

=== Notes ===
- Requires kernel module `xyz` for storage driver
- iDRAC at 10.0.0.15 (credentials in vault)
```

### External Documentation

| What | Where | Linked from |
|------|-------|-------------|
| Runbooks | Internal wiki | Asset notes with URL |
| Network diagrams | draw.io / Lucidchart | Wiki page |
| Credentials | Password manager (Bitwarden/1Password/Vault) | Never in Snipe-IT |
| Architecture docs | GitHub / Wiki | Asset notes with URL |
| Vendor docs | Shared drive / vendor portal | Attached to supplier record |

## Wiki Integration

Link a wiki page in the asset notes with the full configuration:
```
=== Runbook ===
https://wiki.sierputowski.com/servers/srv001
```

The runbook should contain:
- Physical location (rack, U position)
- Network interfaces and IPs
- Services running
- Maintenance procedures
- Restart sequence
- Known issues
- Contact for the asset
