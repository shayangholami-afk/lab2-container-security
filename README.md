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


## 🧠 Reflektion (5-10 meningar)

**Container-säkerhet:** Lärde mig att minimera attackytan är kritiskt. Non-root user hindrar privilege escalation, slim-baser (python:3.12-slim) har färre sårbarheter än fulla images, och att patcha Flask 1.0.0→3.0.0 eliminerar kritiska CVEs. Trivy kvantifierar risker konkret - 1492→116 CVEs är dramatisk förbättring!

**SBOM-importans:** Ger full transparens i supply chain med CycloneDX-JSON. Listar alla komponenter (OS + Python deps) för snabb CVE-hantering. Krävs av EU Cyber Resilience Act för compliance och automatiserad riskhantering i CI/CD.

**Gatekeeper förändrar K8s:** Policy-as-code istället för manuell granskning. "require-team-label" nekar "Bad Pod" automatiskt via admission webhook. Tvingar säkra vanor, förenklar audit/compliance, flyttar säkerhet "left" i DevOps. Gör DevSecOps praktiskt!
