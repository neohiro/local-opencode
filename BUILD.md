# Build the desktop binary with the local provider

The `local` provider is compiled into the opencode desktop Electron binary via:

```bash
# From deploy_target/ (uses default branch dev)
git checkout main        # if needed
bun install --cwd packages/desktop
bun --cwd packages/desktop build       # electron-vite build to out/
bun --cwd packages/desktop package     # electron-builder produces a distributable archive
```

Prerequisites in the workspace:
- `tsgo` (TypeScript 7 Go native compiler) — the package script `typecheck` runs `tsgo -b`. Install it where it's available, e.g. `npm install -g @mxyhi/tsgo` or via the repo's CI runner. If `tsgo` is missing in a session, typecheck aborts but source edits are still valid; the resulting `electron-vite build` only needs Bun + the `effect`, `electron-log`, etc. runtime deps.
- The built app must target Linux x86-64 for this deployment (Windows or macOS targets can be produced separately).

Output names the dist artifact and goes here as an asset. The default output path is `out/main/index.js` plus bundled renderer chunks; `packages/desktop/electron-builder.config.ts` controls where the final `.zip` lands on `packages/desktop/dist/linux-x64/`.

Only after release can the binary be attached as an asset or GitHub Release, then the endpoint config (`wsl-desktop.beaver-sidewinder.ts.net:1234`) applies the same way as the snippet in this repo.
