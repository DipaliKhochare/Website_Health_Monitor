# Website_Health_Monitor
Technologies used : Python, Bash, Linux (cron), Git/GitHub, TCP/IP, DNS, HTTP, TLS/SSL

A small Python + Bash tool that checks whether websites are healthy and logs the results.

## What it checks
| Layer | Check |
|-------|-------|
| DNS | Domain resolves to an IP |
| TCP/IP | Connection succeeds on port 443 |
| TLS/SSL | Certificate expiry (warns under 30 days) and TLS version |
| HTTP | Status code and response time |

## Tech used
Python, Bash, Linux (cron), Git, TCP/IP, DNS, HTTP, TLS/SSL

## Setup
```bash
git clone <your-repo-url>
cd website-health-monitor
pip install -r requirements.txt
chmod +x run.sh
```

## Usage
```bash
python3 monitor.py            # human-readable output
python3 monitor.py --json     # one JSON object per line
python3 monitor.py -f my_sites.txt
./run.sh                      # appends results to logs/health.log
```

Edit `sites.txt` to change which domains are checked.

## Schedule with cron (every 5 minutes)
```bash
crontab -e
*/5 * * * * /full/path/to/website-health-monitor/run.sh
```

## Sample output
```
2026-10-19T02:40:00+00:00 [OK  ] github.com {'ip': '140.82.112.4', 'tls_version': 'TLSv1.3', 'cert_days_left': 85, 'cert_warning': False, 'status': 200, 'latency_ms': 210}
```
