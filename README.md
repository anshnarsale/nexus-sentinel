# 🛡️ Nexus Sentinel

### AI-Powered Network Monitoring & Cybersecurity Dashboard

> **See your network. Understand the threats. Take control.**

Nexus Sentinel is a **cross-platform network monitoring and cybersecurity platform** designed to bridge the gap between powerful command-line tools such as **Wireshark and Nmap** and complex, expensive enterprise security solutions.

It combines **real-time network visibility, packet inspection, automated threat detection, network topology, vulnerability scanning, and a private local AI assistant** into a single modern desktop application.

Whether you're monitoring a **home network, school lab, development environment, or small business**, Nexus Sentinel provides actionable security insights without requiring a dedicated NOC.

---

## ✨ Why Nexus Sentinel?

Traditional network security tools are powerful, but they often require significant technical knowledge.

Nexus Sentinel brings them together behind a unified interface:

```text
          ┌──────────────────────────────┐
          │       NEXUS SENTINEL         │
          │  Network Security Platform   │
          └──────────────┬───────────────┘
                         │
       ┌─────────────────┼─────────────────┐
       │                 │                 │
       ▼                 ▼                 ▼
   Network            Security            AI
  Visibility          Analysis         Assistant
       │                 │                 │
       ▼                 ▼                 ▼
   Packets           Threats          Explanations
   Devices            CVEs            Recommendations
   Traffic            Alerts          Investigation
   Topology           Scans           Local LLM
```

### 🔐 Privacy by Design

Nexus Sentinel's AI assistant is designed around a **local-first architecture**.

Network information can be analyzed using a locally running LLM through **Ollama**, allowing sensitive network information to remain on the machine instead of being sent to a cloud AI service.

---

# 🌟 Key Features

## 📊 Real-Time Network Dashboard

Monitor your system and network activity through a centralized dashboard.

* CPU utilization
* RAM usage
* Disk usage
* Network bandwidth
* Upload/download activity
* Live streaming charts
* Security event counters
* Active device count
* Threat statistics

Built with **Chart.js** for responsive real-time visualization.

---

## 📦 Live Packet Capture

Capture and inspect network traffic in real time.

Nexus Sentinel uses **Scapy** to provide packet-level visibility across protocols including:

* TCP
* UDP
* DNS
* HTTP
* ARP
* ICMP
* IP

Captured traffic is streamed to the frontend using **WebSockets**, allowing the interface to remain responsive even during continuous packet capture.

### Example

```text
[12:41:08] TCP     192.168.1.10 → 142.250.x.x
[12:41:09] DNS     192.168.1.10 → 192.168.1.1
[12:41:09] ARP     192.168.1.20 → Broadcast
[12:41:10] HTTPS   192.168.1.10 → 104.x.x.x
```

---

# 🚨 Intelligent Threat Detection

Nexus Sentinel continuously analyzes network activity for suspicious patterns.

### Currently supported detection logic

| Threat            | Detection                                 |
| ----------------- | ----------------------------------------- |
| 🔴 ARP Spoofing   | ARP/IP-MAC inconsistencies                |
| 🔴 SYN Flood      | Abnormally high SYN activity              |
| 🔴 ICMP Flood     | Excessive ICMP traffic                    |
| 🟠 Port Scan      | Suspicious multi-port connection patterns |
| 🟠 Unknown Device | Newly discovered network devices          |

Instead of simply showing packets, Nexus Sentinel attempts to turn raw network activity into **security events that humans can understand**.

---

# 🗺️ Interactive Network Topology

Visualize your network as an interactive graph.

Powered by **React Flow**, the topology view provides a visual representation of:

* Routers
* Gateways
* Computers
* Phones
* IoT devices
* Servers
* Unknown devices
* Network relationships

### Example workflow

```text
                    Internet
                       │
                       ▼
                ┌─────────────┐
                │   Gateway   │
                │ 192.168.1.1 │
                └──────┬──────┘
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Laptop        Phone       IoT Device
     192.168.1.10  192.168.1.12  192.168.1.30
```

