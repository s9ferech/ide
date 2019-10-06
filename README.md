# BaseGL

BaseGL is a blazing fast 2D drawing API. This repository is a work in progress
of BaseGL 2.0. Please refer to BaseGL 1.0 repository for more information:
https://github.com/luna/basegl-old.

# Working with the code

### Toolchain 

In order to use some of the WASM pipeline features we need to use a nightly Rust
channel. The same applies to the code auto-formatter and it's advanced
configuration options used here. You would neither be able to compile not format
the code using the stable branch. 

To setup the toolchain, please use the [the Rust toolchain installer
](https://rustup.rs/):

```bash
rustup toolchain install nightly # Install the nightly channel.
rustup default nightly           # Set it as the default one.
rustup component add rustfmt     # Install the code auto-formatter.
rustup component add clippy      # Install the linter.
```

### Building and testing the project

Please use the `build.sh` script. We need to use a simple custom wrapper here
because of the following Rust toolchain issues: 

- [No direct support for Cargo Workspaces in
wasm-pack.](https://github.com/rustwasm/wasm-pack/issues/642) 
- There is no watch utility in wasm-pack, which makes using it harder than it
should be.

In order to build and test the project, please use the following commands:

```bash
./build.sh

# Wait till the project finishes building.
# Run the following lines from other cmd.

cd examples/01-scene
npm install
npm run start
```

You can now open the following address in your browser: http://localhost:8080.
**Please remember to disable the cache in your browser!**

### Formatting 

All codebase should be auto-formatted using `rustfmt`. It is highly recommended
that you use an IDE which takes care of formatting the code as you type. Please
remember that auto-formatting does not mean you should not care of the way your
code looks and feels! Be sure to carefully read the [Rust style
guide](https://github.com/luna/enso/blob/master/doc/rust-style-guide.md) and
apply it everywhere in your codebase.


### Linting 

Please be sure to fix all errors reported by `cargo clippy` before creating a
pull request to this repository.