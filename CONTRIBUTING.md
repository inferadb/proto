# Contributing to InferaDB Protocol Buffers

Thank you for your interest in contributing to InferaDB's protocol buffer definitions.

## Before You Start

Proto changes affect multiple downstream repositories:
- **inferadb/engine** - Authorization engine (Rust)
- **inferadb/rust** - Rust SDK client library

Please ensure any changes are backward compatible or coordinate with dependent teams.

## Development Setup

### Prerequisites

- [Buf CLI](https://buf.build/docs/installation) (recommended)
- Or [protoc](https://grpc.io/docs/protoc-installation/) compiler

### Validation

```bash
# Using buf (recommended)
buf lint
buf format --diff
buf breaking --against "https://github.com/inferadb/proto.git#branch=main"

# Using protoc
protoc --proto_path=. inferadb/**/*.proto --descriptor_set_out=/dev/null
```

## Style Guide

### Naming Conventions

- **Packages**: `inferadb.<domain>.v1` (e.g., `inferadb.authorization.v1`)
- **Services**: PascalCase with `Service` suffix (e.g., `AuthorizationService`)
- **RPCs**: PascalCase verbs (e.g., `Evaluate`, `WriteRelationships`)
- **Messages**: PascalCase nouns (e.g., `EvaluateRequest`, `Relationship`)
- **Fields**: snake_case (e.g., `resource_type`, `subject_id`)
- **Enums**: SCREAMING_SNAKE_CASE with type prefix (e.g., `DECISION_ALLOW`)
- **Enum zero value**: Must end with `_UNSPECIFIED`

### Documentation

All public APIs must have comments:

```protobuf
// Evaluate if a subject has permission on a resource.
// Returns a decision with optional trace information.
rpc Evaluate(stream EvaluateRequest) returns (stream EvaluateResponse);

// Subject identifier (e.g., "user:alice", "group:engineers").
string subject = 1;
```

### Versioning

- Use `v1`, `v2`, etc. in package paths for major versions
- Breaking changes require a new major version
- Deprecate fields with `[deprecated = true]` before removal

## Pull Request Process

1. **Create a feature branch** from `main`
2. **Make your changes** following the style guide
3. **Run validation** locally with `buf lint` and `buf format`
4. **Open a PR** - CI will automatically:
   - Lint proto files
   - Check formatting
   - Detect breaking changes
   - Validate compilation
5. **Address review feedback** from `@inferadb/engineers`
6. **Merge** after approval

## Breaking Changes

Breaking changes are detected automatically by CI. If your PR contains breaking changes:

1. Ensure the change is intentional and necessary
2. Update `CHANGELOG.md` with migration guidance
3. Notify dependent repository maintainers
4. Get explicit approval from reviewers

Examples of breaking changes:
- Removing or renaming fields/messages/RPCs
- Changing field numbers
- Changing field types
- Changing RPC signatures

## Questions?

Open an issue or reach out to the engineering team.
