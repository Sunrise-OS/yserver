# yserver

A modern X11 server written from scratch in Rust.

Info about the project is in README.md
Current status is in docs/status.md and should be kept up to date
focus is on yserver (KMS) now

## Instructions

- it's fine not to use clippy pedantic in this repo but DO use regular clippy
- before committing, run clippy exactly as CI does: `cargo clippy --all-targets -- -D warnings`. CI fails on any warning, and `--all-targets` lints test code too — a crate-scoped or non-`--all-targets` run misses lints in tests (e.g. needless_range_loop) and they only surface on GH.
- use `cargo fmt` for formatting
- when adding or changing ioctls, watch for libc linuxisms: request-type aliases like `libc::Ioctl` are not portable across all supported targets, and musl/FreeBSD have regressed here before. Keep ioctl request typing/buildability valid on Linux glibc, Linux musl, and FreeBSD.
- design docs (specs) go in docs/superpowers/specs
- impl plans go in docs/superpowers/plans
- Spec compliance is the goal, but if Xorg deviates from spec (unlikely), we need to follow Xorg, clients are tested for 40+ years on Xorg.