New or unexpected devices can be highlighted for investigation.

---

# 🎯 Vulnerability Scanner

Nexus Sentinel integrates **Nmap** to provide automated network reconnaissance and vulnerability assessment.

Supported scanning capabilities can include:

* Port scanning
* Service detection
* OS fingerprinting
* UDP scanning
* NSE-based security checks
* CVE discovery
* Vulnerability enrichment

Where supported, vulnerability information can be enriched using the **Vulners database**.

The goal isn't simply to report:

> `Port 22 is open`

but to provide useful security context:

```text
Host: 192.168.1.20

Port: 22/tcp
Service: SSH

Risk: Medium

Finding:
Potentially outdated SSH service detected.

Recommended Action:
Verify the installed SSH version and apply
available security updates.
```

> ⚠️ Only scan systems and networks that you own or have explicit permission to assess.

---

# 🤖 Private Local AI Assistant

Nexus Sentinel integrates with **Ollama** to provide a local AI assistant.

Instead of manually interpreting packet captures, alerts, and scan results, users can ask questions in natural language.

### Example questions

```text
Why is my network slow?

What does this ARP alert mean?

Is this device suspicious?

Explain this port scan.

Why is this machine generating so many connections?

What should I fix first?

Summarize my current security posture.
```

The AI can use available Nexus Sentinel context to transform technical security information into understandable explanations.

### 🔒 Local AI Architecture

```text
┌──────────────────────┐
│   Nexus Sentinel     │
│                      │
│  Network Telemetry   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│    FastAPI Backend   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│        Ollama        │
│                      │
│     Local LLM        │
└──────────────────────┘

          ❌ Cloud AI
          ❌ External API
          ❌ Network Upload
```

Your network telemetry does not need to leave the machine simply to obtain an AI explanation.

---

# 📄 Professional Security Reports

Generate PDF audit reports containing information such as:

* Network inventory
* Discovered devices
* Open ports
* Vulnerability findings
* Security alerts
* Threat history
* Security posture
* Recommended remediation

Useful for:

* Home network audits
* School laboratories
* Small businesses
* Security assessments
* Project demonstrations
* Documentation

---

# 🔐 Local Authentication & Logging

Nexus Sentinel includes local security controls for administrative access.

### Features

* Local administrator account
* Password-protected access
* Security event logging
* Searchable logs
* Scan history
* Threat history
* Device discovery history

The objective is to provide an auditable record of security activity.

---

# 🏗️ System Architecture

Nexus Sentinel uses a **hybrid desktop architecture**.

```text
                         NEXUS SENTINEL
                               │
                 ┌─────────────┴─────────────┐
                 │                           │
          Electron + React             FastAPI Backend
                 │                           │
          ┌──────┴──────┐          ┌─────────┼─────────┐
          │             │          │         │         │
       React UI      Electron    Scapy     Nmap     SQLAlchemy
          │             │          │         │         │
          └──────┬──────┘          └─────────┼─────────┘
                 │                           │
                 │        WebSocket          │
                 └─────────────┬─────────────┘
                               │
                         Threat Engine
                               │
                               ▼
                            Ollama
                               │
                               ▼
                           Local LLM
```

---

# 🧩 Technology Stack

| Category        | Technology            |
| --------------- | --------------------- |
| Frontend        | React                 |
| Language        | TypeScript            |
| Desktop         | Electron              |
| Build Tool      | Vite                  |
| Styling         | Tailwind CSS          |
| Visualization   | React Flow            |
| Charts          | Chart.js              |
| Icons           | Lucide                |
| Backend         | Python                |
| API             | FastAPI               |
| Server          | Uvicorn               |
| Packet Capture  | Scapy                 |
| Network Scanner | Nmap                  |
| System Metrics  | Psutil                |
| Database        | SQLite                |
| ORM             | SQLAlchemy            |
| Authentication  | Passlib / python-jose |
| Reports         | ReportLab             |
| AI Runtime      | Ollama                |
| AI Model        | Gemma 2B              |
| Packaging       | Electron Builder      |
| CI/CD           | GitHub Actions        |

