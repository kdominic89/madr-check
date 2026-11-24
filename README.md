# madr-check

Holds a directory of decision records (ADRs) to its profile and keeps its
index.
One statically linked program in a container: no shell, no network.

## Use

Run it in the repository whose records you want checked:

```sh
docker run --rm --network none --volume "$PWD:/work:ro" \
  ghcr.io/kdominic89/madr-check validate docs/decisions
```

Every finding names its file and line.
Any finding is a non-zero exit, so the same line works as a pull request check.

## Commands

| Command | What it does |
| --- | --- |
| `validate [DIR]` | Holds the records to the profile they follow. |
| `index check [DIR]` | Says whether the index matches the records. Writes nothing. |
| `index write [DIR]` | Writes the index again from the records. |

`DIR` defaults to `docs/decisions`.

`index write` changes files, so it needs the mount writable.
On Linux it also needs your own identity,
because the program in the image does not run as you:

```sh
docker run --rm --network none --user "$(id -u):$(id -g)" \
  --volume "$PWD:/work" \
  ghcr.io/kdominic89/madr-check index write docs/decisions
```

Text you wrote around the index table is kept as it is.
An index somebody keeps by hand is left alone and named.

## Profiles

`--profile auto`, the default, reads the profile from the keys the records
carry.
To name it instead:

| Value | Profile |
| --- | --- |
| `madr` | MADR 4.0.0 |
| `doka` | Doka MADR Enterprise Profile 1.0 |
| `ai-devops` | the ai-devops profile |

## Exit codes

| Code | Meaning |
| --- | --- |
| 0 | No finding. |
| 1 | At least one finding; each is printed as `path:line: message`. |
| 2 | The directory could not be judged, for example a mount that is read-only when the index is to be written. |

## Pin it

A tag can be moved and a digest cannot.
In a workflow, name the image by the digest of the version you checked,
`ghcr.io/kdominic89/madr-check@sha256:...`, and not by its tag.
The digest of every version is in the [changelog](CHANGELOG.md).

## Reporting a problem

A finding you think is wrong, or a record the program should refuse and does
not: open an issue here, with the command and the smallest record that shows
it.
A vulnerability is reported privately, as [SECURITY.md](SECURITY.md) says.

The source is not published, so there is nothing to send a change against.

## Terms

Free to run and to pass on unmodified, also commercially.
The full terms are in [TERMS.md](TERMS.md).
The same file is in the image under `/licenses`, beside the license notices of
the open-source crates linked into the program.
