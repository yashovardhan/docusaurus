---
sidebar_position: 1
slug: /api/misc/@docusaurus/eslint-plugin
---

# 📦 eslint-plugin

[ESLint](https://eslint.org/) is a tool that statically analyzes your code and reports problems or suggests best practices through editor hints and command line. Docusaurus provides an ESLint plugin to enforce best Docusaurus practices.

## Installation

```bash npm2yarn
npm install --save-dev @docusaurus/eslint-plugin
```

## Usage

### Recommended config

Add `plugin:@docusaurus/recommended` to the `extends` section of your `.eslintrc` configuration file:

```json title=".eslintrc"
{
  "extends": ["plugin:@docusaurus/recommended"]
}
```

This will enable the `@docusaurus` eslint plugin and use the `recommended` config. See [Supported rules](#supported-rules) below for a list of rules that this will enable.

### Manual config

For more fine-grained control, you can also enable the plugin manually and configure the rules you want to use directly:

```json title=".eslintrc"
{
  "plugins": ["@docusaurus"],
  "rules": {
    "@docusaurus/string-literal-i18n-messages": "error",
    "@docusaurus/no-untranslated-text": "warn"
  }
}
```

## Supported configs

- Recommended: recommended rule set for most Docusaurus sites that should be extended from.
- All: **all** rules enabled. This will change between minor versions, so you should not use this if you want to avoid unexpected breaking changes.

## Supported rules

| Name | Description |  |
| --- | --- | --- |
| [`@docusaurus/no-untranslated-text`](./no-untranslated-text.md) | Enforce text labels in JSX to be wrapped by translate calls |  |
| [`@docusaurus/string-literal-i18n-messages`](./string-literal-i18n-messages.md) | Enforce translate APIs to be called on plain text labels | ✅ |

✅ = recommended

## Example configuration

Here's an example configuration:

```js title=".eslintrc.js"
module.exports = {
  extends: ['plugin:@docusaurus/recommended'],
  rules: {
    '@docusaurus/no-untranslated-text': [
      'warn',
      {ignoredStrings: ['·', '—', '×']},
    ],
  },
};
```
