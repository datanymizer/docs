+++
title = "Text (lorem ipsum or its analog)"
description = ""
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 44
sort_by = "weight"
template = "docs/page.html"

[extra]
section = "transformers"
toc = true
top = false
+++


### paragraph

Gets a "lorem" paragraph (you can specify a count of sentences).

Examples:

The default:

```yaml
paragraph: {}
```

This is equal to:

```yaml
paragraph:
  locale: EN
  # Min count
  min: 2
  # Max count
  max: 5
```

### paragraphs

Gets several "lorem" paragraphs (you can specify a count).

Examples:

The default:

```yaml
paragraphs: {}
```

This is equal to:

```yaml
paragraphs:
  locale: EN
  # Min count
  min: 2
  # Max count
  max: 5
```

### sentence

Gets a "lorem" sentence (you can specify a count of words).

Examples:

The default:

```yaml
sentence: {}
```

This is equal to:

```yaml
sentence:
  locale: EN
  # Min count
  min: 2
  # Max count
  max: 5
```

### sentences

Gets several "lorem" sentences (you can specify a count).

Examples:

The default:

```yaml
sentences: {}
```

This is equal to:

```yaml
sentences:
  locale: EN
  # Min count
  min: 2
  # Max count
  max: 5
```

### word

Gets a "lorem" word.

### words

Gets several "lorem" words (you can specify a count).

Examples:

The default:

```yaml
words: {}
```

This is equal to:

```yaml
words:
  locale: EN
  # Min count
  min: 2
  # Max count
  max: 5
```

### hex_token

Generates random hex tokens. You can set the token length (default is 32).

Examples:

The default:

```yaml
  hex_token: {}
```

With a custom length:

```yaml
hex_token:
  len: 128
```
