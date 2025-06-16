# 📑 Incident Report – SYN-Flood-Angriff (simuliert)

## 🕵️ Vorfallbeschreibung

Am 04.06.2025 wurde ein ungewöhnlicher Netzwerkvorfall festgestellt:  
Ein Webserver reagierte nicht mehr auf Anfragen, Clients erhielten **Verbindungszeitüberschreitungen**.

## 🔍 Erste Analyse

Die Untersuchung der Netzwerkprotokolle ergab eine ungewöhnlich hohe Anzahl eingehender TCP-SYN-Pakete von einer einzelnen Quelle:  
**IP-Adresse: 202.0.112.0**

### 🧪 Technische Details

- Der Angriffstyp wurde als **SYN-Flood** klassifiziert.
- Der betroffene Server versuchte, TCP-Verbindungen aufzubauen, erhielt jedoch **keine finalen ACK-Pakete**.
- Das führte zur Erschöpfung der **Connection Queue** des Servers (Backlog), wodurch reguläre Anfragen nicht mehr bearbeitet werden konnten.

## 📈 Analyse des Logs (Auszug)

Beispielhafte Einträge aus `simulated_log.md`:

14:01:12.123456 IP 202.0.112.0.54321 > 192.168.1.10.80: Flags [S], seq 1234567890, win 64240  
14:01:12.123789 IP 202.0.112.0.54322 > 192.168.1.10.80: Flags [S], seq 1234567891, win 64240  
14:01:12.124123 IP 202.0.112.0.54323 > 192.168.1.10.80: Flags [S], seq 1234567892, win 64240  
...


**Legende:**
- `Flags [S]` = SYN-Paket (Verbindungsanfrage)
- Keine Antwort vom Client → keine vollständige TCP-Session

## 📉 Auswirkungen

- Webserver unter hoher Last, reagierte nicht mehr
- Verfügbarkeit des Dienstes wurde massiv beeinträchtigt
- Potenzielle Reputations- und Geschäftsschäden

## 🛡️ Sofortmaßnahmen

- Temporäres Blockieren der IP-Adresse (Firewall)
- Aktivierung von **SYN-Cookies**
- Reduktion des TCP-Timeouts für halb-offene Verbindungen

## ✅ Langfristige Maßnahmen

- Einführung von **Rate Limiting** für eingehende Verbindungen
- Einsatz eines Intrusion Prevention Systems (IPS)
- Monitoring-Regel zur Detektion ungewöhnlicher SYN-Raten
- Verbesserung der Dokumentation und Playbooks für Incident Response

## 📌 Fazit

Dieser simulierte Angriff zeigt, wie durch einfache SYN-Flood-Techniken kritische Systeme lahmgelegt werden können.  
