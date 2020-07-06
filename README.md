# bouncer

![app-pipeline](https://github.com/wagoodman/go-bouncer/workflows/app-pipeline/badge.svg)
![Go Report Card](https://goreportcard.com/badge/github.com/wagoodman/go-bouncer)

A go dependency license checker.

*This is thin a wrapper around [google's license classifier](github.com/google/licenseclassifier) forked from [go-license](github.com/google/go-licenses) with a few extra options.*

## Installation

```bash
# install the latest version to ./bin
curl -sSfL https://raw.githubusercontent.com/wagoodman/go-bouncer/master/bouncer.sh | sh 

# install a specific version to another directory
curl -sSfL https://raw.githubusercontent.com/wagoodman/go-bouncer/master/bouncer.sh | sh -s -- -b ./path/to/bin v1.26.0
```

## Usage

```bash
# list the licenses of all of your dependencies...
bouncer list                        # ... from ./go.mod
bouncer list ~/some/path            # ... from ~/some/path/go.mod
bouncer list github.com/some/repo   # ... from a remote repo

# pass/fail of user-specified license restrictions (by .bouncer.yaml)
bouncer check
bouncer check ~/some/path
bouncer check github.com/some/repo
```

The `.bouncer.yaml` can specify a simple allow-list or deny-list license name regex patterns (by SPDX name):

```bash
permit:
  - BSD.*
  - MIT.*
  - Apache.*
  - MPL.*
```

```bash
forbid:
  - GPL.*
```

```bash
ignore-packages:
  - github.com/some/repo
forbid:
  - GPL.*
```

Note: either allow or deny lists can be specified, not both.
