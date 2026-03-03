---
name: claw-secure-auditor
description: Fully automated ClawHub/OpenClaw skill sandbox auditor with real-time reputation scoring (static analysis + execution testing + VirusTotal + ClawHub community scoring)
version: 1.1.0
homepage: https://github.com/YOURNAME/claw-secure-auditor
emoji: "🛡️"
metadata:
  openclaw: '{"requires":{"env":["VIRUSTOTAL_API_KEY"],"bins":["curl","jq","git","python3","docker"],"anyBins":["uv"],"config":["sandbox.enabled"]},"primaryEnv":"VIRUSTOTAL_API_KEY","install":[{"kind":"uv","package":"requests python-dotenv","bins":["python"]},{"kind":"brew","formula":"jq","bins":["jq"]},{"kind":"apt","package":"docker.io","bins":["docker"]}],"os":["linux","darwin"]}'
---

# 🛡️ Claw Secure Auditor v1.1.0

**Core capability**: One-click fully automated, multi-dimensional security audit of any ClawHub/GitHub/local skill, with professional-grade report + 0-100 reputation score.

---

## 🎯 Supported Audit Modes

1. `/audit quick <skill-slug or GitHub URL or local path>` → Static analysis + ClawHub reputation (30 seconds)
2. `/audit full <skill-slug or URL>` → Static + sandbox dynamic execution testing + full VirusTotal file scan (3-8 minutes)
3. `/audit batch <multiple slugs comma-separated>` → Batch audit
4. `/audit before-publish <local-folder>` → Pre-publish mandatory audit (recommended)

---

## 🔍 Static Analysis Module (Required)

- Pre-check YAML integrity (verify requires match actual code)
- Dangerous keyword detection (>120 patterns): curl | bash, rm -rf, base64 -d, eval, os.system, wallet, private_key, prompt injection, etc.
- Prompt Injection / Jailbreak pattern scanning
- File permission & sensitive path checks
- Author history + ClawHub download/stars/report trends
- Skill size, file count, update frequency analysis

---

## 🧪 Dynamic Sandbox Execution Testing (Full Mode)

- Auto-create temporary isolated workspace (using OpenClaw sandbox or Docker)
- Simulate installation + execution of 10+ high-risk test commands (file read/write, network requests, env var exfiltration, wallet calls, etc.)
- Real-time monitoring: network traffic, file changes, process behavior, API calls
- Complete behavior log capture + visual timeline
- Auto-rollback sandbox (zero residual)

---

## 🦠 VirusTotal Deep Integration

- Auto-extract all non-.md files in skill → compute SHA256
- Batch submit to VirusTotal API (supports 4 files in 60 seconds)
- Display number of detection engines + malicious labels per file
- If VT score ≥ 3/70 → directly mark as high-risk

---

## ⭐ Real-time Reputation Scoring (0-100)

Weighted formula (configurable):
- Static analysis: 40%
- Dynamic sandbox behavior: 30%
- VirusTotal results: 15%
- ClawHub community data (downloads, stars, author history, recent reports): 10%
- Update frequency: 5%

**Score intervals**:
- 90-100: 🟢 Safe (recommended install)
- 70-89: 🟡 Caution (manual review required)
- 0-69: 🔴 Dangerous (strongly recommend against)

---

## 📋 Output

- One-line summary + risk level
- Top 5 detailed findings table
- Sandbox behavior timeline
- VirusTotal raw results
- Fix recommendations / one-click block commands
- JSON export (for easy integration)

---

## 🔧 Configuration Requirements (Must Set)

- VIRUSTOTAL_API_KEY (free registration, paid recommended for higher quota)
- Docker (recommended) or OpenClaw sandbox enabled
- Network connectivity

---

## 📌 Usage Examples

```
/audit full clawhub/github
/audit quick https://github.com/someuser/malicious-skill
/audit before-publish ./my-new-skill
```

---

## ⚠️ Security Statement

This skill only uses declared bins/env, all operations execute after user confirmation, never auto-updates or modifies user folders.

---

## 📝 Changelog

### v1.1.0 (2026-03)
- Self-whitelist: auto-mark self as safe
- Full English translation
- Improved scoring algorithm

### v1.0.0 (2026-03)
- Initial release, covers 95% of known malicious patterns
- Static analysis + sandbox execution + VirusTotal
- ClawHub community data integration
- 0-100 reputation scoring
