# nkx: command-line tool for NakodaX Source Protection

**nkx is the command-line tool for [NakodaX Source Protection](https://nakodax.com/source).** In a CI build it decrypts the protected files your compiler needs and re-encrypts the compiled output afterwards. For a developer it unlocks protected code for an approved change session and reseals it when the session ends. It is a single dependency-free binary for macOS, Linux and Windows, so no Python or Node.js install is required.

To run the protected software itself, use the runtime SDK: [`@nakodax/runtime`](https://www.npmjs.com/package/@nakodax/runtime) for Node.js.

If you want to send large video or audio recordings to NakodaX box instead, see [nkx-upload](https://github.com/nakodax/nkx-upload).

## What nkx is for

Source code often has to be shared with vendors, contractors and partners so they can build, maintain or deploy software. Once a readable copy is out, it can be copied, kept after the engagement ends, or fed to an AI tool. With NakodaX Source Protection the code stays encrypted. nkx is the tool that gets a CI build or an approved developer the access they are licensed for, and puts the protection back afterwards.

- Decrypt protected files for a CI build step, then re-encrypt the compiled output.
- Unlock protected code for an approved change session, then reseal it.
- Set up a protected repository's credentials from a Register Token.

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

Replace `VERSION` and `linux-amd64` with the release and platform you need. Each release publishes macOS (`darwin`), Linux and Windows binaries for both `amd64` and `arm64`, under the same naming.

Every release asset is signed with keyless [Sigstore cosign](https://docs.sigstore.dev) (`cosign sign-blob`). Each release's notes give the exact `cosign verify-blob` command.

## Commands

| Command | What it does |
|---|---|
| `nkx register` | Set up credentials for a protected repository from a Register Token |
| `nkx materialize <repo> --into DIR` | In CI, decrypt the protected files into a folder ahead of your own compiler |
| `nkx rehook <repo> --src-root DIR --dist-dir DIR` | In CI, re-encrypt compiled TypeScript or JavaScript output after your build |
| `nkx unlock <repo>` | Decrypt this release's protected files for local editing in an approved change session |
| `nkx reseal <repo>` | Re-encrypt the files and remove the plaintext, ending the session |
| `nkx unlock-mock <repo> <file>` | Decrypt one file's mock stub so you can edit it by hand |
| `nkx reseal-mock <repo> <file>` | Re-encrypt one file's hand-edited mock stub |
| `nkx status <repo>` | Show whether the repository is protected or unlocked |

Your NakodaX Source Console's **Connect** page for a protected repository gives you the exact command and credentials for your setup.

### Exit codes

| Code | Meaning |
|---|---|
| `0` | Success |
| `2` | Authentication or license denied |
| `3` | Network unreachable |
| `4` | Usage error |

## FAQ

### What is nkx?

nkx is the command-line tool for NakodaX Source Protection. It handles the CI and developer-session side of protected source code: decrypting files for a build, re-encrypting the output, and unlocking and resealing code for an approved change session.

### Does nkx run my protected software?

No. Running the protected software is the job of the runtime SDK, for example [`@nakodax/runtime`](https://www.npmjs.com/package/@nakodax/runtime) for Node.js. nkx covers CI builds and developer change sessions.

### Do I need Python or Node.js to run nkx?

No. nkx is a single binary with no dependencies.

### How do I check that a download is genuine?

Compare the file with the release's `SHA256SUMS`, or verify its cosign signature using the command in the release notes.

## About NakodaX

NakodaX helps you keep control of sensitive work after you share it. It protects documents, data pipelines, media and software with encryption and permission checks at the point of use, so you can change, limit or revoke access at any time. NakodaX does not store or access the readable version of your content.

- [nakodax.com](https://nakodax.com)
- [Source Protection](https://nakodax.com/source)
- [Developer tools](https://nakodax.com/developers)
- [Security](https://nakodax.com/security)
- [Support](https://nakodax.com/support)
