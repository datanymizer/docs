+++
title = "Special generators"
description = ""
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 31
sort_by = "weight"
template = "docs/page.html"

[extra]
section = "transformers"
toc = true
top = false
+++

#### none

This transformer just does nothing (some sort of `noop`).

Example:

```yaml
# You should use ~ (the null value in YAML) for this transformer
none: ~
```

#### capitalize

Capitalize a given value (from the database, or a previous value in the pipeline).

E.g., the `3 short words` value will be transformed to `3 Short Words`.

Example:

```yaml
# You should use ~ (the null value in YAML) for this transformer
capitalize: ~
```

#### pipeline

You can use pipelines with complicated rules to generate more difficult values.
You can use any transformers as steps (as well as other pipelines too)

Example:

```yaml
pipeline:
  pipes:
    - email: {}
    - capitalize: ~
```

The pipes will be executed in the order in which they are specified in the config.

#### template

This is the most sophisticated and flexible transformer.

It uses the [Tera](https://tera.netlify.app) template engine
(inspired by [Jinja2](https://jinja.palletsprojects.com)).

Specification:

| Section                   | Mandatory | YAML type  | Description
|---                        |---        |---         |---
| `format`                  | yes       | text       | The template for generated value
| `rules`                   | no        | list       | Nested rules (transformers). You can use them in the template
| `variables`               | no        | dictionary | Template variables

Examples:

```yaml
template:
  format: "Hello, {{name}}! {{_1}}:{{_0 | upper}}"
  rules:
    - email: {}
  variables:
    name: Alex
```

where:
* `_0` - transformed value (original);
* `_1`, `_2`, ... `_N` - nested rules by index (started from 1). You can use any transformer (including templates);
* `name` - the named variable from the `variables` section.

It will generate something like `Hello, Alex! some-fake-email@gmail.com:ORIGINALVALUE`.

You can use any filter or markup from the Tera template engine.

Also, you can use the [global](config.md#globals) variables in templates.

You can reference values of other row fields in templates.
Use the `prev` special variable for original values and the `final` special variable - for anonymized:

```yaml
tables:
  - name: some_table
    # You must specify the order of rule execution when using `final`
    rule_order:
      - greeting
      - options
    rules:
      first_name:
        first_name: {}
      greeting:
        template:
          # Keeping the first name, but anonymizing the last name
          format: "Hello, {{ prev.first_name }} {{ final.last_name }}!"
      options:
        template:
          # Using the anonymized value again
          format: "{greeting: \"{{ final.greeting }}\"}"
```

You must specify the order of rule execution when using `final` with [rule_order](config.md#rule_order).
All rules not listed will be placed at the beginning (i.e., you must list only rules with `final`).
