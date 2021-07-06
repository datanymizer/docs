+++
title = "Basic generators"
description = ""
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 30
sort_by = "weight"
template = "docs/page.html"

[extra]
section = "transformers"
toc = true
top = false
+++

### boolean

Gets a boolean value (TRUE/FALSE), with a given probability.

Examples:

The default:

```yaml
boolean: {}
```

You can specify the probability of TRUE value:

```yaml
boolean:
  # 40% for the TRUE and 60% for the FALSE
  ratio: 40
```

### datetime

Generates random dates.

Examples:

The default:

```yaml
datetime: {}
```

You can specify a range:

```yaml
datetime:
  from: 1990-01-01T00:00:00+00:00
  to: 2010-12-31T00:00:00+00:00
```

Also, you can specify datetime format
([available specifiers](https://docs.rs/chrono/0.4.19/chrono/format/strftime/index.html)).
Be careful with this option

```yaml
datetime:
  format: %Y-%m-%dT%H:%M:%S%.f%:z
```

#### digit

Gets a localized digit symbol (e.g., `2` or `5` for the English locale).

### random_num

Gets a random number.

Examples:

The default:

```yaml
random_num: {}
```

You can specify a range (one border or both):

```yaml
random_num:
  min: 10
  max: 20
```

The default range is from `0` to `2^64 - 1` (for 64-bit application binary).

If you want to generate unique numbers, use this option:

```yaml
random_num:
  uniq: true
```

The transformer will collect information about generated numbers and check their uniqueness.
If such a number already exists in the list, then the transformer will try to generate the value again.
You can limit the number of tries (the default is `3`):

```yaml
random_num:
  uniq:
    required: true
    try_count: 5
```

### raw_date

Gets a random date (without formatting).

```
TODO: Examples
```

### raw_datetime

Gets a random datetime (without formatting).

```
TODO: Examples
```

#### color

Gets a color code (e.g., `#ffffff`).
```
TODO: Examples
```
