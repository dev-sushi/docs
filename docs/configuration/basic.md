## [main]

In this section, we can configure the basics of sushi. This includes what language your library was written in, your library path etc.

Starting with: `lang`, you need to specify in what language your library was written.

??? warning "warning"

    If your language is, for example, C++, you should not set it to `.cpp` but to `.hpp`

Next, we have `lib_path`. This is the path for your library.

Lastly, there is `safe_mode`. Its recommended to keep this on, because when it is turned off, Sushi won't show which scripts it will run (if, for example, extending someones config)

## [launch]

Launch is another important section in configuration. It provides sushi with data on how to launch your code. Let's start with `exec_command`:

This specifies what command to run when executing your code.
For this example, we will use C++:

```ini
exec_command = gcc -o lib/out [file-name]
```

-   [file-name] is automatically replaced by sushi with file path that user wants to execute, for example, if we want to execute file: `foo.hpp` from path: `lib/foo.hpp`, [file-name] will be replaced with this: `lib/foo.hpp`

Now, there is `import_syntax`. As the name says, it's just import template that sushi will use to import function from other language. For example, once again if we want to use function from `lib/foo.hpp` the import_syntax would be (already replaced by sushi) this:

```cpp
#include <foo.hpp>
```

## [temp_file]

temp_file

## [index]

index
