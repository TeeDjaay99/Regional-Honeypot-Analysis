# Regional-Honeypot-Analysis

Regional Honeypot Analysis

Stockholm (eu-north-1) vs Virginia (us-east-1)

A 48-hour comparative study of global cyber threat patterns

Author: Tony Jokiranta |[LinkedIn](https://www.linkedin.com/in/tonyjokiranta/) | [Portfolio](https://www.tonyjokirantaportfolio.com/)

## Setup Overview
| Component            | Details                                                            |
| -------------------- | ------------------------------------------------------------------ |
| **Platform**         | AWS EC2 (t2.micro Virginia, t3.micro Stockholm)                    |
| **Honeypot**         | Cowrie SSH/Telnet (Docker)                                         |
| **OS**               | Ubuntu 24.04 LTS                                                   |
| **Monitored Ports**  | 22 (SSH), 23 (Telnet), 3306 (MySQL), 5432 (PostgreSQL), 3389 (RDP) |
| **Duration**         | 48 hours per region                                                |
| **Monitoring Tools** | tcpdump, CloudWatch, AbuseIPDB, VirusTotal                         |

---

## Key Metrics Comparison
| Metric              | Stockholm | Virginia | Difference |
| ------------------- | --------- | -------- | ---------- |
| SSH Connections     | 0         | 57       | +∞         |
| Unique Attacker IPs | ~60       | 482      | +703%      |
| Telnet Packets      | 407       | 751      | +84.5%     |
| RDP Packets         | 316       | 498      | +58%       |
| Total Packets       | 864       | 1,416    | +64%       |

**Finding:** US region received 8× more attackers and far more active exploit attempts.

---

## Top Attacker Origins (Virginia Server)
* China - 20%
* United States - 20%
* Germany - 20%
* South Korea, France, UK, Taiwan - 10% each

Mix of cloud infrastructure (DigitalOcean, Palo Alto Networks, Google Cloud Platform) and home ISPs.

---

## Notable Discovery
**IP 198.235.24.90 (Palo Alto Networks)**
* 35,000 abuse reports but 0% malicious (whitelisted) on AbuseIPDB.
* Flagged by 7/95 security vendors on VirusTotal.
  
**Lesson:** “Trusted” infrastructure can be used maliciously — reputation-based defenses aren not perfect.

---

## IoT Botnet Dominance
* Telnet attacks (53%) > SSH (6%).
* Common credentials: ubnt, raspberry, orangepi, admin.
* IoT devices are prime botnet targets.

---

## Lessons Learned 
* Geographic location influences attack volume.
* US cloud servers attract higher attacker engagement.
* IoT devices dominate modern automated attacks.
* IP reputation systems can contradict each other.
* Real Swedish attacks are targeted, not opportunistic.

---

## Skills demonstrated and learned
* AWS Cloud & EC2 Management.
* Basic Docker and Linux.
* Basic log analysis.
* Threat Intelligence (AbuseIPDB, VirusTotal).
* Report writing.

---

## Summary
Virginia was hit harder, but Sweden remains a real target for advanced attack campaigns, my honeypot captured the noise and the bots, not the sopisticated attacks.
  
