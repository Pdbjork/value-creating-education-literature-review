# Contributing

Use pull requests for substantive changes so the evidence, wording, printable result, and application metadata can be reviewed together.

## Content workflow

1. Create a branch from `main`.
2. Edit the document’s `index.html` source.
3. Regenerate its `printable.pdf` from the updated HTML.
4. Confirm the PDF page count and visual layout.
5. Update the matching entry in `manifest.json` if the title, summary, tags, type, stance, paths, or page count changed.
6. Validate `manifest.json` against `manifest.schema.json`.
7. Open a pull request that identifies the changed claims and the sources supporting them.

Do not edit a PDF without making the corresponding HTML change. Do not change an existing document ID or format path without coordinating a migration for website consumers.

## Review requirements

A pull request should demonstrate that:

- factual additions have claim-level source support;
- quotations and paraphrases are distinguishable;
- evidence, interpretation, and reconstruction are labeled accurately;
- opposing interpretations are represented without collapsing them into fact;
- both the HTML and PDF contain the attribution line;
- internal links and manifest paths resolve;
- the printable PDF has no clipped content, accidental blank pages, or unreadable type;
- private credentials, copyrighted source scans, and unlicensed media are not committed.

## Naming contract

Document directories use lowercase kebab-case IDs. Every directory contains exactly these public format entry points:

```text
index.html
printable.pdf
```

New document IDs must be unique in `manifest.json`. Application code should use manifest IDs as stable keys and the `formats` fields as paths.

## Attribution

Preserve this line in each document unless the author explicitly changes it:

> Prepared by Peter Bjork, M.Ed., DePaul University - College of Education - PhD in Value-Creating Education for Global Citizens
