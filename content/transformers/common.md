+++
title = "Common configuration options"
description = "Common configuration options"
date = 2021-07-06T08:00:00+00:00
updated = 2021-07-06T08:00:00+00:00
draft = false
weight = 20
sort_by = "weight"
template = "docs/page.html"

[extra]
section = "transformers"
toc = true
top = false
+++

Many of transformers don't need any configuration. You can use them just like this:

```yaml
# gets a person last name
last_name: {}
```

If there are no specific notes in the documentation for some transformer,
then there are no configuration options for it.

### Locales

Also many of them support locale configuration:

```yaml
# gets a person last name
last_name:
  locale: RU
```

Please refer [here](config.md#default) for the list of available locales.

In this document we mark such transformers with the globe symbol 🌐.

For some transformers, specifying the locale now may not have any practical effect
(but it may have an effect in the future).

### Uniqueness

You can specify that result values must be unique (they are not unique by default).
You can use short or full syntax.

Short:
```yaml
email:
  uniq: true
```

Full:
```yaml
email:
  uniq:
    required: true
    try_count: 5
```

Uniqueness is ensured by re-generating values when they are same.

You can customize the number of attempts with `try_count` (this is an optional field, the default
number of tries depends on the rule, for some rules it can be guessed automatically).

Currently, uniqueness is supported by: [email](#email), [ip](#ip), [phone](#phone),
[random_num](#random_num).

In the future, we plan to add support for the uniqueness option for all transformers.
