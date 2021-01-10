## err_panic.rs

A program that panics if the specified file does not exist.

```shell
> echo 42 > number.txt  # write numbers to a text file

> cat number.txt
42

> rustup run nightly cargo run --bin err_panic
84

> rm number.txt  # delete text file

> rustup run nightly cargo run --bin err_panic
thread 'main' panicked at 'failed to open the file.: Os { code: 2, kind: NotFound, message: "指定されたファイルが見つかりません。" }', src\bin\err_panic.rs:4:49
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
error: process did not exit successfully: `target\debug\err_panic.exe` (exit code: 101)

> echo hoge > number.txt  # write non numeric values to a text file

> rustup run nightly cargo run --bin err_panic
thread 'main' panicked at 'failed to parse string to a number.: ParseIntError { kind: InvalidDigit }', src\bin\err_panic.rs:8:10
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
error: process did not exit successfully: `target\debug\err_panic.exe` (exit code: 101)
```

## err_no_crate.rs

added error handling to err_panic.rs

```shell
> echo 42 > number.txt  # write numbers to a text file

> cat number.txt
42

> rustup run nightly cargo run --bin err_panic
84

> rm number.txt  # delete text file

> rustup run nightly cargo run --bin err_panic
I/O Error: 指定されたファイルが見つかりません。 (os error 2)

> echo hoge > number.txt  # write non numeric values to a text file

> rustup run nightly cargo run --bin err_panic
Parse Error: invalid digit found in string
```

## err_anyhow.rs

error handling with anyhow

```shell
> echo 42 > number.txt  # write numbers to a text file

> cat number.txt
42

> rustup run nightly cargo run --bin err_anyhow
84

> rm number.txt  # delete text file

> rustup run nightly cargo run --bin err_anyhow
Error {
    context: "failed to read string from number.txt",
    source: Os {
        code: 2,
        kind: NotFound,
        message: "指定されたファイルが見つかりません。",
    },
}

> echo hoge > number.txt  # write non numeric values to a text file

> rustup run nightly cargo run --bin err_anyhow
Error {
    context: "failed to parse string",
    source: ParseIntError {
        kind: InvalidDigit,
    },
}
```
