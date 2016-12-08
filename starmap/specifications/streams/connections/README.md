---
layout: page
permalink: /starmap/specifications/streams/connections/
title: Connecting streams with external systems
status:
  date: December 6, 2016
  is: Draft
knowledgelevel: L2
library: streams
depends_on:
  - /starmap/specifications/streams/MotionObservable
---

# Connecting streams with external systems

This is the engineering specification for connecting motion streams with external systems.

## Overview

There are two primary flows of data we care about:

- **Read**: values that are read into a Material Motion stream.
- **Write**: values that are written from a Material Motion stream.

## Connection types

There are three primary ways to read or write a value: **Properties** and **Inline** functions.

| Option Number | Name              | Readable connections             | Writeable connections                  |
|:--------------|:------------------|:---------------------------------|:---------------------------------------|
| 1.            | Scoped Property   | `propertyOf(view).positionX`     | `propertyOf(view).positionX`           |
| 2.            | Unscoped Property | `source: view, property: View.X` | `target: view, property: View.X`       |
| 3.            | Inline            | `{ return view.position.x }`     | `{ value in view.position.x = value }` |

The above connection types are guidelines around the shape of connections. A given platform must
provide at least one mechanism.

A **Scoped Property** is a property instance that writes to a *specific* target.

An **Unscoped Property** is a property instance that can write to *any* target.

## Example usage

| Option Number | Name              | [$.write](/starmap/specifications/streams/operators/$.write) |
|:--------------|:------------------|:------------------------------------------------|
| 1.            | Scoped Property   | `$.write(to: propertyOf(view).positionX)`       |
| 2.            | Unscoped Property | `$.write(to: view, property: View.X)`           |
| 3.            | Inline            | `$.write({ value in view.position.x = value })` |