🛡️ Nexus Sentinel
An AI-powered, cross-platform Network Monitoring and Cybersecurity Dashboard.

Nexus Sentinel bridges the gap between complex command-line tools like Wireshark/Nmap and expensive enterprise solutions. It provides real-time, deep packet inspection, threat detection, and visual network topology, augmented by a 100% private, local AI assistant to explain network anomalies in plain English.

Whether you are securing a home Wi-Fi network, a school lab, or a small business, Nexus Sentinel gives you enterprise-grade visibility without requiring a Network Operations Center (NOC).

🌟 Key Features
📊 Real-Time Dashboard: Live CPU, RAM, Disk, and Bandwidth metrics with streaming Chart.js graphs.
📦 Live Packet Capture: Deep packet inspection (TCP, UDP, DNS, HTTP, ARP) streamed via WebSockets with zero UI lag.
🚨 Threat Detection Engine: Heuristic algorithms instantly detect ARP Spoofing, SYN Floods, ICMP Floods, and Port Scans.
🗺️ Interactive Network Topology: A live, drag-and-drop visual map (React Flow) of your network. Instantly spot unauthorized devices.
🎯 Advanced Vulnerability Scanner: Automated Nmap profiles (CVE, UDP, OS Fingerprint) with live Vulners database integration to flag actual CVEs and provide remediation advice.
🤖 Private AI Assistant: A local LLM (via Ollama) that analyzes your network context. Ask it "Why is my network slow?" or "Explain this threat"—100% offline.
📄 PDF Audit Reports: Generate professional, branded PDF reports compiling device inventory, threats, and security posture.
🔒 Local Auth & Logging: Secure local admin account creation and a searchable database of all system and security events.
🏗️ System Architecture
Nexus Sentinel uses a high-performance Hybrid Desktop Architecture:

Frontend (Electron + React + TypeScript): Manages the native desktop window, UI rendering, and user interactions. Styled with Tailwind CSS (Glassmorphism dark theme).
Backend (Python FastAPI): Handles the heavy lifting. Uses Scapy for raw packet sniffing, psutil for system metrics, and subprocess for Nmap execution.
Communication: REST APIs for standard CRUD operations (scans, logs) and WebSockets for real-time, bi-directional streaming of packets, metrics, and threat alerts.
AI Engine: Ollama runs locally, serving the gemma:2b model to the FastAPI backend via local HTTP requests, ensuring network data never leaves the machine.
🛠️ Tech Stack
Category
Technologies
Frontend	React, TypeScript, Vite, Tailwind CSS, React Flow, Chart.js, Lucide Icons
Backend	Python 3.12, FastAPI, Uvicorn, SQLAlchemy, SQLite
Networking	Scapy, Nmap (NSE), Psutil
AI	Ollama, Gemma 2B
Packaging	Electron-Builder, GitHub Actions (CI/CD)

🚀 Installation & Setup
Prerequisites (Crucial)
Before running Nexus Sentinel, you must install the required network drivers and Python environment.

Install Python 3.12+:
Download from python.org.
CRITICAL: During installation, check the box "Add Python to PATH".
Install Backend Dependencies:
Open Command Prompt / Terminal and run:
bash

pip install fastapi "uvicorn[standard]" websockets scapy python-nmap psutil reportlab httpx sqlalchemy passlib python-jose
Install Npcap (Windows) / Libpcap (Linux):
Windows: Download Npcap. During installation, check the box for "Install Npcap in WinPcap API-compatible Mode".
Linux: sudo apt install libpcap-dev
Install Nmap (Optional but recommended for Port Scanner):
Download from nmap.org.
Running from Source (Development)
Clone the repository:
bash

git clone https://github.com/ansh-codes-blip/nexus-sentinel.git
cd nexus-sentinel
Start the Backend:
bash

cd backend
python -m venv venv
# Windows: venv\Scripts\activate
# Linux: source venv/bin/activate
pip install -r requirements.txt
sudo venv/bin/python -m uvicorn app.main:app --reload --port 8000
(Note: sudo is required on Linux for raw packet capture).
Start the Frontend:
bash

cd frontend
npm install
npm run electron:dev
Building the Installer (Production)
Compile Backend (Optional):
bash

cd backend
pyinstaller --onefile --name nexus-backend --collect-all scapy --collect-all uvicorn --collect-all fastapi run.py
Build Electron App:
bash

cd frontend
npm run dist
The installer will be in frontend/release/.
⚙️ Enabling the AI Assistant (Optional)
Nexus Sentinel includes a private AI assistant. To enable it:

Download and install Ollama.
Open your terminal and run the following command to download the model (~1.6GB):
bash

ollama run gemma:2b
Once downloaded, the AI Assistant tab in Nexus Sentinel will automatically connect.
📂 Project Structure
text

nexus-sentinel/
├── .github/workflows/      # CI/CD pipeline for Windows builds
├── backend/                # Python FastAPI Backend
│   ├── app/
│   │   ├── api/            # API routes (Metrics, Capture, Scans, Auth)
│   │   ├── models/         # SQLAlchemy DB models (Devices, Alerts, Logs)
│   │   ├── services/       # Core logic (Scapy, Nmap, Threat Engine, AI)
│   │   └── main.py         # App entry point
│   └── run.py              # Production runner
├── frontend/               # Electron + React Frontend
│   ├── electron/           # Electron main process (main.cjs)
│   ├── src/
│   │   ├── pages/          # React components (Dashboard, Topology, etc.)
│   │   ├── layouts/        # Sidebar layout
│   │   ├── stores/         # Auth context
│   │   └── App.tsx         # React router
│   └── package.json        # Build configuration
└── README.md
📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgements
Scapy for being the ultimate packet manipulation tool.
FastAPI for the incredible async Python performance.
Ollama for making local LLMs accessible.
Electron for making cross-platform desktop apps a reality.
