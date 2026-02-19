# Vue Language Pack for Fresh Editor

Lightweight Vue 3 Single File Component (SFC) support for the Fresh editor.

## Features

- Syntax highlighting for `.vue` files:
  - `<script>` (TypeScript / JavaScript – lightweight tokenization)
  - `<template>` (HTML + Vue directives + mustache `{{ ... }}`)
  - `<style>` (basic CSS scope)
- LSP integration via Volar (`vue-language-server`)

## Installation

## LSP Setup (Volar)

Install the Vue language server globally:

```bash
npm i -g @vue/language-server typescript
```

Verify:
    
```bash
which vue-language-server
```

### Vue Syntax from URL

In Fresh: Command Palette → **Package: Install from URL**

Use:
https://github.com/unoctanium/fresh-vue-language

Then quit / restart fresh

## Notes / Limitations

Fresh syntax highlighting is syntect-compatible, so grammars that rely on advanced Sublime features
(e.g. extends) often fail to parse. This pack is intentionally self-contained.

## Development

Validate:
    
```bash
./validate.sh
```

Test by installing from local path (recommended during development):
- Command Palette → Package: Install from URL
- Enter full path to the pack directory

Then check logs / warnings inside Fresh.

