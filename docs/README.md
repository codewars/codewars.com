# Codewars Documentation

- [Introduction](#introduction)
- [Collections](#collections)
  - [languages](#languages)
  - [test_references](#test_references)
  - [references](#references)
  - [tutorials](#tutorials)
  - [infos](#infos)
  - [recipes](#recipes)
- [Development](#development)
- [Known Issues](#known-issues)
- [TODO](#todo)

## Introduction

This project makes Codewars' documentation open for contribution.

Main goals are to:

- Make contents easy to contribute
- Keep maintenance cost low
- Define structural standards

### Ease of Contribution

Documentations are plain text files using Markdown syntax.

Files containing templates may have an extension `.html`,
but the logic is separated so that markdown syntax can be used within them to write contents.

### Low Maintenance Cost

Static site generation with [Jekyll](https://jekyllrb.com/)
and hosting on GitHub Pages are handled automatically.
This setup does not require any external tools or build step.

Use of templates, data files, and YAML front matter reduces the cost of keeping information up to date.

### Structural Standards

Documentations are organized by topic and target audience.


## Collections

### `languages`

Collection of general information for each supported language.

See [_languages/README.md](_languages/README.md) for details.

### `test_references`

Collection of test framework references for each supported language.

See [_test_references/README.md](_test_references/README.md) for details.


### `references`

Collection of generic reference manuals.

See [_references/README.md](_references/README.md) for details.


### `tutorials`

Collection of documentations intended to teach/train users.

See [_tutorials/README.md](_tutorials/README.md) for details.


### `infos`

Collections of general information about Codewars platform.

See [_infos/README.md](_infos/README.md) for details.


### `recipes`

Collection of copy and paste-able solutions to common problems.

See [_recipes/README.md](_recipes/README.md) for details.


## Development

### Bundler

```
bundle install
bundle exec jekyll serve --config _config.yml,_config_dev.yml
```

### Docker

```
docker run --rm --label=jekyll \
  --volume=$(pwd):/srv/jekyll \
  -it \
  -p 127.0.0.1:4000:4000 \
  jekyll/jekyll \
  jekyll serve --config _config.yml,_config_dev.yml
```


## TODO

- Reduce complexity
- Cleanup messy markups/hacks
- Contribution guide
- License
- Improve documentation
- Consider setting up CI for PR
- Styling
  - Typography
  - Colors
  - Responsive
  - Assets
- Navigation
  - Obvious
  - Simple
  - Consistent
  - Add links to Codewars/GitHub/Gitter

- Document trade-offs, issues and reasons behind some decisions

## Known Issues

### Syntax Highlighting

There're some syntax highlighting issues because Jekyll uses older version of Rouge.

- JavaScript issues with newer syntax
- F# is not supported
- Crystal is not supported (use `ruby`). Not supported on latest Rouge either.
- PHP requires `?start_inline=true` after `php` tag.

It's possible to use client side syntax highlighters like
[Prism](http://prismjs.com/examples.html) by disabling Rouge if needed.

```yaml
highlighter: none
kramdown:
  syntax_highlighter: rouge
  syntax_highlighter_opts:
    disable: true
```

### `@mention`

Currently disabled because it interferes with code.
`@username` automatically generates a link to `codewars.com/users/username` if enabled.

Include the following in `_config.yml` to enable this.

```yaml
gems:
  - jekyll-mentions

jekyll-mentions:
  base_url: https://www.codewars.com/users
```

### Directory Structure

The document root will be less cluttered by having `_collections/:collection-name`,
but Jekyll doesn't allow placing collections in subfolders.
