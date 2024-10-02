Test repo for rewatch with PNPM. Forked from testrepo on the rewatch subreddit, and adapted for PNPM.

The [pnpm-workspace.yaml](./pnpm-workspace.yaml) is used to define the workspaces in this monorepo.

To run, initialize the repo using corepack (comes with node) and pnpm install to setup dependencies:

```
corepack enable
pnpm install
```

Then try to run `pnpm build` and note that the packages within the monorepo cannot be found

```
❯ pnpm build

> testrepo@ build /rewatch-pnpm
> rewatch build .

[1/7]📦 Building package tree...[1/2] ️🛑  Error building package tree. The package "@testrepo/dep02" is not found (are node_modules up-to-date?)... ELIFECYCLE  Command failed with exit code 2.
❯ git init
Initialized empty Git repository in /rewatch-pnpm/.git/
```

No modifications done to package structure. Typically you can run `pnpm --filter "@testrepo/dep01" res:build`, and that's resolving but the build command is missing dependencies and there's a circular one.