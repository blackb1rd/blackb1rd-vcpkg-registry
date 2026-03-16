# blackb1rd-vcpkg-registry

A custom vcpkg registry containing ports not available in the official vcpkg curated registry.

## Ports

| Port | Version | Description |
|------|---------|-------------|
| `neoactivemq-cpp` | 1.1.9 | Modern fork of Apache ActiveMQ-CPP with CMake support and OpenSSL integration |

## Usage

### 1. Configure `vcpkg-configuration.json`

Add this registry to your project's `vcpkg-configuration.json`:

```json
{
  "registries": [
    {
      "kind": "git",
      "repository": "https://github.com/blackb1rd/blackb1rd-vcpkg-registry",
      "baseline": "<commit-sha>",
      "packages": [
        "neoactivemq-cpp"
      ]
    }
  ]
}
```

> Replace `<commit-sha>` with the latest commit SHA from this repository.

### 2. Add the dependency in `vcpkg.json`

```json
{
  "dependencies": [
    "neoactivemq-cpp"
  ]
}
```

To enable SSL support:

```json
{
  "dependencies": [
    {
      "name": "neoactivemq-cpp",
      "features": ["ssl"]
    }
  ]
}
```

### 3. Install

```sh
vcpkg install
```

Or install directly:

```sh
vcpkg install neoactivemq-cpp
```

### 4. Use in CMake

```cmake
find_package(neoactivemq-cpp CONFIG REQUIRED)
target_link_libraries(main PRIVATE neoactivemq-cpp::neoactivemq-cpp)
```

## Platform Support

- Linux: supported
- Windows: supported
- macOS: supported
- UWP: not supported (`!uwp`)
