# 🛡️ Claw Secure Auditor

Fully automated ClawHub/OpenClaw skill sandbox auditor with real-time reputation scoring (static analysis + execution testing + VirusTotal + ClawHub community scoring).

---

## Quick Start

### 1. Configure

```bash
# Set VirusTotal API Key (optional, for full mode)
export VIRUSTOTAL_API_KEY="your-api-key-here"
```

### 2. Use

```bash
# Enter file directory
cd /path/to/your/files

# Quick audit (static + ClawHub reputation)
python3 scripts/auditor.py quick ./my-skill

# Full audit (static + sandbox + VirusTotal)
python3 scripts/auditor.py full ./my-skill

# Pre-publish audit
python3 scripts/auditor.py before-publish ./my-new-skill

# JSON report output
python3 scripts/auditor.py quick ./my-skill --json
```

---

## Audit Modes

| Mode | Description | Time |
|------|-------------|------|
| quick | Static analysis + ClawHub reputation | 30 sec |
| full | Static + sandbox + VirusTotal | 3-8 min |
| batch | Batch audit multiple skills | depends |
| before-publish | Pre-publish mandatory audit | 30 sec |

---

## Reputation Score

| Score | Level | Color | Recommendation |
|-------|-------|-------|-----------------|
| 90-100 | Safe | 🟢 | Recommended install |
| 70-89 | Caution | 🟡 | Manual review required |
| 0-69 | Dangerous | 🔴 | Strongly recommend against |

---

## Features

- ✅ 120+ dangerous keyword detection
- ✅ Static analysis YAML integrity
- ✅ Dynamic sandbox execution testing
- ✅ VirusTotal file scanning
- ✅ ClawHub community data integration
- ✅ 0-100 reputation score
- ✅ JSON report export

---

## Full Documentation

Complete usage guide in `SKILL.md`.

---

## License

MIT License

---

*Version: v1.1.0*
