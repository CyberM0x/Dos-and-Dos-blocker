# DoS and DoS Blocker (Python + Scapy)

Educational project demonstrating a basic Denial-of-Service (DoS) attack simulation and a defensive DoS detection and blocking mechanism using packet rate analysis and iptables.

## Files

```
Firewalls/
├── DOS.py
└── DOS-blocker.py
```

## DOS-blocker.py

Real-time network traffic monitor that detects high packet rates from a single IP address and blocks it using iptables.

### Logic

- Sniffs IP packets using Scapy
- Counts packets per source IP
- Calculates packets per second
- Blocks IPs exceeding a defined threshold

### Configuration

THRESHOLD = 40

Maximum allowed packets per second per IP.

### Requirements

- Linux
- Python 3
- Root privileges
- scapy
- iptables

Install dependency:

```pip install scapy```

### Run

```sudo python3 DOS.py```


## Notes

- Scripts must be executed in a controlled environment
- Blocked IPs are added using:

```iptables -A INPUT -s <ip> -j DROP```

View rules:

```iptables -L -n```

Flush rules (use with caution):

```iptables -F```


## Disclaimer

For educational and defensive security research only.
Do not use on production or unauthorized networks.

## Author

CyberM0x



