# 📊 Simulierter Netzwerk-Log – SYN-Flood-Angriff

Dieser simulierte Log zeigt das Verhalten eines SYN-Flood-Angriffs gegen einen Webserver unter der Adresse `192.168.1.10`.  
Der Angreifer nutzt die IP `202.0.112.0`, um massenhaft Verbindungsanfragen ohne Abschluss des Handshakes zu senden.

### 📂 Beispiel-Logeinträge

14:01:12.123456 IP 202.0.112.0.54321 > 192.168.1.10.80: Flags [S], seq 1234567890, win 64240  
14:01:12.123789 IP 202.0.112.0.54322 > 192.168.1.10.80: Flags [S], seq 1234567891, win 64240  
14:01:12.124123 IP 202.0.112.0.54323 > 192.168.1.10.80: Flags [S], seq 1234567892, win 64240  
14:01:12.124456 IP 202.0.112.0.54324 > 192.168.1.10.80: Flags [S], seq 1234567893, win 64240  
14:01:12.124789 IP 202.0.112.0.54325 > 192.168.1.10.80: Flags [S], seq 1234567894, win 64240  


### 📘 Erläuterung

- `Flags [S]`: TCP-SYN-Paket → Verbindungsanfrage
- `seq`: Startwert für TCP-Sequence-Nummer
- `win`: Fenstergröße des Clients
- Kein zugehöriges ACK = keine vollständige Verbindung

**Hinweis:** In einem realen Log könnten auch SYN/ACK-Antworten des Servers zu sehen sein – diese fehlen hier bewusst, um den Angriff klar zu zeigen.


