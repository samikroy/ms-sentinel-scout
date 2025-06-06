# Microsoft Sentinel Scout

⚙️ Features
Feature	Description

🔍 KQL Query Automation	Runs customizable checks via Log Analytics API <br/>
📋 Real-Time Markdown Logs	Easy-to-read GitHub Actions output <br/>
📄 Styled HTML Report	Downloadable assessment report for customer sharing <br/>
🔐 Secure Login	Uses Azure Service Principal credentials <br/>
🧰 Plug-and-Play	Just configure secrets, add queries, and run <br/>

📁 Repo Structure

```
.
├── scripts/
│   ├── generate-ms-sentinel-scout-report.ps1  # Main script to run checks and export HTML
│   └── kql-queries.txt               # List of readiness queries with alias
├── .github/
│   └── workflows/Generate MS Sentinel Scout Report.yml  # GitHub Actions workflow
└── README.md                         # You're reading it

```

The solution on a service principaln with the 
Microsoft Sentinel Reader Permission.


Reach out to samik.n.roy@gmail.com for any queries.
