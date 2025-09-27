# OT-Network-Protocols
### I will be using this Repo to document and share Network Protocols that I will be studying and practicing. The focus will be on discussing Operation Technology (OT) Related Network Protocol.
# A Guide to Operational Technology (OT) Network Protocols

This document serves as a reference guide to many of the common network protocols encountered in Operational Technology (OT) and Industrial Control System (ICS) environments. Understanding these protocols, their vendors, transport layers, and default ports is crucial for network design, security monitoring, and firewall configuration.

> ### ⚠️ A Note on Common Ports
> You will notice that certain port numbers appear frequently. This is often because systems support common protocols for interoperability, even if their primary, proprietary protocol uses a different port.
> * **TCP/502:** The registered port for **Modbus**. Many systems support Modbus for broad compatibility.
> * **TCP/102:** The port for ISO-TSAP, famously used by **Siemens S7Comm**.
> * **UDP/161:** The standard port for **SNMP**, which is widely used for network device monitoring and discovery.
> * **TCP/UDP/44818:** The port for **EtherNet/IP** and **CIP**, common in Rockwell Automation environments.

---

## Foundational & Widely-Used OT Protocols

These protocols are foundational to industrial communication and are supported by a wide range of vendors.

| Protocol | Vendor(s) | Transport | Port(s) | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Modbus** | Schneider (Origin), Multi-Vendor | TCP | `502` | One of the oldest and most widely used protocols due to its simplicity. |
| **S7Comm / S7Comm Plus** | Siemens | TCP | `102` | Used for communication with Siemens SIMATIC S7 series PLCs. |
| **EtherNet/IP (ENIP)** | Rockwell / ODVA | TCP & UDP | `44818` | Adapts the Common Industrial Protocol (CIP) for Ethernet. |
| **DNP3** | Multi-Vendor | TCP, UDP | `20000` | Common in utilities (electric, water) for SCADA communication. |
| **OPC-DA** | Multi-Vendor | TCP | `135` | Legacy standard using DCOM. Uses dynamic high ports after initial connection. |
| **OPC-UA** | Multi-Vendor | TCP | `4840`, `4843` | The modern, secure, and platform-independent successor to OPC-DA. |

---

## Vendor-Specific Protocols

This section lists protocols primarily associated with a single major vendor.

### Siemens

| Protocol/System | Transport | Port(s) | Notes |
| :--- | :--- | :--- | :--- |
| **PROFINET DCP** | UDP | `34962` | Discovery and Configuration Protocol. |
| **PROFINET Real-Time**| Ethernet | N/A | Operates at Layer 2 for deterministic performance; does not use IP/UDP ports. |
| **GOOSE** | Ethernet | N/A | IEC-61850 protocol for substation automation. Layer 2, no ports. |
| **DIGSI 4 / 5** | TCP | `502` | Engineering software for SIPROTEC relays; often uses Modbus for comms. |

### Rockwell Automation (Allen-Bradley)

| Protocol/System | Transport | Port(s) | Notes |
| :--- | :--- | :--- | :--- |
| **CIP (Control & Info)** | TCP | `44818` | The core protocol for EtherNet/IP (explicit messaging). |
| **PCCC** | TCP | `44818` | Legacy protocol, often encapsulated within CIP for older PLCs. |
| **FactoryTalk RNA** | UDP | `2222` | Used for Rockwell Network Agent services. |

### Schneider Electric

| Protocol/System | Transport | Port(s) | Notes |
| :--- | :--- | :--- | :--- |
| **Modbus Schneider** | TCP | `502` | Schneider's implementation of the Modbus protocol. |
| **Triconex TSAA** | TCP | `102` | Protocol for Triconex safety instrumented systems. |
| **PowerLogic Discovery** | TCP | `102` | Used for discovering PowerLogic energy meters. |

### ABB

| Protocol/System | Transport | Port(s) | Notes |
| :--- | :--- | :--- | :--- |
| **Totalflow** | TCP | `502` | Protocol for ABB's line of flow computers. |
| **RNRP** | TCP | `102` | Redundant Network Routing Protocol. |
| **Symphony Plus** | TCP | `102` | Protocol for ABB's Symphony Plus DCS. |

### Emerson

| Protocol/System | Transport | Port(s) | Notes |
| :--- | :--- | :--- | :--- |
| **DeltaV** | TCP | `502` | Internal protocols for the DeltaV DCS; supports Modbus. |
| **Ovation** | TCP | `102` | Suite of protocols for the Ovation DCS. |
| **ROC Plus** | TCP | `102` | For Remote Operations Controller (ROC) family. |

### General Electric (GE)

