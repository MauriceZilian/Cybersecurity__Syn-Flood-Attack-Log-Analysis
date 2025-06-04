# 🛡️ Incident Report: SYN Flood Attack (Simulated Log Analysis)

This report analyzes a simulated denial-of-service (DoS) incident based on a SYN flood attack. The analysis is structured and based on raw log data to demonstrate practical log interpretation skills and familiarity with network-based attacks.

---

## 📘 Summary

At approximately **14:32 local time**, the web server at **192.168.1.10** began experiencing service disruptions. Users reported timeout errors when attempting to access web applications. An inspection of the captured log data using `tcpdump` revealed a high volume of **SYN packets** from a single external IP address **(202.0.112.0)** targeting **port 80 (HTTP)**.

---

## 🔍 Attack Type

**Attack vector:** TCP SYN Flood  
**Source IP:** `202.0.112.0`  
**Target IP:** `192.168.1.10`  
**Target port:** `80` (HTTP)  
**Protocol:** TCP  
**Impact:** Service unavailability, resource exhaustion on target system

---

## 🧪 Log Interpretation (Key Indicators)

### Log Snippet:

14:32:10.121234 IP 202.0.112.0.45321 > 192.168.1.10.80: Flags [S], seq 100123, win 64240, length 0  
14:32:10.121245 IP 202.0.112.0.45322 > 192.168.1.10.80: Flags [S], seq 100124, win 64240, length 0
...


### Observations:
- **Repeated SYN packets** from the same IP address, using different source ports
- **No corresponding ACK packets**, meaning the handshake was never completed
- **Extremely high frequency** of SYN packets within milliseconds

### Interpretation:
This pattern matches a **SYN flood attack**, where the attacker sends many incomplete TCP handshakes to exhaust server resources. The server allocates memory for each handshake attempt and waits for the final ACK that never arrives.

---

## 🛠️ Suggested Mitigation

1. **Enable SYN cookies** on the web server to reduce resource exhaustion.
2. **Rate-limit SYN packets** using firewall rules (e.g., `iptables` or similar tools).
3. **Detect anomalies** with an IDS/IPS (e.g., Snort, Suricata).
4. **Block offending IPs** temporarily via firewall or automated detection scripts.
5. **Log correlation** via SIEM tools for long-term visibility.

---

## 🎯 Lessons Demonstrated

- Interpreting raw TCP packet data
- Understanding the TCP handshake process
- Recognizing symptoms of SYN flooding
- Proposing practical mitigation strategies

---

📝 *This report was created as part of a personal cybersecurity learning project. The logs are simulated and were designed to mirror real-world analysis challenges in incident response.*

