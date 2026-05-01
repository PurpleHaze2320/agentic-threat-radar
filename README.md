# agentic-threat-radar
Continuous Security Analysis of the Model Context Protocol Ecosystem.
🛡️ Agentic Threat Radar

Continuous Security Analysis of the Model Context Protocol (MCP) Ecosystem.

📌 Overview

As the adoption of Agentic AI frameworks accelerates, developers are rapidly deploying Model Context Protocol (MCP) servers to grant Large Language Models (LLMs) local execution context. However, this introduces massive, unmonitored attack vectors into the software supply chain.

The Agentic Threat Radar is an automated static analysis engine designed to continuously scan open-source MCP repositories for critical security misconfigurations, Remote Code Execution (RCE) vectors, and unauthorized network bindings.

🚨 The Problem (Why I Built This)

Through my background in Cybersecurity and Infrastructure Operations (Fortis Intelligence), I identified three critical blind spots in the current MCP landscape:

Unsandboxed Execution: MCPs utilizing raw child_process.exec or subprocess.Popen(shell=True), allowing indirect prompt injections to hijack host environments.

The "NeighborJack" Vector: Servers improperly binding to 0.0.0.0 without strict authentication mechanisms.

Static Credential Leakage: Hardcoded API keys or plaintext environment variables bypassing standard OAuth 2.1 / PKCE compliance.

🏗️ Target Architecture (AWS Native)

While this iteration runs via GitHub Actions, the enterprise architecture is designed to be fully decoupled and deployed natively on AWS:

Compute: Scheduled via Amazon EventBridge triggering AWS Lambda functions to parallelize repository cloning and static analysis.

Storage: Raw JSON intelligence reports stored in Amazon S3.

Visualization: Dashboard served via Amazon CloudFront / S3 static hosting, with threat telemetry aggregated in Amazon QuickSight.

Security: Execution environments strictly isolated inside an Amazon VPC with outbound-only PrivateLink routing.

🚀 Usage (Local Scanning)

To run the static analyzer against a local directory or cloned MCP repository:

# 1. Clone the radar
git clone [https://github.com/PurpleHaze2320/agentic-threat-radar.git](https://github.com/PurpleHaze2320/agentic-threat-radar.git)
cd agentic-threat-radar

# 2. Run the analysis engine against a target directory
python mcp_threat_scanner.py --target ./path/to/mcp/repo


📊 The Dashboard

The accompanying React dashboard visualizes the JSON output from the Python scanner, providing a triage view of the highest-risk repositories currently circulating in the ecosystem.

Dashboard UI is built with Tailwind CSS and React, utilizing a dark-mode, high-contrast security aesthetic.

⚠️ Disclaimer

This tool is built for security research and infrastructure hardening. It is not intended to disparage open-source creators, but rather to highlight the critical need for "Security by Design" in the rapidly evolving Agentic AI space.
