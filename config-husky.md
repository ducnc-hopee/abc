# Config husky

## 1/ Install husky

To install husky, run:

```bash
npx husky-init
```

## 2/ Config

Then, In the .husky/pre-commit file, please modify the code as shown below:

```bash
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

yarn lint
```
