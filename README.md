# Microsoft Sentinel Scout

⚙️ Features
Feature	Description

🔍 KQL Query Automation	Runs customizable checks via Log Analytics API <br/>
📋 Real-Time Markdown Logs	Easy-to-read GitHub Actions output <br/>
📄 Styled HTML Report	Downloadable assessment report for customer sharing <br/>
🔐 Secure Login	Uses Azure Service Principal credentials <br/>
🧰 Plug-and-Play	Just configure secrets, add queries, and run <br/>

🔍 Report Snapshort

![ms-sentinel-scout-report](https://github.com/user-attachments/assets/79645c9b-553e-41e5-b008-b38ce89d235a)


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

🔐 Permission

The solution on a service principaln with the 
Microsoft Sentinel Reader or Log Analytics Reader Permission.

⚙️ How it Runs

![Define rules → Run Pipeline → Generate Report - visual selection](https://github.com/user-attachments/assets/dc4d7578-c57a-4223-b8bb-8d3d1b3012f5)


Here is a sample report - https://github.com/samikroy/ms-sentinel-scout/blob/main/ms-sentinel-scout-report.html

Reach out to samik.n.roy@gmail.com for any queries.

⚙️ How you can run this 
 - Clone this repo
 - Configure the Repository secret based on your environment
   
https://github.com/samikroy/ms-sentinel-scout/settings/secrets/actions

<img width="609" height="243" alt="image" src="https://github.com/user-attachments/assets/a75163a5-f057-47f3-becf-73c35d88a6e2" />

 - Review the schedule
   
https://github.com/samikroy/ms-sentinel-scout/blob/main/.github/workflows/Generate%20MS%20Sentinel%20Scout%20Report.yml

<img width="394" height="164" alt="image" src="https://github.com/user-attachments/assets/0d932924-03ef-44b1-b638-be7e1b7cbccb" />


and then let this run and generate the HTML report.


🧰 Got Ideas 

Submit Here - https://github.com/samikroy/ms-sentinel-scout/issues
