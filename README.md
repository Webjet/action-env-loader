# GitHub Action Global Environment

Register global evironment from text file.

## Pre-requisites

1. Create text file (e.g. `secrets.txt`) that contains multiple line of `key=value`
2. Base 64 encode file content
3. Add encoded value as github secrets call it GLOBAL_ENV or whatever name you feel right

## Usage

Example config text

```text
VAR1=value
VAR2=value
PASSWORD=::add-mask::secret
```

Example step

```bash
- uses: webjet/action-env-loader@v1
  with:
    config: ${{ secrets.GLOBAL_ENV }}
```

