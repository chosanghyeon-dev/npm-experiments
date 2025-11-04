# npm-experiments

A monorepo for experimental npm packages. Rapidly prototype and test various ideas, with validated packages split into separate repositories.

> **Note**: This repository is a development and experimental playground. Check each package's documentation for production usage.

## Packages

- `@csh-js/react-responsive` - Breakpoint-based component library for React responsive UI

## Development Guide

### Update library version

```shell
pnpm changeset
```

### Run a specific package

```shell
pnpm --filter [package] [command]
```
