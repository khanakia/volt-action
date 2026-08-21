# volt-action

Installs the released [`volt`](https://github.com/khanakia/voltkit) binary (checksum-verified, ~1s — never `go install`, which would recompile volt on every fresh runner) and runs one command.

```yaml
- uses: khanakia/volt-action@v1
  with: { args: ci }
```

The pinned default `version:` is the known-good volt release; it advances when the `v1` tag moves, so consumer repos update by doing nothing. Pass `version:` explicitly to pin or to test a pre-release.

This action is deliberately logic-free — the pipeline lives in the binary (voltkit `RELEASE_PIPELINE_SPEC.md`, ADR-R07). It is a separate repo only because `@v1` must be a *moving* tag, and voltkit's tag contract is per-module *immutable* semver; mixing the two tag semantics in one repo outlives everyone's memory of why.
