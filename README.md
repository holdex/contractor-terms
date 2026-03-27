# contractor-terms

This repository contains the Standard Terms for independent contractors working with Holdex Limited. It is published
publicly for transparency.

> **Issues and Discussions are disabled.** For questions, contact [hr@holdex.io](mailto:hr@holdex.io).

---

## Repository Structure

```text
contractor-terms/
├── .github/
│   └── workflows/
│       ├── lint.yml            — markdown formatting checks
│       └── check-links.yml     — URL and anchor link validation
├── README.md                   — this file
├── STANDARD_TERMS.md           — the legal document
└── CHANGELOG.md                — plain English version history
```

---

## How This Works

Each contractor signs a PDF agreement (Special Terms) that references a specific tagged release of `STANDARD_TERMS.md` —
for example `v1.0`. That tag is the version they agreed to. Git ensures the history is tamper-proof and timestamped.

When terms are updated, a new release is tagged (e.g. `v1.1`) and contractors are notified by email at least 14 days
before changes take effect, as described in the [Updates](STANDARD_TERMS.md#updates-to-these-standard-terms) section of
the Standard Terms.

---

## How to Update the Terms

Follow these steps every time the Standard Terms are changed. Do not edit past releases.

### 1. Create a branch

```bash
git checkout main
git pull
git checkout -b update/describe-your-change
```

### 2. Edit `STANDARD_TERMS.md`

Make your changes. Keep the formatting consistent — the lint workflow will flag issues automatically when you open a PR.

### 3. Update `CHANGELOG.md`

Add a new entry at the top of the file describing what changed and why, in plain English. Use the format already in the
file.

### 4. Open a Pull Request

Push your branch and open a PR against `main`. A review and approval is required before merging.

```bash
git add STANDARD_TERMS.md CHANGELOG.md
git commit -m "update: describe your change in plain English"
git push origin update/describe-your-change
```

### 5. Merge and tag a new release

Once approved and merged:

```bash
git checkout main
git pull
git tag v1.1        # increment the version number
git push origin v1.1
```

Then go to **GitHub → Releases → Draft a new release**, select the tag, and publish. Copy the release URL — you will
need it for contractor notifications.

### 6. Notify contractors

Send an email to all active contractors from `hr@holdex.io` with:

- A summary of what changed
- A link to the new release
- The date the new terms take effect (minimum 14 days from the email date)

Use the subject line: `Holdex Contractor Terms Update — v1.1 effective [date]`

---

## Versioning Convention

| Tag    | Meaning                                                                    |
| ------ | -------------------------------------------------------------------------- |
| `v1.0` | Initial release                                                            |
| `v1.1` | Minor update (clarification, new clause, small change)                     |
| `v2.0` | Major update (significant change to rights, obligations, or payment terms) |

When in doubt, increment the minor version. Use a major version bump when the change materially affects contractor
obligations or Company rights — these warrant extra care in contractor communication.

---

## Workflows

### `lint.yml`

Runs `markdownlint` on every PR to `main`. Enforces consistent heading style, list formatting, and whitespace rules. A
PR cannot be merged if lint fails.

### `check-links.yml`

Checks all URLs and internal anchor links in `STANDARD_TERMS.md` on every PR to `main`. Catches broken links before they
reach contractors.

---

## Ownership

This repository is owned and maintained by the HR team at Holdex Limited. For questions or proposed changes, contact
[hr@holdex.io](mailto:hr@holdex.io).

---

_Holdex Limited — [holdex.io](https://holdex.io)_
