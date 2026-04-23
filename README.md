# 📧 Email Domain / Communication Analyzer

A single-file HTML tool for analyzing email communications by domain. Drop in a CSV export of email data, specify a domain, and get a ranked list of unique contacts along with how many messages each appeared in.

## Features

- **Zero install** — just open `index.html` in any modern browser
- **Drag & drop CSV upload** (or click to browse)
- **Smart email parsing** — handles `Name <email@domain.com>`, `email@domain.com (Name)`, and bare-email formats
- **Deduplication by email address** with name consolidation (picks the most descriptive name seen)
- **Message counting** based on unique row IDs
- **Exportable results** — view as a table or copy a CSV to paste elsewhere

## Usage

1. Open `index.html` in your browser.
2. **Step 1** — Enter the domain you want to analyze (e.g. `gmail.com`). No `@` needed.
3. **Step 2** — Drop in your CSV file.
4. **Step 3** — Review results, or click **Show CSV to Copy** to export.

## Expected CSV Format

Your CSV should contain these columns:

| Column                | Description                              |
| --------------------- | ---------------------------------------- |
| `ID`                  | Unique row/message identifier            |
| `Communication From`  | Sender email(s)                          |
| `Communication To`    | Recipient email(s)                       |
| `Communication CC`    | CC'd email(s)                            |
| `Communication BCC`   | BCC'd email(s)                           |

Each address field can contain multiple addresses in any common format:

```
"John Doe" <john@example.com>, jane@example.com (Jane Smith), bob@example.com
```

## Output

Results are displayed as a table with:

- **Name** — best-guess display name for the contact
- **Email Address** — the unique email
- **Message Count** — number of unique rows (by `ID`) where this contact appeared
- **Raw Values** — the original unparsed strings the email was found in

Results are sorted by message count, descending.

## Dependencies

Loaded via CDN at runtime:

- [PapaParse 5.4.1](https://www.papaparse.com/) — CSV parsing

No build step, no package manager, no backend.
