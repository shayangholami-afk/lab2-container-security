# Lab 2: Container Security

## Vad jag gjort
1. **Vulnerable image**: python:3.8 + Flask 1.0.0 → **1492 CVEs**, 378MB
2. **Hardened image**: python:3.12-slim + non-root user + Flask 3.0.0 → **116 CVEs**, 50MB
3. **Trivy scanning**: scan-before.txt (1.5MB) vs scan-after.txt (49 rader)
4. **SBOM**: CycloneDX-format för compliance (EU Cyber Resilience Act)
5. **Gatekeeper**: Policy som kräver `team`-label på pods i `chas-ff` namespace

## Verktyg
- **Trivy**: Vuln-scanning
- **Docker**: Container builds
- **Gatekeeper/OPA**: Kubernetes policy enforcement

