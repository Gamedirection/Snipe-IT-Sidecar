# Security Setup

Baseline security hardening for IT assets before deployment.

## Pre-Deployment Security Checklist

### For All Assets

- [ ] Firmware/BIOS updated to latest stable
- [ ] Secure boot enabled
- [ ] BIOS password set (servers) or TPM enabled (workstations)
- [ ] Disk encryption enabled (BitLocker / FileVault / LUKS)
- [ ] OS fully patched
- [ ] Local admin password changed from default
- [ ] Host-based firewall enabled
- [ ] Antivirus/EDR agent installed and reporting
- [ ] Asset registered in inventory with serial number
- [ ] Asset tagged with physical asset tag

### For Servers

- [ ] Dedicated service account (no shared root/admin)
- [ ] SSH key-based auth only (password auth disabled)
- [ ] SSH access logged and audited
- [ ] SELinux / AppArmor enforcing
- [ ] Auditd installed with appropriate rules
- [ ] NTP configured
- [ ] Log forwarding to SIEM
- [ ] Monitoring agent installed (Nagios/Zabbix/Datadog)
- [ ] Backup schedule configured and tested
- [ ] CVE scanning completed
- [ ] Network segmentation — server VLAN, restricted ACLs
- [ ] MFA enforced for admin access

### For Network Equipment

- [ ] Default credentials changed
- [ ] Management interface on dedicated VLAN
- [ ] SNMP v3 (not v1/v2c)
- [ ] NTP configured
- [ ] Logging to remote syslog
- [ ] Firmware updated

## Encryption Standards

| Asset Type | Standard | Minimum |
|------------|----------|---------|
| Laptop | Full-disk (BitLocker/FileVault) | AES-256 |
| Desktop | Full-disk (BitLocker/LUKS) | AES-256 |
| Server OS | Full-disk or LUKS for data partitions | AES-256 |
| Server data | At-rest encryption on RAID/volume | AES-256 |
| Backups | Encrypted backup destination | AES-256 |
| Removable media | Hardware-encrypted or VeraCrypt | AES-256 |

## Compliance Mapping

| Control | How to satisfy |
|---------|---------------|
| Asset inventory | Snipe-IT record complete and current |
| Change management | Document firmware/OS updates in asset notes |
| Access control | Assign asset to specific user in Snipe-IT |
| Disposal | Use Snipe-IT "Archived" or "Deleted" status with wipe certificate |
| Audit trail | Snipe-IT action logs track checkin/checkout history |

## Vulnerability Management

1. Scan new assets with vulnerability scanner before deployment
2. Remediate critical/high findings before production handoff
3. Document scan results in asset notes or linked ticket
4. Schedule recurring scans for in-service assets

## Notes

- Security configuration details go in the asset's **Notes** field in Snipe-IT
- For sensitive credentials, use a password manager, never store in Snipe-IT
- Link security scan reports as asset attachments or wiki pages
