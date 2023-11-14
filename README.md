# Setup.Npmrc

This action creates a .npmrc file during Github Actions. This is useful when needing to authenticate any private dependencies, such as private npm packages, Github private packages, etc.

## Inputs

## `scope`

The scope of packages that use the registry, with the leading @. If not provided, no scope will be used in the config (e.g. `depra`).

## `domain`

**Required** The registry domain without `https://` (e.g. `npm.pkg.github.com`).

## `registry`

**Required** The name of user or organization owner of the repository (e.g. https://npm.pkg.github.com).

## `token`

**Required** The Auth Token is responsible to able the download of the files of the repository, is highly recommended pass the token through a Github secret.

<sub>Secrets variables can be configured on Repository Settings > Secrets</sup>

## `always_auth`

Force npm to always require authentication when accessing the registry.

## Example usage

```yml
uses: Depra-Inc/Setup.Npmrc@v1
  with:
    token: @EXAMPLE_TOKEN
    scope: @EXAMPLE_SCOPE
    domain: @EXAMPLE_DOMAIN
    registry: @EXAMPLE_REGISTRY
    always_auth: true
```

## Example output

```npmrc
//@EXAMPLE_DOMAIN/:_authToken=@EXAMPLE_TOKEN
@EXAMPLE_SCOPE:registry=@EXAMPLE_REGISTRY
always-auth=true
```