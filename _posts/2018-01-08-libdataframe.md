---
layout: post
title: libdataframe - Portable DataFrames in C and C++
tags: projects
---

# {{ page.title }}

`libdataframe` is an in-progress library for performing in-memory, structured
data analysis: essentially a column-store equivalent to sqlite for use in ad-hoc
data analysis and visualization. We started project after finding no easy
portable equivalent to Pandas or R dataframes.

Basic Goals:
- Easy-to-read structured datasets and analysis from some on-disk format, such
  as CSV.
- Robust and natural timeseries analysis
- Easy to decoding/encoding to other formats (CSV, HDF5, Parquet, Apache Arrow),
  but as separate libraries.
- Fast, performant, well-tested, and well-understood
- Written to C++, but portable to other languages: easy FFI for compiled and
  interpreted languages via C bindings (as a starting point: Python and
  Javascript)
- FFI-based interpreted language bindings should be usable from interactive
  programming environments such as Jupyter notebooks.

Distant, or Explicit Non-Goals:
- Avoiding crazy C++ template metaprogramming and smart expression template
  techniques
- No hipster technologies or languages
- Streaming writes or analysis on streams
- SQL standard, SQL interpreter interface
- Protocol Buffer, Thrift, JSON, etc. ingest interfaces
- Interop with other systems (i.e., Apache Arrow's approach to zero-copy between
  differing Apache big data projects., etc.)

See the rest on [Github](https://github.com/mookerji/libdataframe).
