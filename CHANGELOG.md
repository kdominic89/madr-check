# Changelog

Every published version is listed here with its digest.
A digest names both architectures of a version at once, `linux/amd64` and
`linux/arm64`, and it is what a workflow should pin.

## 0.1.1

```text
ghcr.io/kdominic89/madr-check@sha256:933d050d1e8d7fa00b5b13191a26c19bf40fcbeb0e2a0c4e7e6384548a993a6d
```

- `index write` starts an index, `index.md` and `index.json`, in a directory
  that has none, where the profile has one: `doka` and `ai-devops`.
  0.1.0 wrote nothing there.
- The keys of `index.json` are promised for its `schema_version`;
  the README says how.

## 0.1.0

```text
ghcr.io/kdominic89/madr-check@sha256:6cf72273d511aa00676f48741bc3436e6a00bad82bdf9d84f37b7298137ea888
```

The first version.

- `validate` holds the records of a directory to the profile they follow:
  MADR 4.0.0, the Doka MADR Enterprise Profile 1.0, or the ai-devops profile.
- `index check` says whether the directory's index matches its records.
- `index write` writes the index again from the records.
