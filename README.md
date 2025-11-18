# YARA + Wazuh Package for Ubuntu 18.04

Self-contained archive to install YARA 4.5.4 with optional Wazuh integration on Ubuntu 18.04. No internet required during install.

## What’s inside
- `yara-wazuh-complete-ubuntu18-FIXED.tar.gz`
  - OpenSSL 3.0 libraries (prebuilt)
  - YARA 4.5.4 binaries
  - YARA rules (~11MB)
  - Wazuh active response script
  - Offline installer `install.sh`

## Download

Option A: Browser
- Open the repository page and download the file from the root: `yara-wazuh-complete-ubuntu18-FIXED.tar.gz`

Option B: Terminal (wget)
```bash
wget https://raw.githubusercontent.com/chojuninengu/delete/main/yara-wazuh-complete-ubuntu18-FIXED.tar.gz -O yara-wazuh-complete-ubuntu18-FIXED.tar.gz
```

Option C: Git clone
```bash
git clone https://github.com/chojuninengu/delete.git
cd delete
```

## Install (≈2 minutes, offline)
```bash
# If you downloaded just the file
tar -xzf yara-wazuh-complete-ubuntu18-FIXED.tar.gz
cd complete-yara-package-fixed/
chmod +x install.sh
./install.sh

# If you cloned the repo
cd delete
tar -xzf yara-wazuh-complete-ubuntu18-FIXED.tar.gz
cd complete-yara-package-fixed/
chmod +x install.sh
./install.sh
```

## Verify
```bash
yara --version
# Expected: 4.5.4

echo 'rule test { strings: $a = "hello" condition: $a }' > test.yar
echo 'hello world' > test.txt
yara test.yar test.txt
# Expected: test test.txt
```

## Wazuh integration (optional)
If Wazuh agent is installed on the machine, the installer will automatically place:
- Rules at `/var/ossec/ruleset/yara/rules/yara_rules.yar`
- Active response at `/var/ossec/active-response/bin/yara.sh`

If the agent is not present, YARA will still be installed and usable standalone.

## Requirements
- Ubuntu 18.04
- sudo privileges