# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project generally follows [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added
- Added a `CHANGELOG.md` to track SPA-specific changes in this fork.
- Added bench-mode UI behavior after login:
  - The full controls screen now renders even when live spa panel data is unavailable.
  - A read-only banner is shown to explain that RS485 panel data is not yet available.

### Changed
- Updated login/display gating logic so post-login state is based on auth token, not panel-data availability.
- Added a read-only visual mode when live panel data is missing:
  - Controls are dimmed and interaction is disabled.
  - Bench-mode explanatory text is selectable/copyable.
- Reduced noisy retry impact when spa data is unavailable by increasing panel-data poll retry from 1s to 10s for the specific `no_spa_data_yet` condition.
- Improved client handling of API not-ready responses:
  - Treats `<error>no_spa_data_yet</error>` as a known non-fatal state instead of generic hard error logging.
- Fork policy cleanup: `dist/` is no longer tracked as source-of-truth content and is ignored as generated build output.
- Simplified fork README policy guidance by removing the extra "deploy-ready" terminology section.

### Notes
- During this work, generated build artifacts in `dist/` changed as expected after rebuilding with Vite/PWA.
- Firmware-side companion changes were made in the parent `esp32_balboa_spa` repository to return explicit not-ready API responses and improve POST body handling for chunked requests.
