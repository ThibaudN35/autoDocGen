# autoDocGen

Small Python script to generate simple documentation from custom comment markers in source files.

The idea is to keep documentation close to the code by writing structured comments, then extracting them into a Markdown-like output file.

## Example

Input:

```python
#### @title: My Script
### @section: Functions
## @function: hello()
# @description: Prints a hello message
```

Output:

```md
# title: My Script
### section: Functions
#### function: hello()
###### description: Prints a hello message
```

## Usage

```bash
python autodocgen.py <input_file> <output_file> <config_file>
```

Example:

```bash
python autodocgen.py autodocgen.py documentation.md default_configuration.json
```

## Configuration

Patterns are defined in a JSON configuration file.

Example:

```json
[
  {
    "pattern": "^\\s*#### @(.*)",
    "transform": "# \\1"
  }
]
```

Each rule contains:

- `pattern`: regular expression used to match comments
- `transform`: output format applied to the matched line

## Supported file types

Currently supported extensions:

```
.txt, .csv, .json, .xml, .yaml, .yml, .md, .py
```

## Notes

This is a small experiment around lightweight documentation generation.

It is not meant to replace full documentation tools, but can be useful for simple scripts, lab projects or custom documentation conventions.

