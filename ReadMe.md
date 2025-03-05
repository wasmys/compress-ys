Test Repo For YS + Wasm
=======================

## Synopsis

```
$ ys compress.ys test
PASS
PASS
PASS
$ ys compress.ys https://component-model.bytecodealliance.org/book.js
…compressed javascript code…
```

## Description

We want a YS function that calls Wasm components.

This repo so far mocks up a set of wasm compression calls with CLI calls.

Converted some pseudocode to YS, and added a few things just to show off YS.


## Original Pseudocode

```
!YS-v0
upstream_url =: "https://example.com/something"
upstream_request =: fetch(upstream_url)
upstream_type =: upstream_request.headers.get("content_type")
upstream_body =: upstream_request.body.bytes

minify =: load_component("minifier")
gzip =: load_component("gzip")

# Select a compressor function
body =:
  case upstream_type:
    "css": minify.css(upstream_body)
    "jpeg": gzip.compress(upstream_body)
    else: upstream_body

response:
  status: 200
  body: $body
  # ...
```


## Install `ys` locally

```
$ curl -s https://getys.org/ys | bash
```
