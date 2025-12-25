# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2024-12-24

### Added

- Initial release of InferaDB protobuf definitions
- Core authorization service (`AuthorizationService`)
  - `Check` - Single permission check
  - `CheckBatch` - Batch permission checks
  - `Lookup` - Find resources/subjects by relation
  - `Expand` - Expand permission tree
  - `Watch` - Real-time relationship updates
- Relationship management
  - `WriteRelationships` - Create/update relationships
  - `DeleteRelationships` - Remove relationships
- Schema management (`SchemaService`)
  - `WriteSchema` - Deploy authorization schema
  - `ReadSchema` - Retrieve current schema
