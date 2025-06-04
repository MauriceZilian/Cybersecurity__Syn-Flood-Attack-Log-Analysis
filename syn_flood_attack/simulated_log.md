# 📄 Simulated TCP Dump Log — SYN Flood Attack

This is a simplified and human-readable simulation of a network capture log showing a SYN flood attack coming from a single IP address. The goal is to demonstrate how such an attack might appear in raw log data (e.g., from tcpdump).

---

## 🕵️ Log Data

14:32:10.121234 IP 202.0.112.0.45321 > 192.168.1.10.80: Flags [S], seq 100123, win 64240, length 0
#14:32:10.121245 IP 202.0.112.0.45322 > 192.168.1.10.80: Flags [S], seq 100124, win 64240, length 0
#14:32:10.121255 IP 202.0.112.0.45323 > 192.168.1.10.80: Flags [S], seq 100125, win 64240, length 0
#14:32:10.121264 IP 202.0.112.0.45324 > 192.168.1.10.80: Flags [S], seq 100126, win 64240, length 0
#14:32:10.121273 IP 202.0.112.0.45325 > 192.168.1.10.80: Flags [S], seq 100127, win 64240, length 0
#14:32:10.121283 IP 202.0.112.0.45326 > 192.168.1.10.80: Flags [S], seq 100128, win 64240, length 0
...
#14:32:10.122000 IP 202.0.112.0.45390 > 192.168.1.10.80: Flags [S], seq 100192, win 64240, length 0


---

## 🧾 Legend

- **IP 202.0.112.0** = Malicious actor (attacker)
- **IP 192.168.1.10** = Target server
- **Port 80** = HTTP web server
- **Flags [S]** = SYN flag set (first step in TCP handshake)
- **No ACKs** = The attacker does **not** complete the handshake
- **High frequency** = Indicates flooding behavior

---

## 🧠 Notes

- This is a classic **SYN flood attack**: attacker sends many SYN packets without completing the handshake.
- The target system keeps waiting for the final ACK (which never comes), using up memory and connection slots.
- This can crash or freeze the target service over time (DoS condition).
