# Contributing to Microsoft Sentinel Scout

Thank you for your interest in contributing! Contributions of all kinds are welcome — new KQL queries, bug fixes, documentation improvements, or feature ideas.

## How to Contribute

### 1. Report Issues

Found a bug or have a feature request? Please [open an issue](https://github.com/samikroy/ms-sentinel-scout/issues) and include:

- A clear title and description
- Steps to reproduce (for bugs)
- Expected vs. actual behaviour
- Any relevant screenshots or log output

### 2. Suggest or Add KQL Queries

The query library lives in [`scripts/kql-queries.txt`](scripts/kql-queries.txt). Each line follows this format:

```
<Display Title> >> <KQL query>
```

To propose a new check:

1. Fork the repository.
2. Add your query to `scripts/kql-queries.txt`.
3. Test it against a real Log Analytics workspace to confirm it returns meaningful results.
4. Open a pull request with a short description of what the query checks and why it is useful.

### 3. Improve the PowerShell Script

The main script is [`scripts/generate-ms-sentinel-scout-report.ps1`](scripts/generate-ms-sentinel-scout-report.ps1).

Before submitting changes:

- Make sure the script still runs end-to-end with valid Azure credentials.
- Keep error handling consistent with the existing `try/catch` pattern.
- Avoid introducing new dependencies beyond the standard PowerShell modules.

### 4. Improve Documentation

Documentation changes to `README.md` or other Markdown files are always welcome. Please keep language clear and concise.

## Pull Request Guidelines

- Keep pull requests focused on a single change.
- Provide a clear description of what was changed and why.
- Reference any related issues (e.g. `Closes #42`).
- Ensure the GitHub Actions workflow still passes after your changes.

## Code of Conduct

Please be respectful and constructive in all interactions. This project follows standard open-source community norms.

---

For direct questions, reach out to samik.n.roy@gmail.com.
