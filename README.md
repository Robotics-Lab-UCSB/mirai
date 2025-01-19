# mirai

This is the websockets backend for the virtual robotics lab, built on Tokio's
`axum`. The source code is licensed under a permissive Berkeley-style license.
At this time we do not admit GPL code into the dependencies.

## Hacking

### Using Nix

The easiest way to hack on the project is using Nix to manage all dependencies.
You can install it on macOS and Linux by running

```sh
curl --proto '=https' --tlsv1.2 -sSf -L https://install.determinate.systems/nix | \
  sh -s -- install
```

On Windows, either use WSL, or use the non-Nix instructions below.

With Nix installed and `flakes` enabled, run

```sh
nix build
```

to compile the code project. A binary will be in `result/bin`.

To directly build and run the project, execute:

```sh
nix run
```

Run all tests and checks using:

```sh
nix flake check
```

Format all files using:

```sh
nix fmt
```

Spin up a development environment that provides the full development toolchain
including `rustc`, `cargo`, `rust-analyzer`, `rustfmt`, and more using:

```sh
nix develop
```

Once you are in the development shell, feel free to invoke the commands
detailed below in the non-Nix instructions directly, which should provide a
faster development experience.

### Generic non-Nix instructions

If you don't have or don't want to install Nix, you need to manually install a
Rust toolchain and bring your own tooling.

It's recommended you use [rustup](https://rustup.rs/), but you can obtain Rust
through your distribution's package manager as well. We currently use `rustc`
and `cargo` stable version `1.83.0`.

Then you can run all the `cargo` commands as usual:

Run the project in development mode:

```sh
cargo run
```

Build an optimized release binary:

```sh
cargo build --release
```

Audit dependencies for security advisories:

```sh
cargo audit
```

Format all Rust code:

```sh
cargo fmt
```

Lint code:

```sh
cargo clippy
```

