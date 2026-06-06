# Security Tools

Personal scripts and utilities for recon, parsing, automation and defensive security workflows.

## Purpose

This repository contains small tools built for learning, lab work, defensive analysis and workflow automation.

The goal is to keep practical scripts organized, documented, reusable and safe by default.

This is not a dumping ground for random one-liners, broken experiments or scripts with hardcoded secrets. Para eso ya está la carpeta `Descargas`, ese cementerio universal.

## Structure

```text
security-tools/
├── recon/
├── web/
├── parsing/
├── automation/
├── linux/
├── network/
├── cti/
├── templates/
└── docs/
```

## Categories

- `recon`: enumeration helpers, Nmap wrappers and target organization.
- `web`: utilities for web security labs and HTTP testing.
- `parsing`: log parsers, JSON/CSV processors and report helpers.
- `automation`: scripts to reduce repetitive manual work.
- `linux`: Linux administration and security helpers.
- `network`: network checks, scans and diagnostics.
- `cti`: Threat Intelligence enrichment, IOC handling and reporting.
- `templates`: reusable script and report templates.
- `docs`: notes, usage examples and methodology.

## Templates

Recommended template:

- `templates/tool-template.md`  
  Standard template for documenting tools, usage, requirements, output and safety notes.

If the template does not exist yet, create it under:

```text
security-tools/templates/tool-template.md
```

## Tool folder format

Each tool should include:

```text
tool-name/
├── README.md
├── tool.py
├── requirements.txt
├── examples/
└── docs/
```

For Bash tools:

```text
tool-name/
├── README.md
├── tool.sh
├── examples/
└── docs/
```

For larger tools:

```text
tool-name/
├── README.md
├── src/
├── config/
├── examples/
├── docs/
├── tests/
└── requirements.txt
```

## Tool README format

Each tool should include:

```text
# Tool Name

## Purpose
What the tool does.

## Scope
Where it is safe and intended to be used.

## Features
Main capabilities.

## Requirements
Dependencies and tested environment.

## Installation
How to install dependencies.

## Usage
Commands and examples.

## Output
Expected files, logs or terminal output.

## Safety Notes
Warnings, limits and safe defaults.

## Known Limitations
What the tool does not do.

## Roadmap
Planned improvements.
```

## Rules

- Defensive and authorized use only.
- No credential theft.
- No stealth, persistence or evasion tooling.
- No destructive actions without clear warnings.
- No hardcoded secrets.
- No hardcoded third-party targets.
- No API keys, tokens, cookies or private keys.
- Scripts should include usage notes and safe defaults.
- Scripts should handle errors when possible.
- Scripts should document expected output.
- Inputs should be validated when possible.

## Safe defaults

Tools should prefer safe behavior by default:

```text
Default mode: non-destructive
Target input: explicit
Output: local file or stdout
Logging: clear and minimal
Secrets: never hardcoded
External calls: documented
Rate limits: conservative
```

Avoid:

```text
Automatic destructive changes
Silent failures
Hardcoded targets
Hardcoded credentials
Unexpected network scanning
Unclear output
No help message
```

## Recommended script behavior

A useful script should support at least:

```text
-h / --help
clear usage examples
input validation
error messages
safe output location
exit codes
```

For Python tools:

```python
if __name__ == "__main__":
    main()
```

For Bash tools:

```bash
set -euo pipefail
```

Use `set -euo pipefail` carefully. It is useful, but it can also make scripts fail hard if not handled properly, because Bash enjoys making simple things weird.

## Recommended folders

### `recon/`

Use for:

```text
Nmap helpers
target workspace creation
service enumeration wrappers
subdomain helpers for authorized scope
report generators
```

### `web/`

Use for:

```text
HTTP helpers
header checks
URL parsing
lab request helpers
controlled fuzzing wrappers
```

### `parsing/`

Use for:

```text
JSON parsers
CSV processors
log parsers
Nmap XML parsers
IOC extractors
```

### `automation/`

Use for:

```text
repetitive workflow automation
report generation
file organization
backup helpers
scheduled lab tasks
```

### `linux/`

Use for:

```text
Linux checks
system info helpers
service checks
permission audits
local lab administration
```

### `network/`

Use for:

```text
connectivity checks
port checks
DNS helpers
routing checks
local network diagnostics
```

### `cti/`

Use for:

```text
IOC formatting
hash enrichment helpers
STIX/TAXII experiments
OpenCTI helpers
MISP helpers
report formatting
```

## Recommended commands

### Create a Python tool workspace

```bash
mkdir -p tool-name/{examples,docs}
touch tool-name/README.md
touch tool-name/tool.py
touch tool-name/requirements.txt
```

### Create a Bash tool workspace

```bash
mkdir -p tool-name/{examples,docs}
touch tool-name/README.md
touch tool-name/tool.sh
chmod +x tool-name/tool.sh
```

### Python virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Basic shellcheck

```bash
shellcheck tool.sh
```

### Basic Python syntax check

```bash
python3 -m py_compile tool.py
```

## Documentation checklist

Before publishing a tool:

- [ ] Purpose is clear.
- [ ] Scope is clear.
- [ ] Usage examples are included.
- [ ] Dependencies are listed.
- [ ] Expected output is documented.
- [ ] Errors are handled or documented.
- [ ] No secrets are hardcoded.
- [ ] No third-party targets are hardcoded.
- [ ] Dangerous behavior is not default.
- [ ] Safety notes are included.
- [ ] License/disclaimer context is clear.

## Security checklist

Before publishing a script:

- [ ] No API keys.
- [ ] No tokens.
- [ ] No passwords.
- [ ] No cookies.
- [ ] No private keys.
- [ ] No sensitive paths.
- [ ] No real victim data.
- [ ] No destructive commands without warnings.
- [ ] No stealth behavior.
- [ ] No persistence behavior.
- [ ] No evasion behavior.
- [ ] No credential theft logic.

## Commit message examples

Good commit messages:

```text
Add Nmap report parser
Add recon workspace helper
Improve JSON IOC extractor
Fix error handling in log parser
Add usage examples for web header checker
```

Bad commit messages:

```text
update
fix
stuff
final
test
asdasd
```

`asdasd` puede ser técnicamente válido. También lo es usar cinta aisladora para sostener un rack. No abusemos.

## Disclaimer

This repository is for educational, defensive and authorized use only.

Do not use any tool, script or command from this repository against systems you do not own or do not have explicit permission to test.

Do not use this material for unauthorized access, disruption, credential theft, persistence, evasion or abuse.

**Menos humo, más evidencia.**
