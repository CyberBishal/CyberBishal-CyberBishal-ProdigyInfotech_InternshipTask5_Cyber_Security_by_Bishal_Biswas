# CyberBishal-CyberBishal-ProdigyInfotech_InternshipTask5_Cyber_Security_by_Bishal_Biswas
 Network Packet Analyzer: TASK 5 I have developed a packet sniffer tool that captures and analyzes network packets. Display relevant information such as source and destination IP addresses, protocols, and payload data. Ensure the ethical use of the tool for educational purposes.
 So, Here is my Project watch below :

from scapy.all import *

def packet_callback(packet):
    if IP in packet:
        src_ip = packet[IP].src
        dst_ip = packet[IP].dst
        proto = packet[IP].proto

        if proto == 6 and TCP in packet:
            payload = packet[TCP].payload
            print(f"TCP Packet - Source: {src_ip}, Destination: {dst_ip}, Payload: {payload}")
        elif proto == 17 and UDP in packet:
            payload = packet[UDP].payload
            print(f"UDP Packet - Source: {src_ip}, Destination: {dst_ip}, Payload: {payload}")
        elif proto == 1 and ICMP in packet:
            payload = packet[ICMP].payload
            print(f"ICMP Packet - Source: {src_ip}, Destination: {dst_ip}, Payload: {payload}")

# Start capturing packets on the network interface
sniff(prn=packet_callback, store=0)

 
