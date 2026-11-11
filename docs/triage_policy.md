# Customer Support Triage Policy

Owner: Customer Engineering
Applies to: Mobile Commerce Platform (iOS / Android / Web)

All inbound email is triaged into this GitHub issue tracker. Every inbound email
body contains a `Type:` field.

## 1. Which messages are triaged

| Type | Action |
|------|--------|
| `bug` | customer report - triage |
| `billing` | customer report - triage |
| `feature` | customer report - triage |
| `internal` | not a customer report - ignore |
| `marketing` | not a customer report - ignore |

An ignored message must not create an issue, must not add a comment, and must
not receive a reply.

## 2. Priority mapping

| Impact | Priority |
|--------|----------|
| Critical | P0 |
| High | P1 |
| Low | P2 |
| Request | P2 |

## 3. Issue title format

`[<PRIORITY>][<TYPE>] <email subject>`

`TYPE` is upper-case: `BUG`, `BILLING` or `FEATURE`.

Example: `[P0][BUG] Checkout page returns 500 for all customers`

## 4. Issue body

Each created issue body must contain these labelled lines:

```
Customer: <customer name>
Account email: <customer email address>
Type: <type>
Impact: <impact>
Product area: <product area>
Source message id: <inbox email id>
Details: <short description copied from the email>
```

## 5. Existing open issues

Before creating an issue, list the open issues in this repository. If an open
issue already covers the same problem, do not create a duplicate. Add a comment
to the existing issue instead. The comment must mention the customer's account
email and the new details from the email.

## 6. Acknowledgements

Send a short acknowledgement reply to every customer email that results in a
created issue or an added comment. Do not reply to ignored emails.

## 7. Triage report

Write `support_triage_report.csv` in your working directory with one row for
every inbound email and exactly this header:

```
message_id,sender,subject,type,priority,action
```

Column rules:
- `message_id` - the inbox email id
- `sender` - the sender email address only (no display name)
- `subject` - the email subject
- `type` - `bug` | `billing` | `feature` | `internal` | `marketing`
- `priority` - `P0` | `P1` | `P2` | `N/A`
- `action` - `issue_created` | `comment_added` | `ignored`

For rows with `action = ignored` use `priority = N/A`. For all other rows use
the priority from section 2.
