# nkx CLI

Public releases of `nkx` — the Nakodax customer/CI command-line tool:
`register`, `materialize`, `rehook`, `unlock`, `reseal`, `unlock-mock`,
`reseal-mock`, `status`. A single dependency-free binary; no Python or
Node.js install is required to run it.

## Install

```bash
curl -fsSL -o nkx https://github.com/nakodax/nkx-cli/releases/latest/download/nkx-linux-amd64-VERSION
curl -fsSL https://github.com/nakodax/nkx-cli/releases/latest/download/SHA256SUMS | grep nkx-linux-amd64-VERSION | sha256sum -c -
chmod +x nkx
```

Or via Homebrew (macOS/Linux):

```bash
brew install nakodax/tap/nkx
```

Replace `VERSION` and `linux-amd64` with the release and platform you need —
darwin/windows/arm64 assets are published under the same tag, named the
same way.

Every release asset is signed with keyless `cosign sign-blob`. See a
release's notes for the exact `cosign verify-blob` command.

## Use

Your Nakodax dashboard's Connect page for a protected repository gives you
the exact command and credentials for your setup — a deployment, or a CI
build.