| Protocol/System | Transport | Port(s) | Notes |
| :--- | :--- | :--- | :--- |
| **GE SRTP** | UDP | `161` | Service Request Transfer Protocol, often used with SNMP. |
| **GE-EGD** | UDP | `34962` | Ethernet Global Data, for high-speed data exchange between PLCs. |
| **GE SDI (MarkVie)** | TCP | `502` | For communication with MarkVie turbine control systems. |

---

## Network Management, IT, & Utility Protocols

These protocols support the underlying network infrastructure and are often found in both IT and OT environments.

| Protocol | Transport | Port(s) | Use Case in OT |
| :--- | :--- | :--- | :--- |
| **SNMP** | UDP | `161`, `162` | Monitoring network devices (switches, routers, firewalls). |
| **LLDP / CDP** | Ethernet | N/A | Layer 2 discovery protocols for mapping network topology. |
| **FTP / TFTP** | TCP / UDP | `20`,`21` / `69` | Transferring firmware, configurations, and project files. |
| **SSH / Telnet** | TCP | `22` / `23` | Secure/insecure command-line access to devices. |
| **HTTP / HTTPS** | TCP | `80` / `443`| Accessing embedded web interfaces on modern devices. |
| **RDP** | TCP | `3389` | Remote access to Windows-based HMIs and engineering stations. |
| **DHCP** | UDP | `67`, `68` | Dynamic IP address assignment (use with caution in OT). |
| **NTP** | UDP | `123` | Time synchronization, critical for sequence-of-events analysis. |

