# bootstrap-action action

This action runs an (Archetect)[https://github.com/archetect/archetect] `render`
command using template files contained in `source` and outputs to `destination`

## Inputs

### `source` (_Optional_)

The source directory containing `archetype.yml`

**Default**: `.archetect`

### `destination` (_Optional_)

The destination of the rendered output

**Default**: `.`

### `options` (_Optional_)

Additional command-line options for the archetect command (e.g. `-a`, `-A`, `-s`)

From `archetect render --help`

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

## Outputs

This action has no outputs

## Example usage

Run a `archetect render` and provide answers as `options`:

```yaml
- uses: actions/checkout@v2
- uses: scaffoldly/archetect-render-action@v1
  with:
    options: "-a author=Christian -a email=christian@example.com"
```

Run a `archetect render` and provide an answers file:

```yaml
- uses: actions/checkout@v2
- uses: scaffoldly/archetect-render-action@v1
  with:
    options: "-A ./archetect/default-answers.yml"
```
