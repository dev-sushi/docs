**Warning: this page includes things about how to setup configuration which can change [in any time](https://github.com/dev-sushi/sushi/issues/22).**

Sushi is a library that allows you to use functions from any language, in any language (tl;dr it's foreign function interface). The goal is to eliminate wasted time when searching for new libraries when migrating to new language. Currently, it only supports language to python but it can change in any time.

To get started, be sure that you have the following things installed:

- `sushipy` from PyPi
- `python3.9` or newer.

Inside your project import sushi and call `Sushi` class from `sushipy.main`. This will automatically find all functions from library and put it in python file, so it can be executed. But wait! We are not ready yet. Because sushi supports any language, we will need to create configuration.
It will have things like regex for parsing (this might change in future due to usage some other methods like last) and library path. So let's create new file named: `sushi.conf` inside root folder.

The configuration is pretty straight forward, so there isn't much to explain here. Here's example configuration for C++:
```ini
[main]
lang = hpp
lib_path = lib/main.hpp # can also be lib/*

[launch]
exec_command = g++ -o lib/out [file-name]
import_syntax = #include "[file-name]"

# [file-name] file name that will be imported (for example main.hpp)

verbose = no

[temp_file]
temp_file = $SUSHI_IMPORT $SUSHI_NEWLINE int main() {$SUSHI_FUNCTION()$SUSHI_SEMICOLON}

# SUSHI_IMPORT = import_syntax
# SUSHI_NEWLINE = \n
# SUSHI_FUNCTION = function that will be called
# SUSHI_SEMICOLON = ;

extension = cpp

[index]
function_pattern = ^[\w-]+\s[\w-]+\(([\s\S])*\)$
```

Now let's start our program. If everything goes well, you should see this message: `sushi   saving indexed functions`.
Congratulations 🎉 ! You are ready to use sushi now. Just import function from out folder that sushi generated and call it (e.g `from out.main import example`).