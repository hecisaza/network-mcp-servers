# Network Infrastructure MCP Servers

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

A curated list of Model Context Protocol (MCP) servers for network infrastructure automation, enabling AI agents to interact with network devices, management platforms, and automation tools.

---

## Table of Contents

- [What is MCP?](#what-is-mcp)
- [Why MCP for Network Automation?](#why-mcp-for-network-automation)
- [Vendor-Specific MCP Servers](#vendor-specific-mcp-servers)
  - [Juniper](#juniper)
  - [Cisco](#cisco)
  - [Arista](#arista)
- [Multi-Vendor MCP Servers](#multi-vendor-mcp-servers)
- [Observability and Monitoring](#observability-and-monitoring)
- [Wireless and Campus](#wireless-and-campus)
- [Security and Firewalls](#security-and-firewalls)
- [Data Center](#data-center)
- [Network Source of Truth](#network-source-of-truth)
- [Orchestration Platforms](#orchestration-platforms)
- [Topology and Visualization](#topology-and-visualization)
- [Multi-Server Suites](#multi-server-suites)
- [Watch List](#watch-list)
- [Use Cases](#use-cases)
- [Getting Started](#getting-started)
- [Security Considerations](#security-considerations)
- [Additional Resources](#additional-resources)
- [Contributing](#contributing)

---

## What is MCP?

The **Model Context Protocol (MCP)** is an open standard developed by Anthropic that enables AI models to securely connect with external data sources and tools. MCP servers act as bridges between AI agents (like Claude, Cursor, or custom LLM applications) and infrastructure systems.

**MCP provides:**
- Standardized communication between AI and external systems
- Tool discovery allowing AI to dynamically find available capabilities
- Secure, governed access to infrastructure resources

---

## Why MCP for Network Automation?

Traditional network automation relies on static scripts and playbooks. MCP enables a new paradigm:

| Traditional Automation | MCP-Enabled Automation |
|------------------------|------------------------|
| Static, rule-based scripts | Dynamic, context-aware reasoning |
| Vendor-specific integrations | Standardized protocol across vendors |
| Manual troubleshooting | Conversational network inquiry |
| Fixed workflows | Adaptive, AI-driven operations |

**Key Benefits:**
- Query network state using natural language
- Multi-vendor automation without rewriting core logic
- Closed-loop remediation with governance guardrails
- Scalable architecture—add new vendors by deploying new MCP servers

---

## Vendor-Specific MCP Servers

### Juniper

#### Junos MCP Server

Official MCP server from Juniper for interacting with Junos OS devices.

| Attribute | Details |
|-----------|---------|
| **Repository** | [github.com/Juniper/junos-mcp-server](https://github.com/Juniper/junos-mcp-server) |
| **Maintainer** | Juniper Networks |
| **Protocol** | SSH (Key-based authentication recommended) |
| **Framework** | PyEZ |

**Features:**
- Retrieve device configurations
- Check device health and status
- Execute operational commands
- Push configuration changes
- Dynamic device addition via elicitation

**Resources:**
- [Juniper Community Blog - Network Automation with AI and Junos MCP Server](https://community.juniper.net/blogs/victor-ganjian/2025/11/01/network-automation-with-ai-and-junos-mcp-server)

---

#### Juniper Mist MCP Server (Beta)

Official hosted MCP server for the Juniper Mist cloud — no local install required.

| Attribute | Details |
|-----------|---------|
| **Documentation** | [Juniper Mist MCP Server with Claude Desktop (Beta)](https://www.juniper.net/documentation/us/en/software/mist/mist-aiops/shared-content/topics/concept/juniper-mist-mcp-claude.html) |
| **Maintainer** | Juniper Networks |
| **Endpoint** | `https://mcp.ai.juniper.net/mcp/mist` |
| **Auth** | Bearer token (Mist Cloud API token) + `X-Mist-Base-URL` header, optional `X-Mist-Org-ID` |

**Features:**
- Manage, monitor, and troubleshoot Mist organizations
- Site and organization status queries
- Client and network issue troubleshooting

> ⚠️ Juniper's own docs warn this server can expose sensitive data such as PSKs, RADIUS secrets, and SNMP credentials to the AI assistant. Scope tokens carefully.

---

### Cisco

#### Cisco Catalyst Center MCP Server

Enterprise-grade MCP server for Cisco Catalyst Center (formerly DNA Center) integration.

| Attribute | Details |
|-----------|---------|
| **Documentation** | [Cisco Support Docs](https://www.cisco.com/c/en/us/support/docs/cloud-systems-management/catalyst-center/223278-harness-the-power-of-mcp-servers.html) |
| **Maintainer** | Cisco |
| **Integration** | ServiceNow, HashiCorp Vault, OPA |

**Features:**
- Multi-agent workflow orchestration
- Enterprise authentication (OIDC, Duo MFA)
- Policy-based access control with OPA
- Secret management via HashiCorp Vault
- Audit logging with Elasticsearch

---

#### Cisco Meraki MCP Server

MCP server for managing Cisco Meraki cloud-managed networks.

| Attribute | Details |
|-----------|---------|
| **Blog Post** | [Cisco Learning Blog - Wrangling the Wild West of MCP Servers](https://blogs.cisco.com/learning/wrangling-the-wild-west-of-mcp-servers) |
| **Maintainer** | Cisco |
| **API** | Meraki Dashboard API |

**Features:**
- Device inventory across organizations
- Firmware compliance checking
- Upgrade recommendations with human-in-the-loop approval
- Role-based access control via route maps

---

#### pyATS Network Automation MCP Server

Containerized MCP server using Cisco's pyATS framework.

| Attribute | Details |
|-----------|---------|
| **PulseMCP** | [pulsemcp.com/servers/automateyournetwork-pyats-network-automation](https://www.pulsemcp.com/servers/automateyournetwork-pyats-network-automation) |
| **Maintainer** | John Capobianco (AutomateYourNetwork) |
| **Framework** | pyATS/Genie |

**Features:**
- Device configuration and troubleshooting
- Network monitoring via SSH
- Containerized deployment
- Cisco device support (IOS, IOS-XE, NX-OS, IOS-XR)

---

#### Cisco ThousandEyes MCP Server (Official)

Official MCP server for ThousandEyes network and internet monitoring.

| Attribute | Details |
|-----------|---------|
| **Repository** | [github.com/CiscoDevNet/ThousandEyes-MCP-Server-official](https://github.com/CiscoDevNet/ThousandEyes-MCP-Server-official) |
| **Maintainer** | Cisco (CiscoDevNet) |
| **Transport** | HTTP/SSE and HTTP streamable |
| **Auth** | OAuth bearer token, OAuth2 dynamic client registration |

**Features:**
- List tests and retrieve test details; run instant tests
- Search alerts, events, and internet outages
- BGP test results, path visualization, endpoint agent metrics
- Metric anomaly detection and aggregated metrics
- AI-generated explanations of test results

---

### Arista

#### Arista CloudVision MCP Server

MCP server for Arista CloudVision network management platform.

| Attribute | Details |
|-----------|---------|
| **PulseMCP** | [pulsemcp.com/servers/noredistribution-arista-cloudvision](https://www.pulsemcp.com/servers/noredistribution-arista-cloudvision) |
| **Maintainer** | noredistribution (Community) |
| **API** | CloudVision API |

**Features:**
- Device inventory retrieval
- System event monitoring
- Connectivity status checks
- Tag creation and management
- Natural language network queries

**Resources:**
- [AI Engineer's Guide to Arista CloudVision MCP Server](https://skywork.ai/skypage/en/arista-cloudvision-network-automation/1981594259663417344)

---

## Multi-Vendor MCP Servers

### Scrapli MCP Server

CLI-based network automation using the Scrapli library.

| Attribute | Details |
|-----------|---------|
| **Framework** | Scrapli |
| **Creator** | Carl Montanari |
| **Transport** | SSH, Telnet, NETCONF |

**Supported Platforms:**
- Cisco IOS/IOS-XE/NX-OS/IOS-XR
- Juniper Junos
- Arista EOS
- Additional platforms via `scrapli_community`

**Features:**
- Direct CLI interaction
- Multi-vendor support
- Conversational automation model
- Extensible architecture

**Resources:**
- [Deep Dive into Scrapli Network Automation MCP Server](https://skywork.ai/skypage/en/ai-hardware-scrapli-network-automation/1980441425869053952)

---

### Netmiko MCP Server

Network automation using the popular Netmiko library.

| Attribute | Details |
|-----------|---------|
| **MCP.so** | [mcp.so/server/mcp-server-netmiko/melihteke](https://mcp.so/server/mcp-server-netmiko/melihteke) |
| **Maintainer** | melihteke (Community) |
| **Framework** | Netmiko |

**Supported Platforms:**
- Cisco (IOS, IOS-XE, NX-OS, ASA)
- Juniper Junos
- Arista EOS
- HP/Aruba
- And 50+ other platforms

**Features:**
- Configuration changes across multiple devices
- Log and metric collection
- Network troubleshooting
- Command-line automation

---

### Puppet Edge MCP Server

YANG-based network device configuration via Puppet Enterprise.

| Attribute | Details |
|-----------|---------|
| **Documentation** | [Puppet Blog - Build Tasks for Network Devices](https://www.puppet.com/blog/puppet-edge-code-assist) |
| **Maintainer** | Puppet (Perforce) |
| **Integration** | VS Code, GitHub Copilot |

**Supported Platforms:**
- Cisco
- Juniper Networks
- Arista Networks
- Any device with YANG/OpenConfig support

**Features:**
- Natural language task generation
- YANG model validation
- IDE integration (VS Code)
- Code assistance for network tasks

---

## Observability and Monitoring

### Splunk MCP Server (Official)

Official MCP server from Splunk, distributed as a Splunkbase app.

| Attribute | Details |
|-----------|---------|
| **Splunkbase** | [splunkbase.splunk.com/app/7931](https://splunkbase.splunk.com/app/7931) |
| **Repository** | [github.com/CiscoDevNet/Splunk-MCP-Server-official](https://github.com/CiscoDevNet/Splunk-MCP-Server-official) |
| **Maintainer** | Splunk (Cisco) — "Splunk Supported · Beta" |
| **Supported** | Splunk Enterprise and Splunk Cloud Platform 8.0–10.2 |

**Tools:**
- `generate_spl` — natural language to SPL query generation
- `run_splunk_query` — execute SPL searches and retrieve results
- `get_splunk_info`, `get_indexes`, `get_index_info` — instance and index metadata
- `get_saved_searches` — discover knowledge objects

**Features:**
- Respects existing Splunk role-based access control
- Audit logging and input validation
- v1.0.1 released February 2026

**Resources:**
- [Splunk MCP product page](https://www.splunk.com/en_us/products/model-context-protocol.html)
- [Splunk Docs - MCP Server for Splunk platform](https://help.splunk.com/en/splunk-cloud-platform/mcp-server-for-splunk-platform)

---

## Wireless and Campus

### HPE Aruba Networking Central MCP Server

Read-only MCP server for HPE Aruba Networking Central (documented on HPE's developer portal, but explicitly **not** an officially supported HPE product).

| Attribute | Details |
|-----------|---------|
| **Documentation** | [developer.arubanetworks.com/new-central/docs/central-mcp-server](https://developer.arubanetworks.com/new-central/docs/central-mcp-server) |
| **Repository** | [github.com/KarthikSKumar98/central-mcp-server](https://github.com/KarthikSKumar98/central-mcp-server) |
| **Access** | Read-only — cannot modify configuration or network state |

**Features:**
- 25 tools across 10 categories reaching 85+ Central API endpoints
- Site/device health, AP/switch/gateway monitoring, client history
- Alerts, event logs, network tests, port diagnostics
- 12 pre-built investigation workflows

---

### HPE Networking Unified MCP Server

Community server combining Juniper Mist, Aruba Central, and HPE GreenLake in one container.

| Attribute | Details |
|-----------|---------|
| **Repository** | [github.com/nowireless4u/hpe-networking-mcp](https://github.com/nowireless4u/hpe-networking-mcp) |
| **Maintainer** | nowireless4u (Community) |

---

## Security and Firewalls

### PAN-OS MCP Servers (Community)

Community MCP servers for Palo Alto Networks firewalls.

| Attribute | Details |
|-----------|---------|
| **Repositories** | [github.com/cdot65/pan-os-mcp](https://github.com/cdot65/pan-os-mcp) · [github.com/apius-tech/Palo-MCP](https://github.com/apius-tech/Palo-MCP) |
| **Maintainers** | cdot65, apius-tech (Community) |
| **API** | PAN-OS XML/REST API |

---

### Fortinet Embedded MCP (FortiWeb / FortiManager)

Fortinet ships MCP capability inside its products rather than as a sidecar server.

| Attribute | Details |
|-----------|---------|
| **FortiWeb** | [MCP Protocol - FortiWeb 8.0 Administration Guide](https://docs.fortinet.com/document/fortiweb/8.0.6/administration-guide/97697/mcp-protocol) |
| **FortiManager** | [MCP framework for FortiAI agentic assistants - FortiManager 8.0](https://docs.fortinet.com/document/fortimanager/8.0.0/new-features/850974/the-model-context-protocol-mcp-framework-used-by-fortiai-agentic-assistants-and-features-on-fortimanager) |
| **Maintainer** | Fortinet |

---

## Data Center

### Nexus Dashboard MCP Server

Community MCP server for Cisco Nexus Dashboard with enterprise guardrails.

| Attribute | Details |
|-----------|---------|
| **Repository** | [github.com/beye91/nexus-dashboard-mcp](https://github.com/beye91/nexus-dashboard-mcp) |
| **Maintainer** | beye91 (Community) |
| **License** | Apache 2.0 |

**Features:**
- 638+ operations across 5 Nexus Dashboard APIs
- Read-only by default; write operations require explicit enablement
- RBAC, encrypted credentials, audit logging, LDAP integration
- Web-based admin interface; Docker deployment with PostgreSQL

---

## Network Source of Truth

### NetBox Platform MCP Server (Official)

Fully managed MCP server from NetBox Labs, currently in public preview on NetBox Cloud (NetBox Enterprise support planned).

| Attribute | Details |
|-----------|---------|
| **Documentation** | [netboxlabs.com/docs/cloud/platform-mcp-server](https://netboxlabs.com/docs/cloud/platform-mcp-server/) |
| **Maintainer** | NetBox Labs |
| **Access** | Read **and** write (CRUD, bulk ops) by plan tier; read-only mode on request |
| **Auth** | NetBox v2 API tokens (`nbt_*`) over HTTP bearer |

**Features:**
- Query, search, and model discovery
- GraphQL support, CRUD and bulk operations
- IP address management and cable tracing
- Code Mode for multi-step workflows; branching and change management

---

### NetBox MCP Server (Community)

Lightweight open-source NetBox MCP server.

| Attribute | Details |
|-----------|---------|
| **Repository** | [github.com/netboxlabs/netbox-mcp-server](https://github.com/netboxlabs/netbox-mcp-server) |
| **Maintainer** | NetBox Labs (community project) |

---

### NetBox MCP Server (Read-Write, Community)

Full read/write access to NetBox IPAM/DCIM.

| Attribute | Details |
|-----------|---------|
| **Repository** | [github.com/alexkiwi1/netbox-mcp-rw](https://github.com/alexkiwi1/netbox-mcp-rw) |
| **Maintainer** | alexkiwi1 (Community) |
| **Framework** | FastMCP |

**Features:**
- Device inventory management
- IP address assignment
- Site and rack management
- Full CRUD operations
- Status updates and lifecycle management

**Resources:**
- [AI Engineer's Guide to NetBox MCP Server](https://skywork.ai/skypage/en/netbox-mcp-server-ai-engineer-guide/1981163259676557312)

---

### Nautobot MCP Server (Official)

Official MCP server from Network to Code for the Nautobot source of truth (available to Nautobot customers).

| Attribute | Details |
|-----------|---------|
| **Documentation** | [docs.nautobot.com/projects/nautobot-mcp-server](https://docs.nautobot.com/projects/nautobot-mcp-server/en/stable/) |
| **Maintainer** | Network to Code |
| **Version** | v1.0 |

**Features:**
- Natural language queries over devices, IPAM, and VLANs
- Authenticated API access as a secure middleware layer
- Claude Code, Claude Desktop, and GitHub Copilot integration guides

---

## Orchestration Platforms

### Itential MCP Server

Enterprise orchestration platform with governance and compliance.

| Attribute | Details |
|-----------|---------|
| **Website** | [itential.com/cloud-platform/itential-mcp-server](https://www.itential.com/cloud-platform/itential-mcp-server/) |
| **Maintainer** | Itential |
| **Protocol** | MCP (stdio, HTTP) |

**Features:**
- AI-to-infrastructure mediation layer
- RBAC, SSO, and audit framework integration
- Workflow orchestration with policy governance
- Multi-vendor support (Cisco, Juniper, Arista, cloud providers)
- Closed-loop remediation
- ServiceNow integration

**Use Cases:**
- Compliance remediation (60% faster review times reported)
- AI-augmented troubleshooting
- CI/CD automation
- Ticket triage and resolution

**Resources:**
- [Itential MCP Server Overview](https://www.itential.com/cloud-platform/itential-mcp-server/)
- [From Scripting to Reasoning: The Future of Network Automation](https://www.itential.com/blog/company/ai-networking/from-scripting-to-reasoning-the-future-of-network-automation-with-mcp-agentic-ai/)
- [AI's Rewriting Automation & Itential's MCP Server](https://www.itential.com/blog/company/ai-networking/ais-rewriting-automation-itentials-mcp-server-is-your-guide/)

---

## Topology and Visualization

### Topolograph MCP Server

OSPF/IS-IS topology visualization with LLM integration.

| Attribute | Details |
|-----------|---------|
| **Website** | [topolograph.alyrica.net](https://topolograph.alyrica.net/) |
| **Repository** | topolograph-mcp-server |
| **Maintainer** | Alyrica |

**Supported Platforms:**
- Cisco
- Juniper
- Arista
- Nokia
- Mikrotik
- Huawei

**Features:**
- OSPF/OSPFv3/IS-IS topology visualization
- AI-driven network analysis
- Path calculation and prediction
- Network failure forecasting
- Automated troubleshooting

---

## Multi-Server Suites

### Network MCP Docker Suite

Docker-based suite of ten MCP servers for AI-driven network operations, featured on the Cisco Switzerland Technology Blog.

| Attribute | Details |
|-----------|---------|
| **Repository** | [github.com/pamosima/network-mcp-docker-suite](https://github.com/pamosima/network-mcp-docker-suite) |
| **Maintainer** | pamosima (Community) |
| **Latest Release** | v1.4.3 (May 2026) |

**Included servers:**
Meraki, NetBox, Catalyst Center, IOS XE (SSH), ThousandEyes, ISE, Splunk, Prometheus, ClickHouse, GitLab

**Resources:**
- [Network MCP Docker Suite - Cisco Switzerland Technology Blog](https://gblogs.cisco.com/ch-tech/network-mcp-docker-suite/)

---

## Watch List

Vendors pushing agentic AI for network operations but without a public MCP server yet:

- **ScienceLogic** — the Skylar One platform is heavily agentic-AI focused, but no public MCP server or MCP interface has been announced as of July 2026.
- **SolarWinds** — no official network-monitoring MCP server announced.
- **Arista** — CloudVision coverage remains community-maintained (see above); no official Arista MCP server yet.

---

## Use Cases

### Configuration Management

```
"Show me the running configuration of all border routers"
"Compare configurations between router-1 and router-2"
"Find any devices with default SNMP community strings"
```

### Compliance and Auditing

```
"Which devices are not running the approved firmware version?"
"Generate a compliance report for all switches in the datacenter"
"Identify devices missing NTP configuration"
```

### Troubleshooting

```
"Why is BGP session between router-a and router-b flapping?"
"Check for any interface errors on the core switches"
"Trace the path from server-1 to the internet gateway"
```

### Inventory Management

```
"How many Cisco switches do we have in the London site?"
"List all devices with end-of-life status"
"Create a new IP allocation for the new server subnet"
```

### Automated Remediation

```
"Fix the OSPF neighbor issue on router-3"
"Apply the standard security template to all access switches"
"Schedule firmware upgrade for non-critical devices during maintenance window"
```

---

## Getting Started

### Prerequisites

- MCP-compatible client (Claude Desktop, Cursor, VS Code with MCP extension, or custom client)
- Python 3.8+ (for most MCP servers)
- Network device credentials with appropriate access
- API tokens for management platforms (NetBox, CloudVision, etc.)

### Basic Setup Example (Junos MCP Server)

**1. Clone the repository:**

```bash
git clone https://github.com/Juniper/junos-mcp-server.git
cd junos-mcp-server
```

**2. Install dependencies:**

```bash
pip install -r requirements.txt
```

**3. Configure devices (`devices.json`):**

```json
{
  "router-1": {
    "host": "192.168.1.1",
    "username": "admin",
    "ssh_private_key_file": "/path/to/key.pem"
  }
}
```

**4. Configure MCP client (Claude Desktop example):**

```json
{
  "mcpServers": {
    "junos": {
      "command": "python",
      "args": ["jmcp.py"],
      "cwd": "/path/to/junos-mcp-server"
    }
  }
}
```

**5. Start interacting:**

```
"Show me the interfaces on router-1"
"What's the BGP neighbor status?"
"Retrieve the routing table"
```

---

## Security Considerations

### Authentication

- **Use SSH key-based authentication** instead of passwords
- **Rotate API tokens** regularly
- **Implement least-privilege access** for MCP server credentials

### Network Segmentation

- Run MCP servers in isolated network segments
- Use jump hosts or bastion servers for device access
- Implement firewall rules limiting MCP server communication

### Governance

- Enable **human-in-the-loop** for configuration changes
- Implement **audit logging** for all MCP operations
- Use platforms like **Itential** for policy enforcement

### Data Privacy

- Review corporate policies before sending network data to cloud LLMs
- Consider **on-premises LLM deployments** for sensitive environments
- Sanitize configuration outputs before processing

---

## Additional Resources

### Articles and Blog Posts

- [The Role of MCP in Scaling Agentic Network Automation](https://www.nanites.ai/post/the-role-of-mcp-servers-in-scaling-agentic-network-automation) - Nanites AI
- [Automating Network Lab Tasks with MCP Server and LLM](https://medium.com/@rvisnu/automating-network-lab-tasks-with-an-mcp-server-and-llm-assistance-chapter-2-d94c61986549) - Medium
- [Top 10 MCP Servers to Automate Your Infrastructure in 2026](https://medium.com/devops-ai-decoded/top-10-mcp-servers-to-automate-your-infrastructure-in-2026-5ef175318ac2) - Medium
- [The Ultimate MCP Guide for Network Automation: 56 Essential MCP Servers](https://www.itential.com/resource/guide/the-ultimate-mcp-guide-for-network-automation/) - Itential

### MCP Directories

- [PulseMCP](https://www.pulsemcp.com/) - MCP server directory and discovery
- [MCP.so](https://mcp.so/) - MCP server registry
- [Glama MCP Servers](https://glama.ai/mcp/servers) - MCP server directory with inspection tooling
- [mcpservers.org](https://mcpservers.org/) - Awesome MCP servers directory

### Official Documentation

- [Model Context Protocol Specification](https://modelcontextprotocol.io/)
- [Anthropic MCP Documentation](https://docs.claude.com/en/docs/agents-and-tools/mcp)

---

## Contributing

This is a community-maintained list. Contributions are welcome!

### How to Contribute

1. **Add a new MCP server:** Submit a PR with details about the server, including repository link, maintainer, supported platforms, and features.

2. **Update existing entries:** If you notice outdated information, please submit a correction.

3. **Share use cases:** Real-world examples help the community understand practical applications.

### Suggest an Addition

Know of a network infrastructure MCP server not listed here? [Open an issue](https://github.com/hecisaza/network-mcp-servers/issues) or submit a PR!

---

## License

This document is provided under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Feel free to share and adapt with attribution.

---

## Acknowledgments

Thanks to all the maintainers and contributors of these MCP servers who are advancing network automation with AI.

---

*Last Updated: July 2026*

*Maintained by the Network Automation Community*
