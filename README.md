# 🛡️ Guide for Security Team and BPAM Representatives

To view known vulnerabilities directly in GitHub:

1. Go to the **Security** tab of this repository.
2. Select **Dependabot** from the sidebar.
3. Review the list of detected vulnerabilities.
4. To filter by application or package manager:
   - Click the **Manifest dropdown** at the top of the Dependabot view.
   - Select the relevant app or manifest file to narrow down results.

> 🔎 This allows security reviewers to focus on specific application contexts during triage and remediation.

---

# 🔍 Vulnerability Report Generation using OWASP Dependency-Check

This project helps you run [OWASP Dependency-Check](https://github.com/jeremylong/DependencyCheck) against Java-based applications to identify known vulnerabilities.

---

## 📥 Clone the Repository

Clone the repository locally to run the dependency check:

```bash
git clone https://github.com/your-username/Vulnerability-report.git
```

Once cloned, ensure the `dependency-check` folder is placed **inside** the application folder alongside files such as:

- `ejb/`
- `ear/`
- `war/`
- `pom.xml`

> ℹ️ If there is an existing report (usually named `odc-report`), **you do not need to delete it**. Running a new scan will automatically overwrite the old report.

---

## 🛠️ Running a New Vulnerability Check

To generate a fresh report, use the following command:

```bash
.\dependency-check\bin\dependency-check.bat --project "HAMIS" --scan . --format HTML --out ./odc-report --enableExperimental
```

> 🔁 Replace `"HAMIS"` with the appropriate application name in both the `--project` value and the folder path.

### 📝 Example Usage

Run the command in a path like:

```
C:\...\Vulnerability-report\HAMIS>
```

---

## 📦 Download Dependency-Check

You can download the latest version of OWASP Dependency-Check from:

👉 [https://github.com/jeremylong/DependencyCheck/releases](https://github.com/jeremylong/DependencyCheck/releases)

---

## 🚫 Before Pushing to GitHub

Ensure you **delete the `dependency-check` folder** from each app directory **before committing or pushing** to GitHub. It is large and may cause errors during upload.

---

## ⚠️ Notes on Tool Mismatches

- **Dependabot** may flag more recent vulnerabilities and uses GitHub Security Advisories to help detect vulnerabilities.
- **OWASP Dependency-Check** uses CPE-based resolution and may **not catch newer GitHub advisories** or informal CVEs as quickly.
- **OWASP Dependency-Check** rolls up the vulnerabilities under a master dependency whereas **Dependabot** just lists all vulnerabilities.
