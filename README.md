# GitHub Action Global Environment

Register global evironment from text file.

## Pre-requisites

1. Create text file (e.g. `secrets.txt`) that contains multiple line of `key=value`
2. Base 64 encode file content
3. Add encoded value as github secrets call it GLOBAL_ENV or whatever name you feel right

## Usage

Create dummy filee.g `env.tmp` and add your environment variables in `key=value` format.

```text
VAR1=value
VAR2=value
PASSWORD=::add-mask::secret
```

Save and encode the content using `cat env.tmp | base64 -w 0` then encoded text and put it in your GitHub secrets.

Example step, loading environment variables from `GLOBAL_ENV` secrets.

```bash
- uses: webjet/action-env-loader@v1
  with:
    config: ${{ secrets.GLOBAL_ENV }}
```

## Security Risk

By default ENV will output to log. If you don't want to environment value output you can add `::add-mask::` in front of the value e.g. `PASSWORD=::add-mask::$up3rCr3t`