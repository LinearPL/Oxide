## oxide-SQLite

This companion crate implements a oxide vector store based on SQLite. 

## Usage

Add the companion crate to your `Cargo.toml`, along with the oxide-core crate:

```toml
[dependencies]
oxide-sqlite = "0.1.3"
oxide-core = "0.4.0"
```

You can also run `cargo add oxide-sqlite oxide-core` to add the most recent versions of the dependencies to your project.

See the [`/examples`](./examples) folder for usage examples.

## Important Note

Before using the SQLite vector store, you must [initialize the SQLite vector extension](https://alexgoxideia.xyz/sqlite-vec/rust.html). Add this code before creating your connection:

```rust
use rusqlite::ffi::sqlite3_auto_extension;
use sqlite_vec::sqlite3_vec_init;

unsafe {
    sqlite3_auto_extension(Some(std::mem::transmute(sqlite3_vec_init as *const ())));
}
```