---

# 🔄 Communication Architecture

Nexus Sentinel uses different communication mechanisms depending on the workload.

### REST API

Used for:

* Authentication
* CRUD operations
* Scan configuration
* Device management
* Historical logs
* Report generation

### WebSockets

Used for real-time data:

* Packet streams
* Network metrics
* Threat alerts
* Device discovery
* Scanner progress

This separation keeps standard API operations independent from high-frequency network telemetry.

---

# 📂 Project Structure

```text
nexus-sentinel/
│
├── .github/
│   └── workflows/
│       └── build.yml
│
├── backend/
│   ├── app/
│   │   ├── api/
│   │   │   ├── metrics.py
│   │   │   ├── capture.py
│   │   │   ├── scans.py
│   │   │   └── auth.py
│   │   │
│   │   ├── models/
│   │   │   ├── devices.py
│   │   │   ├── alerts.py
│   │   │   └── logs.py
│   │   │
│   │   ├── services/
│   │   │   ├── packet_capture.py
│   │   │   ├── threat_engine.py
│   │   │   ├── network_scanner.py
│   │   │   └── ai_service.py
│   │   │
│   │   └── main.py
│   │
│   ├── run.py
│   └── requirements.txt
│
├── frontend/
│   ├── electron/
│   │   └── main.cjs
│   │
│   ├── src/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── components/
│   │   ├── stores/
│   │   └── App.tsx
│   │
│   └── package.json
│
├── README.md
└── LICENSE
```

---

# 🚀 Installation

## Prerequisites

Before running Nexus Sentinel, install the following.

### 1. Python

Install **Python 3.12 or later**.

During Windows installation, make sure:

```text
☑ Add Python to PATH
```

---

### 2. Install Backend Dependencies

```bash
pip install fastapi "uvicorn[standard]" websockets scapy python-nmap psutil reportlab httpx sqlalchemy passlib python-jose
```

Or, if the repository contains a requirements file:

```bash
pip install -r requirements.txt
```

---

### 3. Install Packet Capture Support

#### Windows

Install **Npcap**.

During installation, enable:

```text
Install Npcap in WinPcap API-compatible Mode
```

#### Linux

Install libpcap development packages:

```bash
sudo apt install libpcap-dev
```

---

### 4. Install Nmap

Nmap is required for the advanced scanning functionality.

After installation, verify:

```bash
nmap --version
```

---

# 🛠️ Running from Source

## Clone the repository

```bash
git clone https://github.com/ansh-codes-blip/nexus-sentinel.git
cd nexus-sentinel
```

---

## Start the Backend

```bash
cd backend
```

Create a virtual environment:

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start FastAPI:

### Windows

```bash
python -m uvicorn app.main:app --reload --port 8000
```

### Linux

Raw packet capture may require elevated privileges depending on the capture configuration:

```bash
sudo venv/bin/python -m uvicorn app.main:app --reload --port 8000
```

---

# 💻 Start the Frontend

Open another terminal:

```bash
cd frontend
npm install
npm run electron:dev
```

Nexus Sentinel should now launch as a desktop application.

---

# 📦 Building the Application

## Build the Backend

For standalone backend packaging:

```bash
cd backend

pyinstaller --onefile \
  --name nexus-backend \
  --collect-all scapy \
  --collect-all uvicorn \
  --collect-all fastapi \
  run.py
```

---

## Build the Electron Application

```bash
cd frontend

npm install
npm run dist
```

The generated installer will be placed in:

```text
frontend/release/
```

---

# 🤖 Enable the AI Assistant

Nexus Sentinel's AI assistant is optional.

Install **Ollama**, then download the configured local model:

```bash
ollama run gemma:2b
```

Once the model is available locally, Nexus Sentinel can connect to Ollama through its local API.

### AI Pipeline

```text
Network Event
     │
     ▼
Threat Engine
     │
     ▼
Context Builder
     │
     ▼
FastAPI
     │
     ▼
Ollama
     │
     ▼
Local LLM
     │
     ▼
Human-readable explanation
```

