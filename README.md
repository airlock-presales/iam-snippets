# Airlock IAM Configuration Snippets

A curated library of configuration snippets for **Airlock IAM**, designed to help partners and customers accelerate their IAM deployments — and to foster collaboration by sharing best practices and ready-to-use examples.

---

## 🚀 Purpose

This repository provides reusable **YAML configuration snippets** for [Airlock IAM](https://docs.airlock.com/iam/latest/index/1739013283152.html).  
Each snippet represents a self-contained configuration unit (`type: IamSnippet`) that can be easily imported into your IAM base configuration.

Snippets are ideal for:

- Quickly setting up common IAM use cases
- Sharing and reusing configurations across projects
- Demonstrating integrations or advanced features
- Learning best practices from real-world examples

We encourage **partners, customers, and the community** to contribute their own snippets and improvements.

---

## ✅ Why Snippets?

- **Modular** – Build IAM configurations piece by piece instead of from scratch.
- **Reusable** – Share and reapply snippets across environments and projects.
- **Automation-friendly** – Use them in CI/CD or CLI-based workflows.
- **Collaboration-ready** – Easier to review, maintain, and version-control small config units.
- **Community-driven** – Contribute, learn, and improve together.

---

## 🗂 Repository Structure

```ini
/snippets
   ├── authentication/
   │     ├── email-otp-verified.yaml
   │     ├── mtan-activation-alphabet.yaml
   ├── authorization/
   │     ├── role-based-access.yaml
   ├── integrations/
   │     ├── third-party-oauth-connector.yaml
   └── ...
README.md
CONTRIBUTING.md
LICENSE
```

- Each `.yaml` file is a snippet (`type: IamSnippet`).
- Snippets are grouped by domain (authentication, authorization, integrations, etc.).
- `CONTRIBUTING.md` explains how to add and test new snippets.
- `LICENSE` clarifies how this library can be used.

---

## 🧠 How to Use Snippets

1. **Start with your base IAM configuration** (`type: IamConfig`)

2. **Import one or more snippets:**

```bash
iam config import-snippet -f base-config.yaml snippet-file.yaml
```

3. **Connect required plugins** (if the snippet refers to others):

```bash
iam config connect plugin -f base-config.yaml -s <source-id> -d <dest-id> -p <property>
```

4. **Validate your configuration:**

```bash
iam config validate -f base-config.yaml
```

5. **Deploy** or export the configuration as usual.

📘 See [Airlock IAM Documentation](https://docs.airlock.com/iam/latest/index/1739013283152.html) for details on CLI commands and configuration concepts.

---

## 🧩 Developing Snippets

When creating or adapting snippets, follow these best practices:

- Use a valid YAML format with top-level fields:

```yaml
schemaVersion: 1
type: IamSnippet
metadata:
  name: my-snippet
spec:
  # Your IAM configuration elements here
```

- Avoid hard-coded IDs to prevent conflicts.

- Keep snippets minimal and focused on a single purpose.

- Test using the IAM Config Editor or CLI before submitting.

- Document any dependencies or assumptions in comments.

---

## 👥 Contributing

We welcome contributions from everyone!

1. Fork this repository.

2. Create a new branch:

```bash
git checkout -b feature/my-new-snippet
```

3. Add your snippet under the appropriate folder.

4. Validate it using the IAM CLI.

5. Open a Pull Request with a clear description.

Before contributing, please read the [`CONTRIBUTING.md`](CONTRIBUTING.md) file for detailed guidelines.

---

## 🧩 Versioning & Compatibility

- Each snippet should include a `metadata.iamVersion` field indicating the IAM version it was built for.
- Always validate snippets with your target IAM version.
- If major changes occur between IAM versions, review snippets before reuse.

---

## 📚 Useful Links

- 📖 [Airlock IAM Snippet Documentation](https://docs.airlock.com/iam/latest/index/1739013283152.html)
- 🧩 [Airlock IAM Official Documentation](https://docs.airlock.com/iam/latest)
- 🛠 [Airlock IAM CLI Reference](https://docs.airlock.com/iam/latest/index/1739013283152.html#1739013283152)

---

## 🛡 License

This repository is released under the **[insert license name, e.g. MIT or Apache 2.0]**.  
See the [LICENSE](LICENSE) file for details.

---

### ❤️ Thank You!

Your contributions help make the Airlock IAM ecosystem stronger.  
Whether you’re sharing a snippet, fixing a typo, or testing configurations — thank you for being part of the community!

---

*Maintained by the Airlock Pre-Sales Team and community contributors.*
