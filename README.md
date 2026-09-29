# nkx: command-line tool for NakodaX protected software

**nkx is the NakodaX command-line tool for running and building software whose source code is protected by [NakodaX Source Protection](https://nakodax.com/source).** It lets a deployment or a CI build unlock protected code only when it runs, under permission you control. It is a single dependency-free binary for macOS, Linux and Windows. No Python or Node.js install is required.

If you want to send large video or audio recordings to NakodaX box instead, see [nkx-upload](https://github.com/nakodax/nkx-upload).

## What nkx is for

Software vendors often have to hand partners or contractors a readable copy of their source code. Once that copy is out, it can be copied, kept after the contract ends, or fed to an AI tool. With NakodaX Source Protection the code stays encrypted, and nkx is the tool that asks for permission and unlocks it at run time, on the machine that is allowed to run it.

- Deploy software to another party's servers without giving them readable source code.
- Unlock protected code in a CI build or a deployment.
- End access for one deployment without affecting the others.

## Install

**Homebrew (macOS and Linux)**

```bash
brew install nakodax/tap/nkx
```

**Direct download (Linux example)**

```bash
curl -fsSL -o nkx https://github.com/nakodax/nkx-cli/releases/latest/download/nkx-linux-amd64-VERSION
curl -fsSL https://github.com/nakodax/nkx-cli/releases/latest/download/SHA256SUMS | grep nkx-linux-amd64-VERSION | sha256sum -c -
chmod +x nkx
```

Replace `VERSION` and `linux-amd64` with the release and platform you need. darwin, windows and arm64 assets are published under the same tag with the same naming.

Every release asset is signed with keyless [Sigstore cosign](https://docs.sigstore.dev) (`cosign sign-blob`). Each release's notes give the exact `cosign verify-blob` command.

## Commands

| Command | What it does |
|---|---|
| `nkx register` | Register a deployment or CI build with NakodaX |
| `nkx materialize` | Prepare protected code for use |
| `nkx rehook` | Re-attach protection after a change |
| `nkx unlock` | Unlock protected code for the current run |
| `nkx reseal` | Seal the code again after use |
| `nkx unlock-mock` / `nkx reseal-mock` | Test the unlock and reseal flow locally |
| `nkx status` | Show the current state |

Your NakodaX dashboard's **Connect** page for a protected repository gives you the exact command and credentials for your setup, whether that is a deployment or a CI build.

## FAQ

### What is nkx?

nkx is the command-line tool for NakodaX Source Protection. It unlocks encrypted source code at run time, on an approved machine, so a vendor can ship working software without shipping readable source.

### Do I need Python or Node.js to run nkx?

No. nkx is a single binary with no dependencies.

### How do I check that a download is genuine?

Compare the file with the release's `SHA256SUMS`, or verify its cosign signature using the command in the release notes.

### Can access be ended after deployment?

Yes. Access is checked each time protected code is unlocked, so you can end it for one deployment without affecting others.

## About NakodaX

NakodaX helps you keep control of sensitive work after you share it. It protects documents, data pipelines, media and software with encryption and permission checks at the point of use, so you can change, limit or revoke access at any time. NakodaX does not store or access the readable version of your content.

- [nakodax.com](https://nakodax.com)
- [Source Protection](https://nakodax.com/source)
- [Security](https://nakodax.com/security)
- [Support](https://nakodax.com/support)
