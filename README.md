# @avanlan/eslint-config

[![npm](https://img.shields.io/npm/v/@avanlan/eslint-config?color=444&label=)](https://npmjs.com/package/@avanlan/eslint-config) [![code style](https://layouwen.me/badge-code-style.svg)](https://github.com/layouwen/eslint-config)

## Usage

### Starter Wizard

We provided a CLI tool to help you set up your project, or migrate from the legacy config to the new flat config with one command.

```bash
pnpm dlx @avanlan/eslint-config@latest
```

### Manual Install

If you prefer to set up manually:

```bash
pnpm i -D eslint @avanlan/eslint-config
```

And create `eslint.config.mjs` in your project root:

```js
// eslint.config.mjs
import avanlan from '@avanlan/eslint-config'

export default avanlan()
```

<details>
<summary>
Combined with legacy config:
</summary>

If you still use some configs from the legacy eslintrc format, you can use the [`@eslint/eslintrc`](https://www.npmjs.com/package/@eslint/eslintrc) package to convert them to the flat config.

```js
// eslint.config.mjs
import antfu from '@avanlan/eslint-config'
import { FlatCompat } from '@eslint/eslintrc'

const compat = new FlatCompat()

export default antfu(
  {
    ignores: [],
  },

  // Legacy config
  ...compat.config({
    extends: [
      'eslint:recommended',
      // Other extends...
    ],
  })

  // Other flat configs...
)
```

> Note that `.eslintignore` no longer works in Flat config, see [customization](#customization) for more details.

</details>

### Add script for package.json

For example:

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

## Configs

[antfu/eslint-config](https://github.com/antfu/eslint-config)

## License

[MIT](./LICENSE) License &copy; 2025 [AvanLan](https://github.com/layouwen)
