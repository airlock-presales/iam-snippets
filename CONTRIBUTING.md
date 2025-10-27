# Contributing to Airlock IAM Configuration Snippets

First off — thank you for taking the time to contribute! 🎉  
Your help makes this repository a valuable and growing resource for the Airlock IAM community.

This document outlines how you can contribute snippets, fixes, and improvements while keeping consistency and quality high.

---

## 🧭 Goals

This repository is a **community-driven library** of reusable configuration snippets for [Airlock IAM](https://docs.airlock.com/iam/latest/index/1739013283152.html).  
The goals are:

- To **share reusable and well-documented snippets** that help partners and customers implement Airlock IAM faster.
- To **encourage collaboration** and contributions from the community.
- To **maintain high quality**, validated, and version-compatible snippets.

---

## 🧩 What You Can Contribute

You can contribute in many ways:

- ✅ New **IAM snippets** (e.g., authentication methods, policies, connectors, flows)
- 🔧 Improvements or corrections to existing snippets
- 🧾 Documentation or usage examples
- 🧰 Utility scripts (YAML helpers, validators, importers)
- 🐞 Bug fixes or validation improvements

---

## 🧱 Snippet Requirements

Each snippet must:

1. Be a valid Airlock IAM configuration file of type `IamSnippet`.
2. Follow proper YAML syntax.
3. Include metadata describing its purpose and compatibility.

### Example Template

```yaml
schemaVersion: 1
type: IamSnippet
metadata:
  name: example-snippet
  description: Example snippet showing structure and metadata.
  iamVersion: 8.2.0
  author: Your Name
  tags:
    - authentication
    - example
spec:
  # IAM configuration elements go here
```

### Guidelines

- **Use descriptive metadata**:
   - `name` should be concise but clear.
   - Add relevant `tags` to help others find your snippet.

- **Avoid hardcoded IDs** to prevent conflicts when imported.
- **Keep it modular** — one focused purpose per snippet.
- **Validate your YAML** before submitting.
- **Add inline comments** to explain non-obvious configuration details.
- **Document dependencies** — if your snippet relies on another snippet or IAM component.
- **Readme** - to explain in more details to others what this snippet is doing and how it is used.

---

## 🧪 Testing Your Snippet

Before opening a pull request, ensure your snippet works properly:

```bash
iam config import-snippet -f base-config.yaml path/to/your-snippet.yaml
iam config validate -f base-config.yaml
```

Alternatively, use the IAM Config Editor to upload and visually inspect the configuration.

If your snippet connects multiple components, test them via:

```bash
iam config connect plugin -f base-config.yaml -s <source-id> -d <dest-id> -p <property>
```

Validation should pass **without warnings or errors**.

---

## 🪄 Repository Structure

```ini
/snippets
   ├── snippet-name/
   |  ├── snippet-name.yaml
   |  ├── README.md # with explanation and use-case description
   ├── snippet-name1/
   |  ├── snippet-name1.yaml
   |  ├── README.md # with explanation and use-case description
   ├── snippet-name2/
   |  ├── snippet-name2.yaml
   |  ├── README.md # with explanation and use-case description
```

---

## 🪶 File Naming Convention

- Use **kebab-case** for filenames.  
   Example: `oauth2-login-handler.yaml`
- Include a **short, descriptive name** (no spaces, no special chars).
- Optional but encouraged: prefix by topic if applicable.  
   Example: `auth-email-verification.yaml`, `flow-mtan-registration.yaml`

---

## 🧰 Submitting a Contribution

1. **Fork** this repository.

2. **Create a new branch**:

```bash
git checkout -b feature/my-awesome-snippet
```

3. **Add your snippet** to the relevant folder.

4. **Test and validate** your configuration.

5. **Commit and push** your changes:

```bash
git add .
git commit -m "Add: New email OTP verification snippet"
git push origin feature/my-awesome-snippet
```

6. **Open a Pull Request (PR)** with:
   - A clear title and short description.
   - Explanation of what the snippet does.
   - Mention of IAM version compatibility.
   - (Optional) A short usage example.

---

## 🧾 Pull Request Review Process

Once you open a PR:

1. A maintainer will review your submission.
2. Feedback may be provided for:
   - YAML formatting
   - Missing metadata
   - Validation issues
   - Structure or naming conventions

3. Once approved, your PR will be merged into the main branch.

---

## 🛡️ Code of Conduct

We aim to maintain a respectful and inclusive environment.  
Please be kind, constructive, and professional in all discussions.

---

## 🧠 Helpful References

- 📘 [Airlock IAM Snippet Documentation](https://docs.airlock.com/iam/latest/index/1739013283152.html)
- ⚙️ [Airlock IAM CLI Reference](https://docs.airlock.com/iam/latest/index/1739013283152.html#1739013283152)
- 🧩 [Airlock IAM Official Docs](https://docs.airlock.com/iam/latest)

---

## ❤️ Thank You

Your contributions make the Airlock IAM ecosystem stronger.  
Whether it’s a small fix or a major addition — **every contribution matters**.

Let’s make IAM configuration simpler, cleaner, and more shareable — together.
