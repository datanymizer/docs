+++
title = "Transformers"
description = ""
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 10
sort_by = "weight"
template = "docs/page.html"

[extra]
section = "transformers"
toc = true
top = true
+++

We call the anonymization rules for the table columns `transformers`.

You should use them in the [rules](config.md#rules) sections of the configuration file.

Example:

```yaml
rules:
  # `field_name` is a name of database column
  field_name:
    # gets a person full name
    person_name: {}
```

In other examples we will omit the `rules.field_name` part.

This document contains the full list of transformers (grouped by categories).