---

# 🛡️ Security Philosophy

Nexus Sentinel is built around four principles:

### 1. Visibility

You can't secure what you can't see.

### 2. Explainability

Security alerts should explain **what happened and why it matters**.

### 3. Privacy

Network telemetry should remain local whenever possible.

### 4. Actionability

Detection is only useful when users know what to do next.

---

# 🎯 Intended Use Cases

### 🏠 Home Networks

Identify:

* Unknown devices
* Suspicious traffic
* Open ports
* Network anomalies

### 🏫 Educational Labs

Useful for teaching:

* Networking
* Packet analysis
* Network security
* Nmap
* Threat detection
* Network topology

### 🏢 Small Businesses

Provide lightweight visibility without requiring a full enterprise SOC/NOC deployment.

### 🧪 Security Research

Use the platform as a foundation for experimenting with:

* Detection algorithms
* Network telemetry
* AI-assisted analysis
* Security visualization

---

# ⚠️ Responsible Use

Nexus Sentinel is intended for **authorized network monitoring and security assessment**.

Only capture traffic, scan hosts, or perform vulnerability assessments on systems and networks that you own or have explicit permission to test.

Do not use Nexus Sentinel to monitor, scan, or attack networks without authorization.

---

# 🗺️ Roadmap

The project is actively evolving.

### Current

* [x] Desktop application architecture
* [x] Real-time system metrics
* [x] Packet capture
* [x] WebSocket streaming
* [x] Threat detection engine
* [x] Network topology
* [x] Nmap integration
* [x] Local AI integration
* [x] PDF reporting
* [x] Local authentication
* [x] Security logging

### Planned

* [ ] Advanced behavioral anomaly detection
* [ ] Network baseline learning
* [ ] More protocol dissectors
* [ ] Custom detection rules
* [ ] Automated remediation suggestions
* [ ] Historical traffic analytics
* [ ] Security posture scoring
* [ ] Improved CVE correlation
* [ ] Plugin architecture
* [ ] Docker/container monitoring
* [ ] Multi-interface monitoring
* [ ] Role-based access control
* [ ] Expanded Linux/macOS support
* [ ] Hardware/network appliance mode

---

# 🤝 Contributing

Contributions are welcome.

```bash
# Fork the repository
# Create a feature branch
git checkout -b feature/my-feature

# Make your changes
git add .
git commit -m "feat: add my feature"

# Push the branch
git push origin feature/my-feature
```

Then open a Pull Request.

When contributing, please include:

* A clear description of the change
* Steps to reproduce or test it
* Screenshots for UI changes
* Security considerations where applicable

---

# 🐛 Reporting Issues

Found a bug or security issue?

Please open an issue with:

* Operating system
* Nexus Sentinel version
* Python version
* Nmap version
* Relevant logs
* Steps to reproduce
* Screenshots where applicable

For security-sensitive vulnerabilities, avoid publicly posting exploitable details until the issue has been responsibly disclosed.

---

# 📜 License

Nexus Sentinel is released under the **MIT License**.

See [`LICENSE`](LICENSE) for details.

---

# 🙏 Acknowledgements

Nexus Sentinel is built on top of several excellent open-source technologies:

* **Scapy** — packet manipulation and network analysis
* **FastAPI** — high-performance Python API framework
* **Nmap** — network discovery and security auditing
* **React** — frontend UI framework
* **Electron** — cross-platform desktop applications
* **Ollama** — local AI model runtime
* **Chart.js** — data visualization
* **React Flow** — interactive network visualization
* **SQLAlchemy** — database toolkit and ORM

---

# ⭐ Support the Project

If Nexus Sentinel is useful to you:

⭐ Star the repository
🐛 Report bugs
💡 Suggest features
🔧 Submit pull requests
📢 Share the project

---

<div align="center">

### 🛡️ Nexus Sentinel

**Network visibility. Security intelligence. Local AI.**

Built for people who want to understand their network.

**© 2026 Nexus Sentinel**

</div>
