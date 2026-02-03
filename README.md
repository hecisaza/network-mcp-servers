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
- [Network Management Platforms](#network-management-platforms)
- [Orchestration Platforms](#orchestration-platforms)
- [Topology and Visualization](#topology-and-visualization)
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

## Network Management Platforms

### NetBox MCP Server (Read-Write)

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

### NetBox MCP Server (Official - Read-Only)

Official read-only MCP server from NetBox Labs.

| Attribute | Details |
|-----------|---------|
| **Maintainer** | NetBox Labs |
| **Access** | Read-only (safe for production) |

**Features:**
- Query device inventory
- Retrieve IP allocations
- Site and tenant information
- Safe production deployment

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

### MCP Directories

- [PulseMCP](https://www.pulsemcp.com/) - MCP server directory and discovery
- [MCP.so](https://mcp.so/) - MCP server registry

### Official Documentation

- [Model Context Protocol Specification](https://modelcontextprotocol.io/)
- [Anthropic MCP Documentation](https://docs.anthropic.com/en/docs/agents-and-tools/mcp)

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

*Last Updated: February 2026*

*Maintained by the Network Automation Community*
