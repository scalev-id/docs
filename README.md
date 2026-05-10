# Scalev documentation

This repository contains the Scalev documentation site built with Mintlify.

## Local preview

Install the Mintlify CLI if needed:

```bash
npm i -g mint
```

Run the preview from the repository root:

```bash
mint dev
```

## Validation

Before publishing changes, run:

```bash
mint broken-links
git diff --check
```

Content pages are MDX files. Site navigation and language structure are defined in `docs.json`.
