# Sample_CLI : Calculator

## build setup
```shell
> rustup run nightly cargo run
No file specified.
Is verbosity specified?: false

> rustup run nightly cargo run -- input.txt
File specified: input.txt
Is verbosity specified?: false

> rustup run nightly cargo run -- -v input.txt
File specified: input.txt
Is verbosity specified?: true

> rustup run nightly cargo run -- -V
My RPN program 1.0.0

> rustup run nightly cargo run -- -h
My RPN program 1.0.0
Kanta Tamura
Super awesome sample RPN calculator

USAGE:
    sample-cli.exe [FLAGS] [FILE]

ARGS:
    <FILE>    Formulas written in RPN

FLAGS:
    -h, --help       Prints help information
    -v, --verbose    Sets the level of verbosity
    -V, --version    Prints version information
```

## current status
Use Clap to handle command line arguments.

## purpose
An application that calculates formulas in RPN(Reverse-Polish-Notation).

### pattern 1
Reads line by line from standard input and displays the calculated result.
```shell
> cargo run
1 1 +  # 入力
2
1 2 + 3 4 + *  #入力
21
```

### pattern 2
If you specify a file as a command line argument, each line in the file is interpreted as a mathematical formula and the calculation result is output line by line.
```shell
> cat input.txt
1 1 +
1 2 + 3 4 + *

> cargo run input.txt
2
21
```

### pattern 3
When executed with the -v option, the calculation process is also output.
```shell
> cargo run -v
1 1 +  # 入力
["+", "1"][1]
["+"][1,1]
[][2]
2
```
