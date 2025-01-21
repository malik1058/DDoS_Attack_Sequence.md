# DDoS_Attack_Sequence.md
```mermaid
sequenceDiagram
    participant Attacker as Attacker
    participant Botnet as Botnet (Compromised Devices)
    participant Firewall as Firewall
    participant Webserver as Webserver

    %% Step 1: Attacker instructs Botnet
    Attacker->>Botnet: Command to start DDoS attack (Flood Webserver)
    Note right of Attacker: The Attacker controls the Botnet and instructs them to send traffic to the target server (Webserver).

    %% Step 2: Botnet launches the attack
    Botnet->>Webserver: Send massive traffic (Flood of requests)
    Note right of Botnet: The Botnet consists of many compromised devices (bots) which generate a high volume of traffic to overwhelm the Webserver.

    %% Step 3: Webserver receives requests
    Webserver->>Firewall: Forward requests for filtering (Pass traffic through Firewall)
    Note right of Webserver: The Webserver receives the traffic, but first checks the Firewall for any malicious requests.

    %% Step 4: Firewall inspects the traffic
    Firewall->>Firewall: Inspect incoming traffic for DDoS signatures
    Note right of Firewall: The Firewall inspects each incoming request for patterns or signatures that match DDoS attack characteristics.

    %% Step 5: Firewall tries to block malicious traffic
    Firewall-->>Webserver: Block some traffic or allow based on rules
    Note right of Firewall: The Firewall filters out some malicious requests based on its security rules (rate limiting, IP blocking, etc.).

    %% Step 6: Webserver gets overwhelmed
    Webserver->>Webserver: Start dropping requests due to overload
    Note right of Webserver: Despite the Firewall's filtering, the Webserver is still overwhelmed by the sheer volume of requests, which leads to performance degradation.

    %% Step 7: Webserver alerts Firewall
    Webserver-->>Firewall: Alert: Server is overwhelmed, continuing attack
    Note right of Webserver: The Webserver sends an alert to the Firewall indicating that the server is becoming unresponsive due to the flood of traffic.

    %% Step 8: Firewall continues blocking traffic
    Firewall->>Firewall: Adjust rules to block more traffic
    Note right of Firewall: The Firewall adjusts its rules to block more malicious traffic, but the attack is still ongoing.

    %% Step 9: Webserver crashes or becomes unresponsive
    Webserver->>Webserver: Server crashes or becomes unresponsive
    Note right of Webserver: The Webserver is eventually overwhelmed to the point of crashing or becoming unresponsive, completing the DDoS attack.

    %% Final note: Overall impact
    Note right of Webserver: The goal of the attacker is to exhaust the resources of the Webserver, causing downtime or service disruption.
