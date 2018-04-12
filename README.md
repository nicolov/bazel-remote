# Bazel remote cache

This project implements a standalone Bazel cache over HTTP to speed up builds. It's based on the
OSS code at github.com/buchgr/bazel-remote.

## Docker usage

```bash
docker build -t bazel-cache .
mkdir /tmp/bazel-cache
docker run -v /tmp/bazel-cache:/data -p 9090:80 bazel-cache -max_size 10
```

`max_size` is expressed in GBytes.

## Monitoring

The cache serves a status page at `/status`.

## Testing with bazel

Update the cache URL in `tools/bazel.rc` in the `cruise/cruise` repo, then `bazel clean` and `bazel build`.
