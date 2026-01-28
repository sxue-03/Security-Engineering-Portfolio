# SOC Lab — Incident Report Generator

## Objective
Automate the creation of standardized SOC incident reports using Python and Markdown templates to streamline post-incident documentation and ensure consistent report formats.

## Tools Used
- Python 3
- Markdown templates
- `datetime` module

## Skills Learned
- SOC incident documentation and reporting workflows
- Template-based content generation and automation
- Using Python to fill placeholders and insert timestamps
- Structuring incident reports with consistent sections (Summary, Indicators, Affected Systems, Actions)

## Steps Overview
1. Create Markdown templates for incident types (e.g., `templates/brute_force.md`, `templates/malware.md`) with placeholders such as `{{date}}`.
2. Implement `generate.py` to:
   - Read the selected template based on the incident type argument (e.g., `brute_force`, `malware`).
   - Replace `{{date}}` with the current timestamp.
   - Write the output to a new file (e.g., `incident_brute_force.md`, `incident_malware.md`).
3. From the `incident-generator` folder, run `python generate.py brute_force` or `python generate.py malware`.
4. Review the generated Markdown incident report and add case-specific details if needed.
5. Store the reports in a central location or convert them to PDF for sharing with stakeholders.

## Results
- Successfully generated consistent SOC incident reports using predefined templates.
- Automated insertion of timestamps and standardized sections (Summary, Indicators, Affected Systems, Recommended Actions).
- Created reusable report structures for common incident types such as brute-force attacks and malware detections.
- Simulated a realistic incident response documentation workflow used by SOC analysts.

## Next Steps
- Add more incident types (phishing, ransomware, data exfiltration, insider threat).
- Allow passing incident metadata (affected IPs, users, hosts) via JSON input or command-line arguments.
- Integrate a Markdown-to-PDF conversion step to produce final, shareable incident reports.
- Connect the generator to a ticketing system (Jira, ServiceNow, etc.) to automatically attach generated reports to incident tickets.
