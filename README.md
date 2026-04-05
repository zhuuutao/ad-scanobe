ad-scanobe: Local Network Adobe Monitor
ad-scanobe is a specialized macOS monitoring tool designed to detect and log Adobe-related network activity across a local hotspot (bridge100). It leverages the power of tcpdump to provide real-time DNS sniffing with customizable keyword filtering.

🚀 Quick Start (Running with Permissions)
Since this app accesses low-level network interfaces (bridge100), it cannot be run by simply clicking the .app icon. You must execute the internal binary via Terminal with sudo privileges.

Step 1: Build the Project
Open the project in Xcode.

Press Cmd + B to build the application.

Locate the build product:

Right-click ad-scanobe.app under the Products folder in Xcode.

Select Show in Finder.

Step 2: Run via Terminal (Sudo)
Open Terminal.

Type sudo  (make sure to include the space).

Drag the binary file into the Terminal window.

Note: The binary is located inside the app bundle at:
ad-scanobe.app/Contents/MacOS/ad-scanobe

Your command should look like this:

Bash
sudo /Path/To/Your/Build/ad-scanobe.app/Contents/MacOS/ad-scanobe
Press Enter and type your Mac login password.

🛠 Features
Real-time Sniffing: Captures UDP Port 53 (DNS) traffic instantly using the system's tcpdump engine.

Dynamic Keywords: Add or remove keywords (e.g., adobe, licenses, hbrt) on the fly without restarting the scan.

Device Discovery: Integrated ARP scanning to identify devices connected to your macOS Hotspot.

Raw Log Access: View both the parsed domain and the raw packet string for deep inspection.

📋 Monitored Domains (Recommended)
To effectively monitor Adobe compliance, the following keywords are pre-configured:

adobe.io / adobe.com: Core API and licensing checks.

hbrt.adobe.com: Licensing heartbeat service.

cc-api-data: Creative Cloud asset synchronization.

crs.cr: Adobe Crash Reporter (often triggered by unstable/patched versions).

⚠️ Requirements & Troubleshooting
Interface: By default, this app monitors bridge100. Ensure Internet Sharing is turned ON in System Settings.

VPN Notice: If the target device (e.g., a phone connected to the hotspot) is using a VPN or Encrypted DNS (DoH), the monitor will not be able to see the domain names. Disable all proxies on the target device for testing.

Command Not Found: Ensure you are pointing to the binary inside Contents/MacOS/, not just the .app folder.

🛠 Technical Architecture
The app uses a hybrid architecture for maximum reliability:

SwiftUI: Provides a modern, responsive dashboard.

Foundation.Process: Manages a background tcpdump instance.

Pipe & NotificationCenter: Pipes real-time terminal output directly into the UI list with zero-latency.

Developed for SFK International Arts - Compliance & Network Security.
