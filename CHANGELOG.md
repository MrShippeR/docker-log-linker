# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog
and this project adheres to Semantic Versioning.

---

## [1.3] - 2026-01-05
### Modified
 - fix logging, path to main logfile is now defined in program
 - edited CHOWN to be just for directories
 - fix if no containers is running

---

## [1.2] - 2025-12-23

### Added
 - fixing SEPARATELY_DEFINED mode
 - rewriting code to be in fuctions

---

## [1.1] - 2025-12-15

### Added
 - more logging messages
 - fixing owner of log directories, moving all mkdir to one section
 - in test mode logging is just to console
 - fixind when paths ends with slash in configuration file
 - customizing install guide and adding Uninstall commands in README.md

---

## [1.0] - 2025-12-14

### Added
- Initial release
- Systemd service to create symlinks to Docker container log files
- Support for linking logs from selected containers
- Support for central log directory mode
- Support for per-container log directory mode
- Configurable startup delay after Docker daemon start
