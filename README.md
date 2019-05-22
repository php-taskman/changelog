# Taskman Changelog

Generate changelogs using [Github Changelog Generator](https://github.com/github-changelog-generator/github-changelog-generator).

## Generate the changelog of this package

Make sure you have a Github token, if not, [create one](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line).

Then, create a `taskman.yml` file in the project's root:

```yaml
github:
  token: REPLACE_WITH_YOUR_TOKEN_HERE
  changelog:
    user: php-taskman
    project: changelog
    filename: CHANGELOG.md
    release:
      branch: 0.x
    between-tags: $(git tag --sort=-creatordate --merged '${github.changelog.release.branch}' | tr '\n' ',')
    extra: --no-unreleased
```

and then:

```bash
./vendor/bin/taskman github:changelog
```

For more information about how to customise the building process check 
[Taskman Changelog](https://github.com/php-taskman/changelog) project page.
