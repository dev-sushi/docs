## main

In this section, we can configure the basics of lingfo. This includes what language your library was written in, your library path etc.

Starting with: `lang`, you need to specify in what language your library was written.

!!! note

    If your language is, for example, C++, you should not set it to `.cpp` but to `.hpp`

Next, we have `lib_path`. This is the path for your library.

Lastly, there is `safe_mode`. Its recommended to keep this on, because when it is turned off, Lingfo won't show which scripts it will run (if, for example, extending someones config)

## launch

Launch is another important section in configuration. It provides lingfo with data on how to launch your code. Let's start with `exec_command`:

This specifies what command to run when executing your code.
For this example, we will use C++:

```ini
exec_command = gcc -o lib/out [file-name]
```

-   [file-name] is automatically replaced by lingfo with file path that user wants to execute, for example, if we want to execute file: `foo.hpp` from path: `lib/foo.hpp`, [file-name] will be replaced with this: `lib/foo.hpp`

Now, there is `import_syntax`. As the name says, it's just import template that lingfo will use to import function from other language. For example, once again if we want to use function from `lib/foo.hpp` the import_syntax would be (already replaced by lingfo) this:

```cpp
#include <foo.hpp>
```

## temp_file

Temp file section is used to tell lingfo how to manage temp file that is required to launch. Temp file for lingfo is a way to execute function from e.g C++ to python by compiling file that imported selected function.

So, for example, if you want to execute: `hello()` in C++, the temp file would look like this:

```cpp
#include "lingfo.hpp"

int main() {
    hello()
}
```

After compile the file is automatically deleted. First is: `temp_file`. This sets sturcture for our temp file. Example:

```ini
temp_file = $SUSHI_IMPORT $SUSHI_NEWLINE int main() {$SUSHI_FUNCTION($SUSHI_ARGS)$SUSHI_SEMICOLON}
```

Lets start with `$SUSHI_IMPORT`. This will be replaced with the import for selected library.
`$SUSHI_NEWLINE` is just (as the name says) new line (\n)

`$SUSHI_FUNCTION` is replaced with function to execute.

`$SUSHI_ARGS` is replaced with arguments to use. If none were passed, this will be empty.

`$SUSHI_SEMICOLON` is just a semicolon.

As we saw, there were 2 things that usually shouldnt be here. New line and semicolon. It's because in `.ini` files its new line or comment which isnt parsed by `configparser`.

The last thing is `extension`. Its just what file extension to use when creating temp file. Example: if using `C++`, use `cpp`
