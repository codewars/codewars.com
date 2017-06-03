# `languages`

Collection of general information for each supported language.

## Front Matter

```
---
title:        Title/Display Name
language:     Language tag
versions:     List of supported versions
tests:        List of supported test frameworks
packages:     List of installed packages
services:     List of services
timeout:      String describing the allowed execution time
docker_image: Docker image name

no_overview:  Disables the language overview if set to `true`.
---
```

```
---
title: JavaScript
language: javascript
versions:
  - Node v0.10.x
  - Node v6.6.x
tests:
  - Codewars
  - Mocha
packages: [] # TODO
services:
  - sqlite3
  - redis
  - mongodb
timeout: 12 seconds
docker_image: codewars/node-runner
---
```

## Output

`/languages/:path/`

## Content

Any content is included in the output `/languages/:language/` using layout `_layouts/language.html`.
