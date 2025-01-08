# @avanlan/eslint-config

[![npm](https://img.shields.io/npm/v/@avanlan/eslint-config?color=444&label=)](https://npmjs.com/package/@avanlan/eslint-config) [![code style](https://antfu.me/badge-code-style.svg)](https://github.com/layouwen/eslint-config)

Supports ESLint v9 or v8.50.0+

> [!IMPORTANT]
> Since v1.0.0, this config is rewritten to the new [ESLint Flat config](https://eslint.org/docs/latest/use/configure/configuration-files-new), check the [release note](https://github.com/antfu/eslint-config/releases/tag/v1.0.0) for more details.

## Usage

```bash
pnpm i -D eslint @avanlan/eslint-config@^2
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
import avanlan from '@avanlan/eslint-config'
import { FlatCompat } from '@eslint/eslintrc'

const compat = new FlatCompat()

export default avanlan(
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

## License

[MIT](./LICENSE) License &copy; 2025-PRESENT [AvanLan](https://github.com/layouwen)
