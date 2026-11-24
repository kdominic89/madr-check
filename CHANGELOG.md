# Changelog

Every published version is listed here with its digest.
A digest names both architectures of a version at once, `linux/amd64` and
`linux/arm64`, and it is what a workflow should pin.

## Unreleased

### 0.1.0

The first version.

- `validate` holds the records of a directory to the profile they follow:
  MADR 4.0.0, the Doka MADR Enterprise Profile 1.0, or the ai-devops profile.
- `index check` says whether the directory's index matches its records.
- `index write` writes the index again from the records.
