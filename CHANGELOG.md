# Changelog

All notable changes to this GitHub action will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

## [0.9.0] - 2024-11-20
### Changed
- Update dependencies to stop using deprecated `upload-artifact` version.

## [0.8.0] - 2024-09-25
### Changed
- Update dependencies, which adds rate-limiting when accessing the GitHub API.

### Fixed
- Allow to write any file from the Docker container. [#22](https://github.com/zaproxy/action-api-scan/issues/22)

## [0.7.0] - 2024-04-02
### Changed
- Update dependencies.

## [0.6.0] - 2024-01-25
### Changed
- Run with node20. [#29](https://github.com/zaproxy/action-api-scan/issues/29)

## [0.5.0] - 2023-08-24
### Added
 - An input (`artifact_name`) used to name the artifact that contains the ZAP reports.

## [0.4.0] - 2023-08-02
### Changed
- The default Docker image was changed to `ghcr.io/zaproxy/zaproxy:stable`.

## [0.3.1] - 2023-07-05
### Fixed
- Check issues with authenticated user. [#19](https://github.com/zaproxy/action-api-scan/issues/19)

## [0.3.0] - 2023-06-29

### Changed
- To use Node 16
- Updated dependencies

## [0.2.0] - 2022-09-09

### Added
- Support for authentication environment variables.

## [0.1.1] - 2022-05-23

### Fixed
- Use default zap user rather than root.

## [0.1.0] - 2021-09-14

First release to Marketplace.

[Unreleased]: https://github.com/zaproxy/action-api-scan/compare/v0.9.0...HEAD
[0.9.0]: https://github.com/zaproxy/action-api-scan/compare/v0.8.0...v0.9.0
[0.8.0]: https://github.com/zaproxy/action-api-scan/compare/v0.7.0...v0.8.0
[0.7.0]: https://github.com/zaproxy/action-api-scan/compare/v0.6.0...v0.7.0
[0.6.0]: https://github.com/zaproxy/action-api-scan/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/zaproxy/action-api-scan/compare/v0.4.0...v0.5.0
[0.4.0]: https://github.com/zaproxy/action-api-scan/compare/v0.3.1...v0.4.0
[0.3.1]: https://github.com/zaproxy/action-api-scan/compare/v0.3.0...v0.3.1
[0.3.0]: https://github.com/zaproxy/action-api-scan/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/zaproxy/action-api-scan/compare/v0.1.1...v0.2.0
[0.1.1]: https://github.com/zaproxy/action-api-scan/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/zaproxy/action-api-scan/compare/12a34c296c603f7505336a7fc750363fa978d93e...v0.1.0
