# Nmap Notes

This repository contains my personal learning notes and hands-on practice
with Nmap, focusing on host discovery, port scanning, and service enumeration
from an ethical hacking perspective.

These notes are based on practical testing, documentation, and controlled labs.
No unauthorized scanning is performed.

## Topics Covered
- Host discovery (ICMP, ARP, TCP probes)
- Port scanning techniques
- Service and version detection
- Common Nmap flags and when to use them
- Interpreting scan results

## Why Nmap?
Nmap is a fundamental reconnaissance tool used by penetration testers
to identify live hosts, open ports, and exposed services before exploitation.

# Host Discovery

Host discovery is the process of identifying whether a target system
is alive before performing port scans.

## How Nmap Determines a Host Is Alive

A host is considered **up** when Nmap receives a response to its probes.

Example output:
Host is up (0.12s latency)

## ICMP

ICMP (Internet Control Message Protocol) is used for network diagnostics.

Nmap commonly uses ICMP Echo Requests (ping) to check if a host is alive.

Example:
nmap -sn scanme.nmap.org

If ICMP is blocked by a firewall, the host may appear down even when it is online.
This means the target responded within 0.12 seconds.

## Basic Nmap Commands

### Ping Scan (Host Discovery Only)
nmap -sn target_ip

Purpose:
Checks which hosts are alive without scanning ports.

---

### Skip Host Discovery
nmap -Pn scanme.nmap.org

Purpose:
Assumes the host is up. Useful when ICMP is blocked.

---

### Fast Scan
nmap -F scanme.nmap.org

Purpose:
Scans the most common ports quickly.

## What Does "Noisy" Mean in Nmap?

A noisy scan generates a lot of network traffic and is easy
for firewalls and intrusion detection systems (IDS) to detect.

Example:
nmap -A scanme.nmap.org

This enables OS detection, version detection, script scanning,
and traceroute — all at once — making it highly detectable.

## Why Scans Can Fail (scanme.nmap.org)

Nmap's scanme.nmap.org is intentionally rate-limited and protected.

Reasons scans may fail:
- Too many requests in a short time
- Aggressive scans (-A)
- IDS blocking repeated probes



## Learning Goal
To build a strong reconnaissance mindset and understand how network
visibility works in real-world environments.
