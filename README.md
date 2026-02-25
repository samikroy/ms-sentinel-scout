# Microsoft Sentinel Scout

**Microsoft Sentinel Scout** is a lightweight, plug-and-play GitHub Actions tool that automatically runs KQL (Kusto Query Language) queries against your Azure Log Analytics / Microsoft Sentinel workspace and produces a styled HTML assessment report — ideal for health checks, readiness reviews, and customer-facing documentation.

---

## ⚙️ Features

| Feature | Description |
|---|---|
| 🔍 KQL Query Automation | Runs customizable checks via the Log Analytics REST API |
| 📋 Real-Time Markdown Logs | Easy-to-read GitHub Actions output during each run |
| 📄 Styled HTML Report | Downloadable assessment report for customer sharing |
| 🔐 Secure Login | Authenticates using an Azure Service Principal |
| 🧰 Plug-and-Play | Just configure secrets, add queries, and run |

---

## 🔍 Report Preview

![ms-sentinel-scout-report](https://github.com/user-attachments/assets/79645c9b-553e-41e5-b008-b38ce89d235a)

Sample report: https://github.com/samikroy/ms-sentinel-scout/blob/main/ms-sentinel-scout-report.html

---

## 📁 Repo Structure

```
.
├── scripts/
│   ├── generate-ms-sentinel-scout-report.ps1  # Main PowerShell script — runs KQL queries and builds the HTML report
│   └── kql-queries.txt                        # List of KQL queries with display aliases
├── .github/
│   └── workflows/
│       └── Generate MS Sentinel Scout Report.yml  # Scheduled GitHub Actions workflow
├── ms-sentinel-scout-report.html              # Sample generated report
└── README.md
```

---

## 🔐 Required Permissions

The solution authenticates using an **Azure Service Principal** that must be granted one of the following roles on the Log Analytics workspace:

- **Microsoft Sentinel Reader**, or
- **Log Analytics Reader**

---

## ⚙️ How It Works

![Define rules → Run Pipeline → Generate Report](https://github.com/user-attachments/assets/dc4d7578-c57a-4223-b8bb-8d3d1b3012f5)

1. The GitHub Actions workflow runs on a daily schedule (or on demand).
2. The PowerShell script authenticates to Azure using Service Principal credentials.
3. Each KQL query defined in `scripts/kql-queries.txt` is executed against the Log Analytics workspace via the REST API.
4. Results are assembled into a single styled HTML report and uploaded as a workflow artifact.

---

## 🚀 How to Run

1. **Clone this repo**

2. **Configure Repository Secrets** — add the following secrets at  
   `Settings → Secrets and variables → Actions`:

   | Secret | Description |
   |---|---|
   | `AZURE_CLIENT_ID` | Service Principal Application (client) ID |
   | `AZURE_CLIENT_SECRET` | Service Principal client secret |
   | `AZURE_TENANT_ID` | Azure Active Directory tenant ID |
   | `LOG_ANALYTICS_WORKSPACE_ID` | Log Analytics workspace ID |

   <img width="609" height="243" alt="Repository secrets configuration" src="https://github.com/user-attachments/assets/a75163a5-f057-47f3-becf-73c35d88a6e2" />

3. **Review (and optionally adjust) the workflow schedule** in  
   `.github/workflows/Generate MS Sentinel Scout Report.yml`  
   *(default: daily at midnight UTC)*

   <img width="394" height="164" alt="Workflow schedule" src="https://github.com/user-attachments/assets/0d932924-03ef-44b1-b638-be7e1b7cbccb" />

4. **Run the workflow** — the HTML report will be uploaded as a GitHub Actions artifact.

---

## 🧰 Got Ideas or Issues?

Submit them here: https://github.com/samikroy/ms-sentinel-scout/issues

Reach out to samik.n.roy@gmail.com for any queries.
