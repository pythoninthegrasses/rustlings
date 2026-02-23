# AGENTS.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Local fork of the official [rustlings](https://github.com/rust-lang/rustlings) exercises for learning Rust. The repo contains 100+ exercises across 24 categories (variables, ownership, traits, lifetimes, etc.) with corresponding solutions. Each exercise is a standalone binary target defined in `Cargo.toml`.

There is no `src/` directory — all code lives in `exercises/` and `solutions/` as individual `.rs` files.

## Build & Development Commands

All commands use [Task](https://taskfile.dev/) as the task runner:

```bash
task install          # Install all deps (mise, rustup, sccache, rustlings, cargo-nextest)
task test             # Run tests via cargo nextest (falls back to cargo test)
task lint             # Run cargo clippy --workspace
task format           # Run cargo fmt --all
task pre-commit       # Run pre-commit hooks via prek
task build:timings    # Analyze build performance
```

Run the interactive exercise runner:
```bash
rustlings
```

Run a single exercise directly:
```bash
run exercises/01_variables/variables1.rs
```

Run tests for a specific exercise:
```bash
cargo nextest run --bin variables1
```

## Toolchain & Environment

- **Runtime management**: `mise` (see `.tool-versions` for pinned versions)
- **Rust toolchain**: nightly (pinned in `.tool-versions`)
- **Rust edition**: 2024
- **Compilation cache**: sccache (`RUSTC_WRAPPER=sccache`)
- **Test runner**: cargo-nextest (installed via cargo-binstall)
- **Pre-commit**: prek
- **Env precedence**: `TASK_X_ENV_PRECEDENCE=1` in `.env` makes Taskfile env override OS env (required for PATH manipulation)

## Build Environment

The global `env:` block in `taskfile.yml` sets:

- `CARGO_HOME` and `CARGO_TARGET_DIR` to `.cache/cargo` and `target` under the project root
- `PATH` prepends mise shims, `~/.local/bin`, and cargo bin dir (strips IDE globalStorage paths)
- `RUSTFLAGS` enables multi-threaded compilation (`-Zthreads=N`)
- `CARGO_BUILD_JOBS` reserves 2 cores for system (min 1 job)

## Cargo Lints

Defined in `Cargo.toml`:

- `unsafe_code = "forbid"` — no unsafe allowed
- `unstable_features = "forbid"` — no nightly-only features in exercises
- `dead_code = "allow"` — exercises often have unused code
- `todo = "forbid"` (clippy) — no unfinished TODOs
- `empty_loop = "forbid"` / `infinite_loop = "deny"` (clippy)

## Exercise Structure

Each exercise follows this pattern:

```rust
// Exercise code with TODO markers or deliberate errors for the learner to fix

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_name() {
        assert!(condition);
    }
}
```

Exercises live in `exercises/<NN_topic>/` and solutions mirror at `solutions/<NN_topic>/`. Both are registered as `[[bin]]` targets in `Cargo.toml`.

## Context7

Always use Context7 MCP when I need library/API documentation, code generation, setup or configuration steps without me having to explicitly ask.

### Libraries

- jdx/mise
- nextest-rs/nextest
- websites/taskfile_dev
