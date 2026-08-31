# Value-Creating Education Literature Review Documents

A content-first repository of six research-informed handouts on Tsunesaburo Makiguchi, Josei Toda, and Daisaku Ikeda. It is organized as a stable source for a future literature-review website and collaboration platform.

Prepared by Peter Bjork, M.Ed., DePaul University - College of Education - PhD in Value-Creating Education for Global Citizens

## Documents

| Figure | Document | Type | HTML | PDF | Pages |
|---|---|---|---|---|---:|
| Tsunesaburo Makiguchi | Makiguchi’s Ideas in Day-to-Day Education | Educator guide | [Open](documents/makiguchi-day-to-day-education/index.html) | [Download](documents/makiguchi-day-to-day-education/printable.pdf) | 2 |
| Tsunesaburo Makiguchi | Makiguchi: Opposing Ideas and Major Critics | Critical perspectives | [Open](documents/makiguchi-opposing-ideas-and-major-critics/index.html) | [Download](documents/makiguchi-opposing-ideas-and-major-critics/printable.pdf) | 3 |
| Josei Toda | Josei Toda’s Contributions to Education | Historical synthesis | [Open](documents/toda-contributions-to-education/index.html) | [Download](documents/toda-contributions-to-education/printable.pdf) | 3 |
| Josei Toda | Josei Toda: Criticism and Leading Critics | Critical perspectives | [Open](documents/toda-criticism-and-leading-critics/index.html) | [Download](documents/toda-criticism-and-leading-critics/printable.pdf) | 3 |
| Daisaku Ikeda | A Secondary School for Value Creation | Evidence-grounded reconstruction | [Open](documents/ikeda-secondary-school/index.html) | [Download](documents/ikeda-secondary-school/printable.pdf) | 4 |
| Daisaku Ikeda | Non-Examples of an Ikeda Classroom | Visual field guide | [Open](documents/ikeda-classroom-non-examples/index.html) | [Download](documents/ikeda-classroom-non-examples/printable.pdf) | 3 |

Each document has the same stable layout:

```text
documents/<document-id>/
├── index.html
└── printable.pdf
```

## Integration contract

[`manifest.json`](manifest.json) is the collection index and application-facing contract. [`manifest.schema.json`](manifest.schema.json) defines its JSON Schema. Consumers should discover documents through the manifest rather than hard-coding the document list.

```js
const response = await fetch("/manifest.json");
if (!response.ok) throw new Error(`Manifest request failed: ${response.status}`);

const manifest = await response.json();
for (const document of manifest.documents) {
  console.log(document.id, document.formats.html, document.formats.pdf);
}
```

Once the repository is public, the canonical raw manifest URL will be:

```text
https://raw.githubusercontent.com/Pdbjork/value-creating-education-literature-review/main/manifest.json
```

While the repository is private, a server-side application can retrieve the raw manifest through the GitHub Contents API:

```js
const response = await fetch(
  "https://api.github.com/repos/Pdbjork/value-creating-education-literature-review/contents/manifest.json?ref=main",
  {
    headers: {
      Accept: "application/vnd.github.raw+json",
      Authorization: `Bearer ${process.env.GITHUB_TOKEN}`,
      "X-GitHub-Api-Version": "2022-11-28"
    }
  }
);
```

Keep GitHub credentials on the server. Do not expose a personal access token in browser code.

## Editorial model

- HTML is the editable source for each handout.
- PDF is the corresponding print artifact.
- Claims, quotations, citations, and distinctions between evidence and interpretation should remain explicit.
- A content change is complete only when both formats and the manifest metadata agree.
- Stable document IDs and format paths are part of the integration contract.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the contribution workflow.

## Repository status and rights

This repository begins as private to avoid publishing the documents or granting reuse rights without an explicit decision. No open-source or content license is granted at this time. Repository visibility and licensing can be changed separately when the collaboration model is defined.
