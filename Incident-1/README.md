# Incident 1: Malicious URL Access Blocked

**Date:** April 30, 2026  
**Severity:** High  
**Status:** Resolved  
**Alert ID:** 8816

## Summary

At 01:46:22 UTC, an internal host attempted to open a URL that was already on the firewall blocklist. The connection was blocked, and no successful outbound session was established.

## Incident Details

| Field | Value |
|-------|-------|
| Internal IP | 10.20.2.17 |
| Destination IP | 67.199.248.11 |
| URL | hxxps[://]bit[.]ly/3sHkX3da12340 |
| Destination Port | 80 (HTTP) |
| Source Port | 34257 |
| Protocol | TCP |
| Firewall Action | Blocked |

## Investigation

1. Reviewed the firewall alert for blocked access to a blacklisted URL.
2. Confirmed URL reputation in VirusTotal.
3. Queried Splunk logs for additional events to the same destination IP.

## Findings

- One blocked event was found for the source host and destination IP.
- VirusTotal marked the URL/IP as malicious.
- No successful connection to the destination IP was found in logs.

## Evidence

### SOC Dashboard Overview
<p align="center">
  <img src="./screenshots/dashboard.png" alt="SOC Dashboard" width="800"/>
</p>

### Alert Details
<p align="center">
  <img src="./screenshots/alart.png" alt="Alert Details" width="800"/>
</p>

### VirusTotal Scan
<p align="center">
  <img src="./screenshots/virus-total.png" alt="VirusTotal Scan" width="800"/>
</p>

### Splunk Search Results
<p align="center">
  <img src="./screenshots/splunk.png" alt="Splunk Search Results" width="800"/>
</p>

## Action Taken

The alert was classified as a true positive blocked attempt. No containment or recovery action was required because the connection did not succeed.

## Closure

Incident closed as resolved. Records are kept for tracking and audit.
