# SKILL.md — Example Skill

> This is a filled-in example showing the pattern for writing a skill.
> Copy this file into your own skill folder and adapt it.
> Delete this notice when you do.

---

## What this skill does

Generates a structured plain-text summary of a user-submitted document, formatted for display in the product UI.

---

## When to use it

Use this skill whenever a user uploads a document and the product needs to produce a summary. Do not use it for real-time streaming responses — this skill is for batch processing only.

---

## Inputs

Before starting, confirm you have:
- [ ] The full text content of the document (or a parsed version of it)
- [ ] The target length for the summary (default: 3–5 sentences)
- [ ] The user's language preference (default: English)

---

## Steps

1. Read the full document text
2. Identify the core subject, the key facts, and the main conclusion
3. Write a summary that covers all three in the target length
4. Do not include opinions, inferences, or information not in the document
5. Format the output as plain text — no markdown, no bullet points, no headers
6. If the document is in a language other than the user's preference, note this at the end of the summary

---

## Output format

```
[Summary text here. 3–5 sentences. Plain prose. No formatting.]

[Optional: "Note: Original document is in [language]."]
```

---

## Edge cases

**Document is too short (under 100 words):**
Return the full text as the summary. Do not pad.

**Document contains no meaningful content (e.g. a blank form):**
Return: "No summary available — the document does not contain readable content."

**Document is in a language the model cannot process:**
Return: "Unable to summarise — document language is not supported."

**Document contains sensitive personal information:**
Summarise at the category level only. Do not include specific names, numbers, or identifiers in the output.

---

## Example

**Input document (excerpt):**
> "This agreement is made between Acme Corp and the contractor for the provision of software development services commencing 1 January 2025. The total contract value is CHF 48,000 payable in monthly instalments. Either party may terminate with 30 days written notice."

**Output:**
> This is a software development services contract between Acme Corp and a contractor, effective from January 2025. The total value is CHF 48,000 paid monthly, with a 30-day termination notice period on either side.