## OT Network Protocols
| Protocol/System                             | Vendor         | Transport Layer Protocol | Port Number(s) |
|---------------------------------------------|---------------|--------------------------|----------------|
| ABB DMS System                             | ABB           | TCP                      | 502            |
| ABB HC800 (Infinet)                        | ABB           | TCP                      | 502            |
| ABB Melody                                 | ABB           | TCP                      | 502            |
| AMS (ADS)                                  | Beckhoff      | UDP                      | 502            |
| Bailey                                     | ABB           | TCP                      | 502            |
| BSAP                                       | Bristol       | UDP                      | 502            |
| CAPWAP                                     | -             | UDP                      | 5246, 5247     |
| Caterpillar AHS                            | Caterpillar   | TCP                      | 502            |
| CC-Link IE Field                           | CC-Link IE    | UDP                      | 34962          |
| CIP                                        | Rockwell      | TCP                      | 44818          |
| Cisco Discovery Protocol (CDP)             | Cisco         | UDP                      | 161            |
| Citect HMI                                 | -             | TCP                      | 502            |
| ClearSCADA ViewX                           | AVEVA         | TCP                      | 502            |
| CODESYS V2                                 | CODESYS       | TCP                      | 502            |
| CODESYS V3                                 | CODESYS       | TCP                      | 502            |
| Control Technologies Inc. (CTI)            | CTI           | UDP                      | 502            |
| CPHA (Checkpoint High Availability)        | Checkpoint    | UDP                      | 502            |
| COTP                                       | -             | TCP                      | 102            |
| CSPv4                                      | -             | UDP                      | 161            |
| Cygnet SCADA                               | Cygnet        | TCP                      | 502            |
| DACP                                       | Willowglen    | UDP                      | 502            |
| DeltaV                                     | Emerson       | TCP                      | 502            |
| DHCP                                       | -             | UDP                      | 67, 68         |
| Digi RealPort                              | Digi          | TCP                      | 502            |
| DIGSI4 (SIPROTEC 4)                        | Siemens       | TCP                      | 502            |
| DIGSI5                                     | Siemens       | TCP                      | 502            |
| DLMS COSEM                                 | -             | TCP                      | 4059           |
| DNP3                                       | -             | TCP                      | 20000          |
| DPI (over PCCC)                            | Rockwell      | TCP                      | 44818          |
| E-Terra                                    | Alstom        | UDP                      | 502            |
| E-Terra Workstation                        | -             | TCP                      | 502            |
| ENIP                                       | Rockwell      | UDP                      | 44818          |
| EtherCAT                                   | Beckhoff      | UDP                      | 34962          |
| Ethernet POWERLINK                         | -             | UDP                      | 34962          |
| ITEPM (Endpoint Mapper)                    | -             | UDP                      | 161            |
| ETHERNET/IP                                | -             | UDP                      | 44818          |
| FINS                                       | Omron         | UDP                      | 9600           |
| FactoryTalk RNA                            | -             | UDP                      | 2222           |
| FL-net                                     | -             | UDP                      | 102            |
| All JEMA                                   | -             | UDP                      | 502            |
| FI-net Toyoda                              | Toyota        | UDP                      | 502            |
| FOCAS                                      | Fanuc Robotics| UDP                      | 8193           |
| Foundation Fieldbus (FF)                   | -             | UDP                      | 1502           |
| Foxboro LLC                                | Foxboro       | TCP                      | 502            |
| Foxboro RTV                                | Foxboro       | TCP                      | 502            |
| FTP                                        | -             | TCP                      | 20, 21         |
| SEL                                        | Schweitzer    | UDP                      | 161            |
| Gaz Modem                                  | Plum          | UDP                      | 502            |
| GE Bentley Nevada (BNC3500)                | GE            | TCP                      | 502            |
| GE PAC8000 (AXE)                           | GE            | TCP                      | 502            |
| GE QuickPanel (TRAPI+HTTP)                 | GE            | TCP                      | 502            |
| GE SDI (MarkVie)                           | GE            | TCP                      | 502            |
| GE SDI Classic (MarkVie)                   | GE            | TCP                      | 502            |
| GE SRTP                                    | GE            | UDP                      | 161            |
| GE-ALM                                     | GE            | UDP                      | 161            |
| GE-EGD                                     | GE            | UDP                      | 34962          |
| GE-EGD-CMP                                 | GE            | UDP                      | 34962          |
| GE-iFix                                    | GE            | TCP                      | 502            |
| GOOSE (IEC-61850)                          | IEC           | UDP                      | 102            |
| HART-IP                                    | -             | UDP                      | 5094           |
| HiDiscovery                                | Hirschmann    | UDP                      | 161            |
| Honeywell C200 - FTEBCIP                   | Honeywell     | UDP                      | 502            |
| Honeywell EpicMo (C300 Management)         | Honeywell     | UDP                      | 502            |
| Honeywell Experion - CeeNTComm (C300, EHPM)| Honeywell     | UDP                      | 502            |
| Honeywell Firewall CF9                     | Honeywell     | UDP                      | 502            |
| Hot Standby Router Protocol (HSRP)         | -             | UDP                      | 1985           |
| HP Switch                                  | HP            | UDP                      | 161            |
| HTTP                                       | -             | TCP                      | 80             |
| Keyence Logger                              | Keyence       | TCP                      | 102            |
| Knapp                                       | Knapp         | TCP                      | 102            |
| Linux High Availability                     | Linux         | TCP                      | 102            |
| LLDP                                        | -             | Ethernet                 | N/A            |
| MasterBus 300                               | ABB           | TCP                      | 102            |
| Matrikon OPC Tunneler                       | Matrikon      | TCP                      | 135            |
| MaxDNA (maxNET)                             | Valmet        | TCP                      | 102            |
| MDLC data                                   | Motorola      | TCP                      | 102            |
| MDLC management                             | Motorola      | TCP                      | 102            |
| Melsec                                      | Mitsubishi    | TCP                      | 102            |
| Melsoft                                     | Mitsubishi    | TCP                      | 102            |
| Microsoft DCE RPC                           | Microsoft     | TCP                      | 135            |
| ABB DCS Service Manager                     | Microsoft     | TCP                      | 135            |
| CIFS (SMB)                                  | Microsoft     | TCP                      | 445            |
| NTLMSSP (Auth protocol)                     | Microsoft     | TCP                      | 445            |
| RDP                                         | Microsoft     | TCP                      | 3389           |
| SAMR                                        | Microsoft     | TCP                      | 445            |
| Mitsubishi GOT                              | Mitsubishi    | TCP                      | 102            |
| Modbus                                      | -             | TCP                      | 502            |
| Modsoft                                     | Schneider     | TCP                      | 502            |
| Modbus Concept                              | Schneider     | TCP                      | 502            |
| Modbus Eltec                                | Eltec         | TCP                      | 502            |
| Modbus Execload                             | -             | TCP                      | 502            |
| Modbus GE Enervista                         | GE            | TCP                      | 502            |
| Modbus ScadaPack                            | ScadaPack     | TCP                      | 502            |
| Modbus Schneider                            | Schneider     | TCP                      | 502            |
| Modbus Twinsoft                             | Twinsoft      | TCP                      | 502            |
| Modbus Xinje                                | Xinje         | TCP                      | 502            |
| MQTT                                        | -             | TCP                      | 1883           |  
| NetBIOS Browser (UDP 138)                   | -             | UDP                      | 138            |
| NetBIOS Datagram Service                    | -             | UDP                      | 137            |
| Odeq                                        | Yokogawa      | TCP                      | 102            |
| Omniflow Flow Computer                      | Omniflow      | TCP                      | 102            |
| OPC-DA                                      | -             | TCP                      | 135            |
| OPC-UA                                      | -             | TCP                      | 4840-4843      |
| Ovation                                     | Emerson       | TCP                      | 102            |
| Ovation ADMD                                | Emerson       | TCP                      | 102            |
| Ovation Alarm                               | Emerson       | TCP                      | 102            |
| Ovation DBXmit                              | Emerson       | TCP                      | 102            |
| Ovation PTEdit                              | Emerson       | TCP                      | 102            |
| OvationRPC                                  | Emerson       | TCP                      | 102            |
| P2                                          | Siemens       | TCP                      | 102            |
| PCCC                                        | Rockwell      | TCP                      | 44818          |
| PCWin                                       | Toyoda        | TCP                      | 102            |
| PI1                                         | OSISoft       | TCP                      | 102            |
| PI3                                         | OSISoft       | TCP                      | 102            |
| POP3                                        | -             | TCP                      | 110            |
| Portwell                                    | Portwell      | TCP                      | 102            |
| PowerLogic Discovery                        | Schneider     | TCP                      | 102            |
| ProConoS (TCP 20547)                        | Phoenix Contact | TCP                    | 20547          |
| Profinet DCP                                | -             | UDP                      | 34962          |
| Profinet I/O                                | -             | UDP                      | 34962          |
| Profinet Real-Time                          | -             | UDP                      | 34962          |
| Prosoft Discovery                           | -             | UDP                      | 161            |
| PRP                                         | -             | UDP                      | 161            |
| PTP                                         | -             | UDP                      | 161            |
| Radius                                      | -             | UDP                      | 1812           |
| Redlion Crimson                             | Redlion       | TCP                      | 102            |
| Redlion NView-2 Discovery                   | Redlion       | UDP                      | 161            |
| RNRP                                        | ABB           | TCP                      | 102            |
| ROC Plus                                    | Emerson       | TCP                      | 102            |
| RTCP                                        | -             | UDP                      | 161            |
| S7Comm                                      | Siemens       | TCP                      | 102            |
| S7Comm Plus                                 | Siemens       | TCP                      | 102            |
| Sattbus                                     | -             | Serial                   | N/A            |
| SBUS                                        | SAIA          | Serial                   | N/A            |
| Schneider NetManage                         | Schneider     | TCP                      | 102            |
| Schneider EGX UDP 59                        | Schneider     | UDP                      | 161            |
| Schneider ION                               | Schneider     | TCP                      | 102            |
| Siemens FWL LOAD (Firmware Upload)          | Siemens       | TCP                      | 102            |
| Siemens IEM                                 | Siemens       | TCP                      | 102            |
| Sinaut FW8                                  | Siemens       | TCP                      | 102            |
| SIP                                         | -             | UDP                      | 5060           |
| Skinny (SCCP)                               | Cisco         | UDP                      | 2000           |
| SNMP                                        | -             | UDP                      | 161            |
| Spirit                                      | ABB           | TCP                      | 102            |
| SSH                                         | -             | TCP                      | 22             |
| Sunny WEBBOX                                | SMA           | TCP                      | 502            |
| Symphony Plus                               | ABB           | TCP                      | 102            |
| Synchrophasor                               | -             | UDP                      | 102            |
| T3000 Protocols                             | Siemens       | TCP                      | 102            |
| TDS                                         | Microsoft     | TCP                      | 102            |
| Telnet - Hirschmann                         | Hirschmann    | TCP                      | 23             |
| Telnet - DeltaV                             | Emerson       | TCP                      | 23             |
| Telnet - Moxa                               | Moxa          | TCP                      | 23             |
| Telnet - Omniflow                           | Omniflow      | TCP                      | 23             |
| Telnet - SEL                                | Schweitzer    | TCP                      | 23             |
| TFTP                                        | -             | UDP                      | 69             |
| Totalflow                                   | ABB           | TCP                      | 502            |
| TRDP Process Data                           | TCNOpen       | UDP                      | 161            |
| Triconex Tristation                         | Schneider     | TCP                      | 102            |
| Triconex TSAA                               | Schneider     | TCP                      | 102            |
| UDLD                                        | Cisco         | UDP                      | 161            |
| Valmet DNA Alarms                           | Valmet        | TCP                      | 102            |
| Valmet DNA Damatic Configuration            | Valmet        | TCP                      | 102            |
| Valmet DNA Damatic Data                     | -             | TCP                      | 102            |
| Valmet DNA Data                              | Valmet        | TCP                      | 102            |
| Valmet DNA Frontend                          | Valmet        | TCP                      | 102            |
| VNC                                          | -             | TCP                      | 5900           |
| VNET (VHF)                                   | Yokogawa     | UDP                      | 34962          |
| WAGO                                         | WAGO         | TCP                      | 502            |
| Windows Update Delivery Optimization         | Microsoft    | TCP                      | 80, 443        |
| WonderWare Suitelink IOTalk                  | WonderWare   | TCP                      | 102            |
|



 






