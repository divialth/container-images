# AGENT Instructions

## Setup
Install test dependencies in the container before running tests:

```sh
apt-get update && apt-get install -y yamllint
```

## Tests
Run YAML linting for all YAML files:

```sh
yamllint .
```
