<div align="center">
    <p><a href="https://inferadb.com"><img src=".github/inferadb.png" width="100" /></a></p>
    <h1>InferaDB Protocol Buffers</h1>
    <p>gRPC protocol buffer definitions for InferaDB APIs.</p>
</div>

<br />

## Structure

```
inferadb/
├── authorization/
│   └── v1/
│       └── authorization.proto    # Permission checks, relationships, lookups
└── management/
    └── v1/
        └── (coming soon)          # Organizations, vaults, schemas, teams
```

## Package Naming

Packages follow the pattern `inferadb.<domain>.v1`:

- `inferadb.authorization.v1` - Authorization service (checks, relationships, watch)
- `inferadb.management.v1` - Management service (orgs, vaults, schemas, teams)

## Usage

### Buf

```bash
buf generate
```

### protoc

```bash
protoc --proto_path=. \
  --go_out=. --go_opt=paths=source_relative \
  --go-grpc_out=. --go-grpc_opt=paths=source_relative \
  inferadb/authorization/v1/authorization.proto
```
