
# LogChef Deployment Guide

## Local Docker Setup
LogChef runs seamlessly out of the box when using local Docker.

## VM Hosting Challenges

### Authentication Issues with Dex
When hosting LogChef on a VM, Dex authentication fails by default. A domain is required for proper functionality.

### Solutions

#### Using nip.io Domain
If you don't have a registered domain, use [nip.io](https://nip.io) as a workaround:
- Provides dynamic DNS for IP addresses
- Enables Dex authentication without domain registration

#### SSL/TLS Certificate Configuration
Self-signed certificates are necessary due to certificate validation issues in VM environments.

**Steps:**
1. Generate self-signed certificates for your domain/nip.io address
2. Configure Nginx as a reverse proxy on the server
3. Route APIs through Nginx with proper certificate binding

### Configuration Overview
```
VM Server
├── Nginx (reverse proxy with SSL/TLS)
├── LogChef application
└── Dex authentication service
```
