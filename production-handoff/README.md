# Production Handoff

Process for moving assets from staging/procurement into production.

## Handoff Workflow

```
Procurement → Receiving → Staging → Configuration → Testing → Security Review → Production → Monitoring
```

## Staging Checklist

- [ ] Asset received and logged in Snipe-IT with serial, PO, cost
- [ ] Physical inventory tag affixed
- [ ] Racked / placed in final location
- [ ] Power and network connected
- [ ] Initial configuration applied (OS, firmware, network)

## Pre-Production Checklist

- [ ] Asset status in Snipe-IT set to "Ready to Deploy"
- [ ] All required fields populated (see Documentation section)
- [ ] Security baseline applied and verified
- [ ] Vulnerability scan completed with no critical findings
- [ ] Backup configured and tested (restore verified)
- [ ] Monitoring agent installed and reporting
- [ ] Logging configured and shipping to central log
- [ ] Runbook / wiki page created
- [ ] On-call team notified of new asset

## Handoff Form Template

```
Asset:          SRV001
Handoff Date:   2026-07-15
Handoff By:     jdoe
Received By:    ops-team

[ ] Racked & cabled
[ ] OS installed & patched
[ ] Network configured & tested
[ ] Firewall rules applied
[ ] Monitoring active
[ ] Backup running & verified
[ ] Security scan passed
[ ] Documentation complete
[ ] Stakeholders notified

Notes: ______________________________________________
```

## Acceptance Testing

| Test | Criteria |
|------|----------|
| Power cycle | Clean restart, services auto-start |
| Network connectivity | All interfaces reachable, correct VLAN |
| Service health | All services running and responding |
| Monitoring alert | Asset appears in monitoring, no false alerts |
| Backup/restore | Backup completes, restore verified on test data |
| Load test | Handles expected load (servers) |

## Go-Live Gate

Before flipping an asset to "in production":

1. Run the full acceptance test suite
2. Verify all checkboxes on the handoff form are checked
3. Update Snipe-IT asset status to "Deployed"
4. Assign asset to responsible user in Snipe-IT
5. Send handoff notification email to stakeholders
6. Archive the handoff form in the asset's notes or attachments

## Post-Handoff

- Monitor the asset closely for 48 hours after handoff
- Document any issues found during the initial burn-in period
- Schedule first maintenance window within 30 days
- Review and update documentation with any learnings
