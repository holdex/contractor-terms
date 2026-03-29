# contractor-terms

This repository contains the Standard Terms and Special Terms template for
independent contractors working with Holdex Limited. It is published publicly
for transparency.

> **Issues and Discussions are disabled.** For questions, reach out through your existing Holdex contact.

---

## Repository Structure

```text
contractor-terms/
├── .github/
│   └── workflows/
│       └── lint.yml            — markdown lint and link validation
├── .rumdl.toml                 — markdown lint configuration
├── README.md                   — this file
├── STANDARD_TERMS.md           — the legal document (versioned by git tags)
├── SPECIAL_TERMS.md            — blank template (filled in per contractor by HR; keep only the relevant compensation subsection)
└── CHANGELOG.md                — plain English version history
```

---

## How This Works

Each contractor engagement produces two documents:

**1. Standard Terms** (`STANDARD_TERMS.md`)
The boilerplate legal terms governing all contractor relationships. Versioned
by git tags (e.g. `v1.0`). The tag is the version — git timestamps it
automatically. Never edited retroactively.

**2. Special Terms** (`SPECIAL_TERMS.md`)
A blank template stored here. When preparing an agreement for a specific
contractor, HR copies and fills in the template, then stores the completed
version in the private HR repository alongside any signed artifacts.

The contractor signs a document that references both:

- The Standard Terms by tag (e.g. `v1.0`)
- The Special Terms by the commit of their filled-in copy

---

## Workflow for Onboarding a New Contractor

### 1. Prepare the Special Terms

Copy `SPECIAL_TERMS.md` to the private HR repository. Fill in all
`<!-- PLACEHOLDER -->` fields. In the Compensation section, keep only
the subsection that applies to this contractor (Hourly, Per Project, or
Milestone-Based) and delete the other two. Record the Standard Terms tag
currently in effect (e.g. `v1.0`) at the top of the document.

### 2. Send for signing

Share the filled-in Special Terms with the contractor for review and signature.
Signatures can be collected digitally (e.g. DocuSign) or as a signed PDF scan.
Store the signed copy in the private HR repository.

### 3. Confirm the version on record

Ensure the signed copy clearly references the Standard Terms tag in effect
at the date of signing. This is the version that governs that contractor's
relationship indefinitely unless updated per the process below.

---

## Workflow for Updating the Standard Terms

Follow these steps every time `STANDARD_TERMS.md` is changed.
**Never edit past releases.**

### 1. Create a branch

```bash
git checkout main
git pull
git checkout -b update/describe-your-change
```

### 2. Edit `STANDARD_TERMS.md`

Make your changes. Keep formatting consistent — the lint workflow will
flag issues automatically when you open a PR.

### 3. Update `CHANGELOG.md`

Add a new entry at the top describing what changed and why, in plain English.

### 4. Open a Pull Request

Push your branch and open a PR against `main`. A review and approval is
required before merging.

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

Then go to **GitHub → Releases → Draft a new release**, select the tag,
and publish. Copy the release URL — you will need it for contractor notifications.

### 6. Notify contractors

Send an email to all active contractors with:

- A summary of what changed
- A link to the new release
- The date the new terms take effect (minimum 14 days from the email date)

Use the subject line: `Holdex Contractor Terms Update — v1.1 effective [DATE]`

---

## Versioning Convention

| Tag    | Meaning                                                                    |
| ------ | -------------------------------------------------------------------------- |
| `v1.0` | Initial release                                                            |
| `v1.1` | Minor update — clarification, new clause, small change                     |
| `v2.0` | Major update — significant change to rights, obligations, or payment terms |

When in doubt, increment the minor version. Use a major version bump when
the change materially affects contractor obligations or Company rights —
these warrant extra care in contractor communication.

---

## Workflows

### `lint.yml`

Runs on every PR to `main` that touches a `.md` file. Two steps:

1. **rumdl** — enforces consistent markdown formatting per `.rumdl.toml`
2. **lychee** — validates all URLs and internal anchor links

A PR cannot be merged if either step fails.

---

## Ownership

This repository is owned and maintained by the HR team at Holdex Limited.
For questions or proposed changes, raise them internally through the HR team.

---

_Holdex Limited — [holdex.io](https://holdex.io)_
