# Changelog

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.0.0] - 2026-08-27

### Added

- Added TLS1.2 enforcement for enhanced security
- Added $commands array to import only required Exchange cmdlets, reducing memory footprint
- Added detailed property selection arrays for optimized data retrieval

### Changed

- Refactored entire codebase following PowerShell best practices with consistent splatting
- Enhanced error handling with detailed try-catch-finally blocks and $PSItem usage
- Improved audit logging with consistent structured format across all operations
- Improved mailbox filter to include multiple search fields (Name, SamAccountName, Alias, PrimarySmtpAddress)

### Fixed

- Corrected session cleanup in finally blocks with proper error handling
- Improved error message formatting with line numbers and detailed context

## [1.0.0] - 2023-08-17

Initial release of HelloID-Conn-SA-Full-Exchange-On-Premises-Usermailbox-ActiveSync-Devices-Delete.

### Added

- Initial release for deleting Exchange On-Premises ActiveSync devices
