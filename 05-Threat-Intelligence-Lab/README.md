# Threat Intelligence Lab — VirusTotal Log Enricher

## Objective
Automate IP address reputation checks using the VirusTotal API, enrich indicators of compromise (IOCs), and generate CSV-based threat intelligence reports to support SOC investigations.

## Tools Used
- Python 3
- VirusTotal Public API
- CSV (for reporting)

## Skills Learned
- Working with REST APIs in Python
- Automating threat intelligence enrichment workflows
- Parsing text input files and handling JSON API responses
- Exporting structured data to CSV for analysis
- Supporting Tier 1 SOC investigations with enrichment tooling

## Steps Overview
1. Obtain a free VirusTotal API key and configure it in `enrich.py` (`API_KEY = "YOUR_API_KEY_HERE"`).
2. Prepare an input file (`sample_ips.txt`) containing one IP address per line.
3. From the `threat-intel-enricher` folder, run `python enrich.py sample_ips.txt`.
4. For each IP address, query the VirusTotal API for reputation and malicious score.
5. Write enrichment results to `enriched_results.csv` with columns such as `ip` and `malicious_score`.
6. Open the CSV file in Excel, Power BI, or another BI tool to review, sort, and visualize threat levels across IP addresses.

## Results
- Built a Python-based enrichment tool that automates IP reputation lookups using VirusTotal.
- Successfully processed lists of IP addresses and generated `enriched_results.csv` as a clean report.
- Provided a simple way for analysts to quickly assess which IPs may be malicious or suspicious.
- Demonstrated an end-to-end enrichment workflow similar to real SOC processes.

## Next Steps
- Add support for domains and URLs in addition to IP addresses.
- Include additional VirusTotal attributes (e.g., categories, detection ratios, last analysis date).
- Integrate with other threat intelligence providers (AbuseIPDB, GreyNoise, etc.) for multi-source enrichment.
- Build a small Streamlit dashboard to visualize malicious scores and filter IOCs interactively.

---
