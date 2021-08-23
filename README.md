# `archetect render` GitHub Action

[![Maintained by Scaffoldly](https://img.shields.io/badge/maintained%20by-scaffoldly-blueviolet)](https://github.com/scaffoldly)
![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/scaffoldly/archetect-render-action)
![Archetect Version](https://img.shields.io/badge/archetect-%3E%3D0.6.1-blue.svg)

This action runs an [Archetect](https://github.com/archetect/archetect) `render`
command using template files contained in `source` and outputs to `destination`.

`source` can be a directory relative to where the action is running or a URL to
a Git repository (e.g. `https://github.com/scaffoldly/archetype-scaffoldly-bootstrap.git`).

## Inputs

### `source` (**Required**)

The source directory or Git repo containing an `archetype.yml`

### `destination` (_Optional_)

The destination of the rendered output

**Default**: `.`

### `github-token` (_Optional_)

A GitHub token with `repo` and `workflow` permissions

_Note_: Useful if Archetect is rendering `.github/workflow` files

**Default**: The GitHub token provided by the GitHub Workflow

### `options` (_Optional_)

Additional command-line options for the archetect command (e.g. `-a`, `-A`, `-s`)

From `archetect render --help`:

```
FLAGS:
    -h, --help
            Prints help information

    -o, --offline
            Only use directories and already-cached remote git URLs

    -V, --version
            Prints version information

    -v, --verbose
            Increases the level of verbosity

OPTIONS:
    -a, --answer <key=value>...
            Supply a key=value pair as an answer to a variable question. This option may be specified more than once.

            Valid Input Examples:

            key=value
            key='multi-word value'
            key="multi-word value"
            "key=value"
            'key=value'
            'key="multi-word value"'
            "key = 'multi-word value'"
    -A, --answer-file <path>...
            Supply an answers file as answers to variable questions. This option may be specified more than once.

    -s, --switch <switches>...
            Enable switches that may trigger functionality within Archetypes
```

**Default**: `` (empty string)

### `commit` (_Optional_)

If set, changes will be committed back into the repository

**Default**: `"true"`

## Outputs

This action has no outputs

## Example usage

Run a `archetect render` and provide answers as `options`:

```yaml
- uses: actions/checkout@v2
- uses: scaffoldly/archetect-render-action@v1
  with:
    source: "https://github.com/scaffoldly/archetype-scaffoldly-bootstrap.git"
    options: "-a nonlive_domain=myproject.dev -a live_domain=myproject.com"
```

Run a `archetect render` and provide an answers file:

```yaml
- uses: actions/checkout@v2
- uses: scaffoldly/archetect-render-action@v1
  with:
    source: "https://github.com/scaffoldly/archetype-scaffoldly-bootstrap.git"
    options: "-A ./path/to/answers.yml"
```
