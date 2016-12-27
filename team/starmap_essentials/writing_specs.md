---
layout: page
---

# Writing specs

Engineering specifications are the means by which we discuss and ratify what we'd like to build
across all of our supported platforms. All specs have a consistent shape and are expected to evolve
over time.

## General guidelines

The goal of a spec is to provide a checklist for an engineer to validate their implementation
against.

If you are writing a spec you ideally already have a working implementation in your langauge of
choice. Do not paste this implementation into the spec verbatim. Your role as spec writer is to
break the implementation apart into a checklist. Another engineer - potentially thinking in a
language different from your own - can then follow this checklist.

Avoid use of language-specific features where possible. If a language-specific feature is necessary,
explain why.

Specs do not need to be 100% byte-for-byte accurate. The goal is to communicate the intent and shape
of the topic, not its literal implementation.

## Shape of a spec

Presented below is the outline of an engineering specification. We discuss each section in more
detail further below.

```yaml
---
key: value
key: value
...
---

# <topic> specification

This is the engineering specification for the `<topic>` API.

## Overview

A high-level overview of the topic. Discuss new concepts where relevant.

## Examples

An optional set of examples showing use of the topic.

## MVP

### Specific thing to build

And how to build it.
```

## YAML preamble

All specs start with a yaml preamble. This preamble includes relevant metadata.

### Layout

```yaml
layout: page
```

### Status

Indicates the current status of the page.

Date must be long-form `Month day, year` format.

Status can be any of `Draft`, `Experimental`, or `Stable`.

```yaml
status:
  date: December 13, 2016
  is: Draft
```

### Knowledge level

Defines the expected end-user knowledge level for this topic.

There are four knowledge levels: L1-L4.

```yaml
knowledgelevel: L2
```

### Library

The library this API should live within.

All library names are lower-cased and hyphenated.

```yaml
library: streams
```
### Dependencies

A list of absolute paths to other starmap files.

A dependency is a spec that must be built before this spec can be built.

```yaml
depends_on:
  - /starmap/specifications/primitives/gesture_recognizers/GestureRecognizer
  - /starmap/specifications/streams/operators/foundation/$._map
```

### Stream type

Operators should define their expected input and output types.

```yaml
streamtype:
  in: GestureRecognizer
  out: Point
```

### Availability

Link to the platform's source and tests, when available.

We use the following platform names: `Android`, `iOS`, and `JavaScript`.

```yaml
availability:
  - platform:
    name: <platform name>
    url: <source url>
    tests_url: <tests url>
  - platform:
    name: <platform name>
    url: <source url>
    tests_url: <tests url>
```