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
- `LICENSE` - Apache 2.0 License
- `NOTICE` - Copyright and attribution notices

**No sensitive files** (`.env`, credentials, source maps, test files) are included.

---

## 🚨 Reporting a Vulnerability

We take security vulnerabilities seriously. If you discover a security issue, please follow responsible disclosure:

### Contact Information

**Primary Contact:**
- **Name:** Victor SILVESTRE
- **Email:** victor.silvestre.dev@gmail.com
- **Role:** Full-Stack Developer - Angular/Node.js/TypeScript Specialist

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

## 📝 Security Best Practices

### For Users

When using this tool:

- ✅ Install from official npm registry: `npm install @silvestv/migration-planificator`
- ✅ Verify package integrity using `npm audit`
- ✅ Review generated reports before sharing (may contain file paths/code snippets)
- ✅ Use specific version pinning in production: `npm install @silvestv/migration-planificator@x.y.z`
- ⚠️ Avoid running as root/administrator unless necessary

### For Contributors

When contributing:

- Use `npm audit` to check dependencies for vulnerabilities
- Follow TypeScript strict mode guidelines
- Never commit secrets, API keys, or credentials
- Run tests before submitting: `npm test`
- Sign commits with GPG when possible

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

## 📜 License & Liability

This software is licensed under the **Apache License, Version 2.0**.

### Key License Terms

- ✅ **Commercial Use** - Allowed for any purpose
- ✅ **Modification** - Can be modified and distributed
- ✅ **Distribution** - Can be distributed freely
- ✅ **Patent Grant** - Includes express grant of patent rights
- ✅ **Private Use** - Can be used privately without restrictions

### Required When Using

- 📝 Include the LICENSE file
- 📝 Include the NOTICE file (if present)
- 📝 State changes made to the code (if modified)

### Disclaimer

This software is provided **"AS IS"** without warranty of any kind, express or implied. See the [LICENSE](LICENSE) file for the full license terms and limitations.

```
Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
```

### Enterprise Support

For enterprise security requirements, SLAs, or private security audits:

📧 Contact: victor.silvestre.dev@gmail.com

---

## 📚 Additional Resources

- 📦 [NPM Package](https://www.npmjs.com/package/@silvestv/migration-planificator)
- 📖 [Apache 2.0 License Text](http://www.apache.org/licenses/LICENSE-2.0)
- 🔐 [npm Security Documentation](https://docs.npmjs.com/auditing-package-dependencies-for-security-vulnerabilities)
- 📧 [Security Contact](mailto:victor.silvestre.dev@gmail.com)

---

## 🏢 Corporate Usage

This project is suitable for use in enterprise environments:

- ✅ **Clear licensing** under Apache 2.0
- ✅ **No GPL dependencies** that could affect your proprietary code
- ✅ **Patent protection** included in the license
- ✅ **Professional support** available upon request

---

**Last Updated:** January 2025  
**Version:** Aligned with Apache License 2.0

© 2025 Victor SILVESTRE

Licensed under the Apache License, Version 2.0. You may obtain a copy of the License at:
http://www.apache.org/licenses/LICENSE-2.0
