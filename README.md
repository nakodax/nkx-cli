# nkx CLI

Public binary releases for `nkx` — the Nakodax customer/CI CLI
(register / materialize / rehook / unlock / reseal / unlock-mock /
reseal-mock / status).

Source lives in the private `nakodax/nakodax` monorepo
(`packages/nkx-cli`); this repo hosts only signed Release assets so the
binary can be downloaded without a token.

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

Every release asset is signed with keyless `cosign sign-blob`. See a
release's notes for the exact `cosign verify-blob` command.
