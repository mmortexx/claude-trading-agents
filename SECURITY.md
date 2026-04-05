# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.x     | :white_check_mark: |

## Reporting a Vulnerability

We take security seriously. If you discover a security vulnerability, please report it responsibly.

### How to Report

1. **Do NOT** open a public GitHub issue for security vulnerabilities
2. Send a private vulnerability report through GitHub's [Security Advisory](https://github.com/mmortexx/claude-trading-agents/security/advisories/new) page
3. Include as much detail as possible:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Any suggested fixes (optional)

### Response Timeline

- **Initial Response**: Within 48 hours
- **Assessment**: Within 7 days
- **Resolution**: Depending on severity and complexity

### Scope

This project is software "as-is" without warranties. Users are responsible for:
- Securing their own API keys and credentials
- Proper configuration of exchange connections
- Compliance with their local regulations
- Risk management appropriate to their situation

## Security Best Practices for Users

- Never commit API keys or secrets to version control
- Use environment variables or secret management tools
- Implement proper access controls on your deployment environment
- Regularly rotate API credentials
- Monitor your trading systems for unusual activity
- Use read-only API keys when possible
- Network isolate your trading systems appropriately

## Qualifying Vulnerabilities

We are primarily interested in:
- Remote code execution vulnerabilities
- Authentication or authorization bypasses
- Data exposure of user credentials or trading data
- Injection attacks (API, configuration)
- Dependency vulnerabilities with known exploits

## Out of Scope

- Social engineering attacks
- Physical security issues
- Denial of service attacks on public endpoints you do not control
- Reports from automated scanning tools without demonstrated impact
