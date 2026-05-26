# Dependabot Version Updates - Example

Adapted from https://github.com/mkyong/maven-examples.git

## Dependabot Configuration

This repository uses Dependabot for automated dependency version updates. The configuration lives in [`.github/dependabot.yml`](.github/dependabot.yml).

### Cooldown (supply-chain best practice)

The `cooldown` field instructs Dependabot to wait a number of days after a new version is published before opening a pull request. This gives the community time to discover and report problems (e.g. a compromised package or a breaking release) before the update lands in your codebase.

```yaml
cooldown:
  default-days: 3   # wait 3 days after a new version is published
```

You can also set ecosystem- or package-specific overrides:

```yaml
cooldown:
  default-days: 3
  semver-major-days: 7   # extra caution for major-version bumps
```

See the [Dependabot cooldown documentation](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuration-options-for-the-dependabot.yml-file#cooldown) for all available options.

### Dependency groups

Dependencies are grouped into `production-dependencies` and `development-dependencies` so that each Dependabot run produces at most one PR per group instead of one PR per package.
