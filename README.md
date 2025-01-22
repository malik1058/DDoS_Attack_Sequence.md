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

%% - **Attacker**: Controls the Botnet and initiates the DDoS attack by sending commands to flood the Webserver with traffic.
%% - **Botnet**: A network of compromised devices that sends large volumes of malicious traffic to the Webserver.
%% - **Webserver**: Receives the flood of traffic, attempts to process it, but is overwhelmed by the sheer volume and eventually crashes or becomes unresponsive.
%% - **Firewall**: Inspects incoming traffic for malicious patterns and blocks some of the requests, but cannot fully stop the DDoS attack due to the scale of traffic.
