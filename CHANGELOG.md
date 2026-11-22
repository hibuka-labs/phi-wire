# Changelog

All notable changes to the `phi-wire` workspace are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Fixed
- **The client transport tests run on Windows again.** The three transport
  tests named `/bin/sh`, a path Windows does not have, so they failed there
  with `SETUP_REQUIRED` before they could test the transport at all. They
  now spawn the platform's own shell — `cmd /C` on Windows, `/bin/sh -c` on
  Unix — and assert the exit status the way the platform spells it
  ("exit code: 3" on Windows, "exit status: 3" on Unix).
- **The adapter's default shell is held by a test.** The default shell used
  to be `/bin/sh` on every platform; it is now the platform's own (`cmd /C`
  on Windows), and a test pins that so it cannot regress.

## [0.1.0] - 2026-10-31

### Added
- **First release of the phi provider wire** — `phi-wire-protocol`,
  `phi-wire-adapter`, and `phi-wire-client` are the fork of the OpenGCUA
  `mu-protocol` / `mu-adapter` / `mu-client` crates, published under the
  hibuka-labs namespace so the phi family's capability packs can depend on a
  wire that resolves on crates.io.
- **The Playwright contract now lives inside the crate.** Upstream embedded
  `api/contract/playwright-v1.json` through a path that pointed outside the
  crate directory, which does not survive packaging; the fork copies the
  contract to `crates/protocol/contract/` and rewrites the `include_str!`.
