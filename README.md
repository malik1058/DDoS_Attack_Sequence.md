# DDoS_Attack_Sequence.md
```mermaid
sequenceDiagram
    participant Attacker as Attacker
    participant Botnet as Botnet
    participant Firewall as Firewall
    participant Webserver as Webserver

    Attacker->>Botnet: Command to send attack traffic
    Botnet->>Webserver: Flood with requests
    Webserver->>Firewall: Forward traffic for filtering
    Firewall->>Firewall: Inspect traffic
    Firewall-->>Webserver: Block some malicious requests
    Webserver->>Webserver: Overwhelmed by remaining traffic
    Webserver-->>Firewall: Alert: Server is overwhelmed
    Firewall->>Webserver: Continue blocking more traffic
    Webserver->>Webserver: Server crashes or becomes unresponsive
