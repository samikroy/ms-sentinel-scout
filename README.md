# Microsoft Sentinel Scout

**Microsoft Sentinel Scout** is a GitHub Actions-powered tool that runs KQL queries against a Log Analytics workspace and produces a styled HTML assessment report. It is designed to help security teams quickly review their Microsoft Sentinel environment on a scheduled or on-demand basis.

## ✨ Features

| Feature | Description |
|---|---|
| 🔍 KQL Query Automation | Runs customizable checks via the Log Analytics REST API |
| 📋 Real-Time Markdown Logs | Easy-to-read GitHub Actions output during each run |
| 📄 Styled HTML Report | Downloadable assessment report ready for customer sharing |
| 🔐 Secure Authentication | Uses Azure Service Principal credentials stored as GitHub Secrets |
| 🧰 Plug-and-Play | Just configure secrets, add queries, and run |

## 📸 Report Snapshot

![ms-sentinel-scout-report](https://github.com/user-attachments/assets/79645c9b-553e-41e5-b008-b38ce89d235a)

A sample report is available here: [ms-sentinel-scout-report.html](ms-sentinel-scout-report.html)

## ⚙️ How It Works

![Define rules → Run Pipeline → Generate Report](https://github.com/user-attachments/assets/dc4d7578-c57a-4223-b8bb-8d3d1b3012f5)

1. KQL queries are defined in [`scripts/kql-queries.txt`](scripts/kql-queries.txt).
2. The GitHub Actions workflow authenticates to Azure using a Service Principal and runs each query against the Log Analytics workspace.
3. Results are compiled into a self-contained HTML report and uploaded as a workflow artifact.

## 📁 Repository Structure

```
.
├── scripts/
│   ├── generate-ms-sentinel-scout-report.ps1  # Main PowerShell script: runs queries and exports HTML
│   └── kql-queries.txt                        # KQL queries with display aliases
├── .github/
│   └── workflows/
│       └── Generate MS Sentinel Scout Report.yml  # Scheduled GitHub Actions workflow
├── ms-sentinel-scout-report.html              # Sample generated report
└── README.md                                  # This file
```

## 🔐 Required Permissions

The solution authenticates using an Azure Service Principal. The principal must have one of the following roles on the Log Analytics workspace:

- **Microsoft Sentinel Reader**, or
- **Log Analytics Reader**

## 🚀 Getting Started

### Prerequisites

- A Microsoft Sentinel-enabled Log Analytics workspace
- An Azure Service Principal with Reader access to the workspace (see [Required Permissions](#-required-permissions))
- A GitHub repository where you can store secrets

### Setup

1. **Fork or clone this repository** into your own GitHub account.

2. **Configure GitHub Secrets** in your repository settings (`Settings → Secrets and variables → Actions`):

   | Secret Name | Description |
   |---|---|
   | `AZURE_CLIENT_ID` | Service Principal application (client) ID |
   | `AZURE_CLIENT_SECRET` | Service Principal client secret |
   | `AZURE_TENANT_ID` | Azure Active Directory tenant ID |
   | `LOG_ANALYTICS_WORKSPACE_ID` | Log Analytics workspace ID |

   <img width="609" height="243" alt="GitHub Secrets configuration" src="https://github.com/user-attachments/assets/a75163a5-f057-47f3-becf-73c35d88a6e2" />

3. **Review and adjust the workflow schedule** in [`.github/workflows/Generate MS Sentinel Scout Report.yml`](.github/workflows/Generate%20MS%20Sentinel%20Scout%20Report.yml). By default the report runs every day at midnight (UTC).

   <img width="394" height="164" alt="Workflow schedule configuration" src="https://github.com/user-attachments/assets/0d932924-03ef-44b1-b638-be7e1b7cbccb" />

4. **Run the workflow** manually via `Actions → Generate MS Sentinel Scout Report → Run workflow`, or wait for the scheduled run.

5. **Download the HTML report** from the workflow run's artifacts once it completes.

## 📝 Customizing KQL Queries

Queries are stored in [`scripts/kql-queries.txt`](scripts/kql-queries.txt), one per line, using the format:

```
<Display Title> >> <KQL query>
```

**Example:**

```
Ingestion from AzureActivity Logs >> AzureActivity | summarize LogEntries = count() by bin(TimeGenerated, 1d) | sort by TimeGenerated desc
```

The text before `>>` becomes the section heading in the HTML report, and the text after `>>` is the KQL query that is executed.

The following checks are included out of the box:

| Query Title | What It Checks |
|---|---|
| Ingestion Report | Overall data volume and billing per table (last 7 days) |
| Ingestion from AzureActivity Logs | Daily activity log ingestion |
| Ingestion from SecurityEvent Logs | Security events per computer (last 24 h) |
| Ingestion from MS Defender Logs | Device events per device (last 24 h) |
| Ingestion from EntraID Logs | Sign-in logs per user (last 24 h) |
| Ingestion from SecurityAlert Logs | Security alerts by name (last 7 days) |
| Ingestion top 20 ActionTypes | Top 20 action types across all tables (last 24 h) |
| Devices Missing Security Telemetry | Computers with no heartbeat in the last 24 h |
| AzureDiagnostics (PaaS Logging) | Daily PaaS diagnostic log volume |
| Data Volume per Solution | Total ingestion volume per Log Analytics solution |

## 💡 Got Ideas?

Submit feature requests and bug reports via [GitHub Issues](https://github.com/samikroy/ms-sentinel-scout/issues).

For direct enquiries, reach out to samik.n.roy@gmail.com.
