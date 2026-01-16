DoS Detection and Blocking with Python & Scapy

This repository contains two Python scripts demonstrating a basic Denial-of-Service (DoS) simulation and a real-time DoS detection and blocking mechanism using packet rate analysis and Linux iptables.

⚠️ Educational use only
These scripts are intended for learning, testing, and defensive cybersecurity research in controlled environments.

Project Structure
Firewalls/
├── DOS.py              # DoS traffic generator (attacker simulation)
└── DOS-blocker.py      # DoS detection & automatic IP blocking

1. DOS-blocker.py — DoS Detection & Blocking
Description

This script monitors incoming IP packets in real time.
If a source IP exceeds a defined packet rate threshold, it is automatically blocked using iptables.

How It Works

Captures network packets using Scapy

Counts packets per source IP

Calculates packets per second

If the rate exceeds the threshold:

The IP is blocked via iptables

The IP is stored to prevent duplicate rules

Key Features

Real-time traffic monitoring

Packet rate–based DoS detection

Automatic firewall rule insertion

Uses defaultdict for efficient counting

Configuration
THRESHOLD = 40  # Maximum packets per second per IP


Adjust this value based on your network capacity.

Requirements

Linux system

Python 3

Root privileges

Scapy

iptables

Install dependencies:

pip install scapy

Usage
sudo python3 DOS-blocker.py


You must run the script as root, otherwise it will exit.

Example Output
THRESHOLD: 40
Monitoring network traffic...
Blocking IP: 192.168.1.63, packet_rate: 68.04

2. DOS.py — DoS Traffic Generator (Test Script)
Description

This script simulates a basic DoS attack by rapidly sending TCP packets to a target IP address over a specified network interface.

It is designed only for testing the detection script.

How It Works

Crafts raw Ethernet/IP/TCP packets

Sends packets continuously for a given duration

Stops after reaching the packet limit or time limit

Configuration
TARGET_IP = "192.168.1.66"   # Target machine
INTERFACE = "eno1"           # Network interface
NUM_PACKETS = 100            # Max packets
DURATION = 5                 # Seconds


⚠️ Ensure the target IP is your own test machine.

Usage
sudo python3 DOS.py

Important Notes

These scripts must be run on a controlled lab network

Blocking is done using:

iptables -A INPUT -s <IP> -j DROP


Blocked IPs persist until rules are manually removed

To view rules:

iptables -L -n


To flush rules (DANGEROUS on production systems):

iptables -F

Security Disclaimer

This project is provided for educational and defensive purposes only.
The author is not responsible for misuse, illegal activity, or damage caused by these scripts.

Author

CyberM0x
Cybersecurity & Software Engineering Student
