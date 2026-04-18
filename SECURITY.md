# Security Policy

## Supported Versions

Currently supported versions of Tingly-Box via Homebrew:

| Version           | Supported     |
| ----------------- | ------------- |
| Latest release    | ✅             |
| Previous releases | ⚠️ Best effort |

## Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly.

### How to Report

**Do NOT open a public issue.**

Instead, send your report privately:

1. **Email**: Send details to the security team at the project's security contact
2. **GitHub Advisory**: Use [GitHub's private vulnerability reporting](https://github.com/tingly-dev/tingly-box/security/advisories)

### What to Include

Please include as much of the following information as possible:

- **Description**: A clear description of the vulnerability
- **Steps to Reproduce**: Detailed steps to reproduce the issue
- **Impact**: Potential impact of the vulnerability
- **Affected Versions**: Which versions are affected
- **Proposed Fix** (optional): If you have a fix, please include it

### Response Timeline

- **Initial Response**: Within 48 hours
- **Detailed Response**: Within 7 days
- **Fix Timeline**: Depends on severity and complexity

### Security Policy

1. **Verification**: We will verify the vulnerability
2. **Assessment**: Determine severity and impact
3. **Fix Development**: Develop a patch
4. **Release**: Coordinate release of fix
5. **Disclosure**: Public disclosure after fix is available

## Supported Environments

The Homebrew formula installs Tingly-Box in user-space. Security considerations:

- Binaries are installed to `/usr/local/bin` or `/opt/homebrew/bin`
- Configuration files are stored in user home directory
- No system-level services are automatically enabled
- Network access is controlled by the application, not Homebrew

## Security Best Practices

For Users:

1. **Keep Updated**: Always use the latest version (`brew upgrade tingly-box`)
2. **Verify Checksums**: Homebrew automatically verifies SHA256 checksums
3. **Review Permissions**: Be aware of network and file permissions
4. **Report Issues**: Report suspicious behavior immediately

## Security Audits

Periodic security audits are conducted to ensure:
- Dependencies are up-to-date
- No known vulnerabilities in dependencies
- Secure coding practices are followed
- Proper input validation and sanitization

## Dependency Security

The formula includes:
- Direct binary downloads from official releases
- SHA256 checksum verification
- No build-time dependencies
- No runtime dependencies that affect security

## Disclosure Policy

We follow responsible disclosure practices:
1. Private report and verification
2. Fix development and testing
3. Coordinated release
4. Public disclosure with fix

## Contact

For general security questions:
- Open an issue with the "security" label
- Contact the maintainers privately for sensitive matters

## Acknowledgments

We thank all researchers who responsibly report vulnerabilities to help improve Tingly-Box security.
