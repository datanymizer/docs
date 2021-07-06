+++
title = "Internet and communications"
description = "Transformers to use with internet topics"
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 40
sort_by = "weight"
template = "docs/page.html"

[extra]
section = "transformers"
toc = true
top = false
+++

### domain_suffix

Gets a domain suffix (e.g., `com`).
```
TODO: Examples
```

### email

Gets a random email. You can specify a kind. The kind can be `Safe` (it is default) or `Free`.

With the `Safe` kind the transformer generates only emails for example domains (e.g., `some@example.com`).
It is not real email addresses.

With the `Free` kind the transformer generates emails for free email providers (e.g., `some@gmail.com`,
`some@yahoo.com`, `some@hotmail.com`).

Examples:

The default:

```yaml
email: {}
```

You can specify the kind:

```yaml
email:
  kind: Free
```

If you want to generate unique emails, use this option:

```yaml
email:
  uniq: true
```

The transformer will collect information about generated emails and check their uniqueness.
If such a email already exists in the list, then the transformer will try to generate the value again.
You can limit the number of tries (the default is `3`):

```yaml
email:
  uniq:
    required: true
    try_count: 5
```

### free_email_provider

Gets a free email provider name (e. g., `gmail.com`).
```
TODO: Examples
```

### ip

Generates an IP address.

You can specify the kind (`V4` or `V6`).

Examples:

The default:

```yaml
ip: {}
```

Default kind is `V4`, you can specify V6:

```yaml
ip:
  kind: V6
```

### local_cell_phone

Gets a local cell phone number (for a given locale).
```
TODO: Examples
```

### local_phone

Gets a local phone number (for a given locale).
```
TODO: Examples
```

### mac_address

Gets a MAC address.
```
TODO: Examples
```

### password

Generates a random password.

You can set minimum and maximum string length.

Examples:

The default:
```yaml
  password: {}
```

With a custom length (the default `min` option is `8` and the `max` option is `20`):

```yaml
password:
  min: 5
  max: 10
```

### phone

Gets a random phone number.

Examples:

The default:

```yaml
phone: {}
```

You can specify the phone format:

```yaml
phone:
  format: "+7^#########"
```

where:
* `#` - any digit from 0 to 9
* `^` - any digit from 1 to 9

Also, you can use any other symbols in format: `^##-00-### (##-##)`.

The default format is `+###########`.

If you want to generate unique phone numbers for this database column, use the `uniq` option:

```yaml
phone:
  uniq: true
```

The transformer will collect information about generated numbers and check their uniqueness.
If such a number already exists in the list, then the transformer will try to generate the value again.
The number of attempts is limited by the number of available invariants based on the format.

### user_agent

Gets a User-Agent header.
```
TODO: Examples
```

### username

Gets a username (login).
```
TODO: Examples
```
