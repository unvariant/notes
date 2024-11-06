## debugging the standard library
see [https://std-dev-guide.rust-lang.org/development/building-and-debugging.html](https://std-dev-guide.rust-lang.org/development/building-and-debugging.html).
> Since logging and IO APIs are not available in `alloc` and `core` advice meant for the rest of the compiler is not applicable here.
> Instead one can either extract the code that should be tested to a normal crate and add debugging statements there or on POSIX systems one can use the following hack:
```rs
extern "C" {
	fn dprintf(fd: i32, s: *const u8, ...);
}

macro_rules! dbg_printf {
	($s:expr) => {
		unsafe {
			dprintf(2, "%s\0".as_ptr(), $s as *const u8);
		}
	}
}

fn function_to_debug() {
	let dbg_str = format!("debug: {}\n\0", "hello world");
	dbg_printf!(dbg_str.as_bytes().as_ptr());
}
```
- add the `-Zbuild-std` flag to when using `cargo` to recompile the standard library