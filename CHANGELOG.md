# Changelog

All notable changes to the `phi-wire` workspace are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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
