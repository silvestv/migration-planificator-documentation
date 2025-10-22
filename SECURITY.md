# Security Policy

## 🔒 Security Commitment

**@silvestv/migration-planificator** is committed to protecting your codebase and maintaining the highest security standards.

---

## 🛡️ Privacy & Data Collection

### What This Tool Does NOT Do

This CLI tool is designed with **privacy-first principles**:

- ❌ **No Data Collection** - We do not collect, store, or transmit any data from your codebase
- ❌ **No Telemetry** - Zero usage tracking or analytics
- ❌ **No Network Requests** - The tool runs entirely offline (except for npm package download)
- ❌ **No External APIs** - All analysis is performed locally using AST parsing libraries
- ❌ **No Code Upload** - Your source code never leaves your machine

### How It Works

1. **Local Execution Only** - All code analysis happens on your machine
2. **AST Parsing** - Uses `ts-morph` and `@angular/compiler` for local code analysis
3. **File System Access** - Only reads files in the specified project directory
4. **Output Generation** - Generates HTML reports locally in the `output/` directory

---

## 🔍 Package Integrity

### npm Package Signing

All packages published to the npm registry are **automatically signed** by npm to ensure integrity:

- ✅ Packages are cryptographically signed upon publication
- ✅ Signature verification happens automatically during `npm install`
- ✅ Tampering detection is built into npm's infrastructure

### Verify Package Contents

You can audit the published package contents at any time:

```bash
# Download the package tarball
npm pack @silvestv/migration-planificator

# Inspect the contents
tar -tzf silvestv-migration-planificator-*.tgz

# Or view files metadata directly from npm registry
npm view @silvestv/migration-planificator files
```

### Published Files

Only the following files are included in the published package (defined in `package.json` `files` field):

- `dist/src/` - Compiled TypeScript source
- `dist/client.bundle.js` - Client-side JavaScript bundle
- `dist/styles.css` - Compiled CSS styles
- `README.md` - English documentation
- `README.fr.md` - French documentation
- `LICENSE` - License information

**No sensitive files** (`.env`, credentials, source maps, test files) are included.

---

## 🚨 Reporting a Vulnerability

We take security vulnerabilities seriously. If you discover a security issue, please follow responsible disclosure:

### Contact Information

**Primary Contact:**
- **Name:** Victor SILVESTRE
- **Email:** victor.silvestre.dev@gmail.com
- **Role:** Freelance Software Engineer (FR) - Angular / NodeJS & TypeScript Developer

### Reporting Process

1. **DO NOT** open a public GitHub issue for security vulnerabilities
2. Email details to: **victor.silvestre.dev@gmail.com**
3. Include:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if any)

### Response Timeline

- **Initial Response:** Within 48 hours
- **Status Update:** Within 7 days
- **Fix & Disclosure:** Coordinated with reporter

### What to Expect

1. Acknowledgment of your report within 48 hours
2. Investigation and validation of the issue
3. Development of a fix (if confirmed)
4. Coordinated disclosure timeline
5. Credit in release notes (if desired)

---

## 🔐 Security Best Practices

### For Users

When using this tool:

- ✅ Install from official npm registry: `npm install @silvestv/migration-planificator`
- ✅ Verify package integrity using `npm audit`
- ✅ Review generated reports before sharing (may contain file paths/code snippets)
- ✅ Use specific version pinning in production: `npm install @silvestv/migration-planificator@x.y.z`
- ⚠️ Avoid running as root/administrator unless necessary

### For Contributors

When contributing (for future community contributions):

- Use `npm audit` to check dependencies for vulnerabilities
- Follow TypeScript strict mode guidelines
- Never commit secrets, API keys, or credentials
- Run tests before submitting: `npm test`

---

## 📋 Dependencies Security

This project uses minimal, well-maintained dependencies:

### Production Dependencies

- **ts-morph** (^27.0.0) - TypeScript AST manipulation
- **@angular/compiler** (^20.3.4) - Angular HTML template parsing
- **chart.js** (^4.4.0) - Client-side chart rendering
- **tailwindcss** (^4.1.14) - CSS framework
- **typescript** (^5.9.3) - TypeScript compiler

### Security Audits

Run regular security audits:

```bash
# Check for known vulnerabilities
npm audit

# Fix automatically (if possible)
npm audit fix

# View detailed report
npm audit --json
```

---

## 🏢 License & Liability

This software is dual-licensed under:

- **AGPL-3.0** (for open-source/community use)
- **Commercial License** (for business use without AGPL obligations)

### Disclaimer

This tool is provided **"AS IS"** without warranty of any kind. See [LICENSE](https://github.com/silvestv/migration-planificator-documentation/blob/master/LICENSE) for full terms.

### Commercial Support

For enterprise security requirements or private security audits:

📧 Contact: victor.silvestre.dev@gmail.com

---

## 📚 Additional Resources

- 📦 [NPM Package](https://www.npmjs.com/package/@silvestv/migration-planificator)
- 📧 [Contact for Support](mailto:victor.silvestre.dev@gmail.com)

---

**Last Updated:** January 2025

© 2025 Victor SILVESTRE - All rights reserved
