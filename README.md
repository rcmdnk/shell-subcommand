# shell-subcommand
Template for shell command with subcommand.

Subcommand can be defined by alias, function, or executable in PATH,
like Git command.

## Installation

Put **bin/shell-subcommand** file where as you like.

## Getting started

Prepare main script, e.g. `mycmd`.

The minimum script is:

```mycmd
#!/usr/bin/env bash
source /path/to/shell-subcommand
```

Then, you can call any of alias, function or executable in the PATH
which have a name starting with `mycmd-`.

e.g., if you have an function named `mycmd-func`,
you can call `mycmd func`

## Use alias/function in your environment

alias/function are not passed to the script.

If they are defined in **.bashrc**, just call them before `shell-subcommand`.

```mycmd
#!/usr/bin/env bash
source ~/.bashrc
source /path/to/shell-subcommand
```

Of course, you can defined them in the script, too:

```mycmd
#!/usr/bin/env bash
alias mycmd-hello="echo Hello world!"
mycmd-hello-func () {
  echo "Hello, this is function!"
}
source /path/to/shell-subcommand
```

Check help:

    $ mycmd help
    usage: mycmd <sub-commands> [options]

    sub commands: hello hello-func help

Now you can call

    $ mycmd hello
    $ mycmd hello-func

## Help description

You can give a short description for the help:

    SHORT_DESCRIPTION="My command with various sub commands!"

Then, it shows

    $ mycmd
    mycmd: My command with various sub commands!

    usage: mycmd <sub-commands> [options]

    sub commands: hello hello-func help

If you want to add more help, you can change `usage...` sentences by `HELP_MAIN`, like

    HELP_MAIN="usage: $(basename "$0") <sub-commands> [options]

    sub-commands are made from alias, function, and executables in PATH.
"

Now it shows:

    $ ./mycmd
    mycmd: My command with various sub commands!

    usage: mycmd <sub-commands> [options]

    sub-commands are made from alias, function, and executables in PATH.


    sub commands: hello hello-func help


## Example

Check example: [mycmd](https://github.com/rcmdnk/shell-subcommand/blob/master/example/mycmd).
