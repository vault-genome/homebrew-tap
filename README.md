# Homebrew tap for Vault Genome

The two tools a person runs on their own machine — `acpctl` and
`acp-keygen` of [vaultgenome-core](https://github.com/vault-genome/vaultgenome-core) —
for macOS (Apple silicon and Intel) and Linux (x86-64 and arm64):

```bash
brew install vault-genome/tap/vaultgenome
acpctl version
```

The formula installs the binaries of a signed release as they are: each
`url` is a release asset, and each `sha256` is the line of that release's
`checksums-<tag>.txt` — the list the release workflow signs, verified under
the workflow's identity by the script that writes the formula
(`bin/update-formula.sh vX.Y.Z`; nothing in `Formula/` is typed by hand).
The release page carries, for every file, a Sigstore signature, a Sigstore
bundle for a machine with no route, an SBOM and a SLSA provenance; the
repository's README, "Download and verify a release", says how to check
them.

The daemons (`sagvd`, `acp-compute`, `acp-bootstrap`) are not here: they
run on Linux x86-64 hosts with the confidential-computing hardware they
attest with, from the release's signed binaries or images.

`brew upgrade vaultgenome` follows the releases. The formula's version is
the release tag.
