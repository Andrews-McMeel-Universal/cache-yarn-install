# Action Template

This is a Yarn Install composite action designed for Yarn versions 3/4+ and "nodeLinker: node-modules". It helps to cache and speed up your Yarn installations in your GitHub workflows.

Reference: [Gist](https://gist.github.com/belgattitude/042f9caf10d029badbde6cf9d43e400a)

## Getting Started

To get started, clone the repository:

```bash
git clone https://github.com/Andrews-McMeel-Universal/cache-yarn-install
```

## Installation

To integrate `cache-yarn-install` into your workflow, add a step to one of your workflows in the `.github/workflows/` directory of your GitHub repository.

> **Note:** The `@setup/node` action should be run before this action.

Here's an example of how to use it:

```YAML
- name: Cache Yarn Install
  uses: Andrews-McMeel-Universal/cache-yarn-install@v1
  with:
    enable-corepack: false
    cwd: ${{ github.workspace }}/apps/my-app
    cache-prefix: 'your-cache-key-prefix'
    cache-node-modules: false
    cache-install-state: false
```

## Options

Here are the options you can configure for this action:

| Variable              | Description                                                                                                                             | Required | Default |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | :------: | ------- |
| `cwd`                 | Changes node's process.cwd() if the project is not located at the root. Defaults to process.cwd()                                      |    No    | `.`     |
| `cache-prefix`        | Adds a specific cache-prefix.                                                                                                           |    No    | `'default'` |
| `cache-npm-cache`     | Caches npm global cache folder often used by node-gyp, prebuild binaries. Invalidated on lock/os/node-version changes.                  |    No    | `'true'`    |
| `cache-node-modules`  | Caches node_modules to potentially speed up the link step. Invalidated on lock/os/node-version/branch changes.                          |    No    | `'false'`   |
| `cache-install-state` | Caches yarn install state to potentially speed up the resolution step when node-modules cache is activated. Invalidated on lock/os/node-version/branch changes. |    No    | `'false'`   |
| `enable-corepack`     | Enables corepack.                                                                                                                       |    No    | `'true'`    |
