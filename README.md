# TinyGo Plugin

[![ci](https://github.com/fluentci-io/tinygo-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/tinygo-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [tinygo](https://tinygo.org/).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm tinygo setup
```

## Functions

| Name   | Description                                |
| ------ | ------------------------------------------ |
| setup  | Installs a specific version of tinygo.      |
| build  | Compile packages and dependencies  |
| run    | Compile and run immediately |
| test   | Test packages |
| clean  | empty cache directory ($HOME/.cache/tinygo) |


## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.1.9"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/tinygo@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: tinygo
    args: |
      setup
- name: Show tinygo version
  run: |
    type tinygo
    tinygo version
```
