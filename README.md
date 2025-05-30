# NIDS-Simulation (Suricata)
Network-Based Intrusion Detection System (Suricata)

This project displays the full setup of a custom Network-Based Intrusion Detection System using Suricata on Kali Linux. It detects and logs any malicious network activities coming in.

---

##Tools & Technologies
- Suricata
- Kali Linux
- Nmap
- Nikto
- jq (for parsing JSON)
- Custom Suricata rules

---

##Lab Setup

### Step 1: Install Suricata

sudo apt update && sudo apt install suricata -y

---

### Step 2: Enable & Start Suricata as a Service

sudo systemctl enable suricata
sudo systemctl start suricata
sudo systemctl status suricata

![Surciata Starting](docs/screenshots/suricata%20running.png).

---

### Step 3: Identify Network Interface
Run "ip a" to identify network interface, in this case it was eth0

---
Step 4: Run Suricata

sudo suricata -i eth0 -c /etc/suricata/suricata.yaml -l /var/log/suricata/

![Surciata Runs](docs/screenshots/suricata%20starts%20successfully.png).

---

### Step 5: Edit suricata.yaml to process local.rules

![Edit Suricata.yaml](docs/screenshots/edit%20suricata.yaml%to%20process%20local.rules.png).

---

### Step 6: Edit /etc/suricata/rules/local.rules to add custom rules

![Edit local.rules](docs/screenshots/suricata%20local%20rules.png).

Reload suricata after rule changes

sudo systemctl restart suricata

Rules loaded

![Rules loaded](docs/screenshots/rules%20successfully%20loaded.png).

---

### Step 7: Ran a ping scan against the target host

![ping scan](docs/screenshots/ping%20scan.png).

---

### Step 8: Log Analysis

cat /var/log/suricata/fast.log
cat /var/log/suricata/eve.json | jq

---

### Step 9: Suricata recieving traffic and alerts using custom rules

/var/log/suricata/eve.json feeding back results from Suricata custom rules

![Echo Request](docs/screenshots/echo%20request%20detected.png).

---

### Results

Custom rules implemented

Suricata successfully triggered alerts from custom rules implemented

### Future Improvements

Connect Suricata to a SIEM

Add rules for malware C2 or DGA detection










