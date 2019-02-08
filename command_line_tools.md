# Command Line Tools

When writing command line tools, there are a couple of pitfalls to be aware of.
In the past we made certain painful experiences which we would like to prevent
in the future.

### Project Structure

Let's consider an example project for our new command line tool called
`cooltool`. The project structure should look something like this.

```
$ tree cooltool -d
cooltool
└── cmd
    ├── create
    │   └── cluster
    │       ├── defaulting
    │       └── validation
    └── version

6 directories
```

The structure tells us what kind of commands the tool provides.

```
cooltool version
cooltool create cluster
```

Note the folders `defaulting` and `validation`. There isolated code for
defaulting and validation should be located at. Having such code separated makes
isolated tests for specific aspects of the required business logic more obvious.
Isolation, dependency injection and other patterns should guide us here, even in
command line tools.

Each command folder should at least contain the following files.

* `command.go`, the Cobra command setup.
* `error.go`, error types and their matchers.
* `flag.go`, flag initialization and validation.
* `runner.go`, the command execution specific code, without the Cobra command setup.

The full example would look like this.

```
$ tree cooltool
cooltool
├── cmd
│   ├── create
│   │   ├── cluster
│   │   │   ├── defaulting
│   │   │   ├── validation
│   │   │   ├── command.go
│   │   │   ├── error.go
│   │   │   ├── flag.go
│   │   │   └── runner.go
│   │   ├── command.go
│   │   ├── error.go
│   │   ├── flag.go
│   │   └── runner.go
│   └── version
│       ├── command.go
│       ├── error.go
│       ├── flag.go
│       └── runner.go
└── main.go

6 directories, 13 files
```
