# Sample_CLI : Calculator

## build setup
```shell
> cargo run
["target\debug\sample-cli.exe"]

> cargo run -- 1 a xyz 2.0
["target\debug\sample-cli.exe", "1", "a", "xyz", "2.0"]
```

## current status
Store command line arguments in vec and output.

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
