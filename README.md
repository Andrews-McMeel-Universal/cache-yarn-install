# Action Template

Yyarn Install composite action for yarn 3/4+ and "nodeLinker: node-modules"

Reference: https://gist.github.com/belgattitude/042f9caf10d029badbde6cf9d43e400a

## Getting Started

```bash
git clone https://github.com/Andrews-McMeel-Universal/cache-yarn-install
```

## Installation

To make `cache-yarn-install` a part of your workflow, just add a step to one of your workflows in your `.github/workflows/` directory in your GitHub repository.

> Requirement: @setup/node should be run before

Example:

```YAML
- name: Cache Yarn Install
  uses: Andrews-McMeel-Universal/cache-yarn-install@v1
  with:
    enable-corepack: false
    cwd: ${{ github.workspace }}/apps/my-app
    cache-prefix: add cache key prefix
    cache-node-modules: false
    cache-install-state: false
```

## Options

| Variable              | Description                                                                                                                             | Required | `[Default]` |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | :------: | ----------- |
| `cwd`                 | Changes node's process.cwd() if the project is not located on the root. Default to process.cwd()                                        |          | `.`         |
| `cache-prefix`        | Add a specific cache-prefix                                                                                                             |          | `'default'` |
| `cache-npm-cache`     | Cache npm global cache folder often used by node-gyp, prebuild binaries (invalidated on lock/os/node-version)                           |          | `'true'`    |
| `cache-node-modules`  | Cache node_modules, might speed up link step (invalidated lock/os/node-version/branch)                                                  |          | `'false'`   |
| `cache-install-state` | Cache yarn install state, might speed up resolution step when node-modules cache is activated (invalidated lock/os/node-version/branch) |          | `'false'`   |
| `enable-corepack`     | Enable corepack                                                                                                                         |          | `'true'`    |
