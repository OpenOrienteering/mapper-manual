---
title: Command line interface
authors:
  - Michael Behrens
last_modified_date: 06 July 2026
parent: Reference
nav_order: 0.5
---

## Introduction

The command line interface (CLI) brings functions from inside of Open Orienteering Mapper into the command line.
This is usually used to programmatically execute actions of the software, e.g. in scripts or continuous integration workflows.

## Usage

The CLI is embedded in the main Mapper binary and can be invoked by placing a `--cli` behind the main command.

```bash
Mapper --cli <subcommand> [options]
```

Qt options (such as `-platform offscreen`) may be placed before `--cli`:

```bash
Mapper -platform offscreen --cli export -i map.omap -o map.pdf
```

## Commands

| Subcommand | Description |
|------------|-------------|
| `help`     | Show this help and a list of available subcommands |
| `export`   | Export the map to printable and image formats |
| `convert`  | Convert between orienteering map formats |

### help

Displays a list of available subcommands and usage information.

```bash
Mapper --cli help
```

### export

Exports a map to PDF or image formats (PNG, JPEG, TIFF, BMP, WEBP, …).

Options:

| Option | Description | Comment |
|--------|-------------|-------|
| `-i`, `--input <path>` | Input map file. | *required* |
| `-o`, `--output <path>` | Output file path. | *required* |
| `--output-format <id>` | Output format ID (e.g. `pdf`, `png`, `jpg`). | When not specified, the format is derived from the file extension. |
| `--full-map` | Export the full map extent instead of the saved print area. | |
| `--dpi <dpi>` | Output resolution in DPI. | default: 300 |
| `-h`, `--help` | Show help for export command. | |

Examples:

```bash
# Export to PDF
Mapper --cli export -i map.omap -o map.pdf

# Export full map extend to PNG at 600 DPI
Mapper --cli export -i map.omap -o map.png --dpi 600 --full-map

# Override format using output-format, will produce a png with a .pdf extension
Mapper --cli export -i map.omap -o map.pdf --output-format png
```

### convert

Converts between orienteering map formats (e.g. OMAP, XMAP, OCD) and to GIS formats.

Options:

| Option | Description | Comment|
|--------|-------------|-------|
| `-i`, `--input <path>` | Input map file. | *required* |
| `-o`, `--output <path>` | Output file path. | *required* |
| `--output-format <id>` | Output format ID (e.g. `XML`, `OCD`, `OCD12`).  | When not specified, the format is derived from the file extension. |
| `-h`, `--help` | Show help for convert command. | |

Examples:

```bash
# Convert between native formats
Mapper --cli convert -i map.omap -o map.xmap
Mapper --cli convert -i map.xmap -o map.omap

# Convert to OCD format
Mapper --cli convert -i map.omap -o map.ocd
Mapper --cli convert -i map.omap -o map.ocd --output-format OCD9

# Explicit format selection
Mapper --cli convert -i map.omap -o map.gpx
```


## Notes

- Any Qt options need to be passed before the `--cli` flag.
- Error messages are printed to stderr.
