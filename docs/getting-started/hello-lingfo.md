Lingfo is a library that allows you to use functions from any language, in any language (tl;dr it's foreign function interface). The goal is to eliminate wasted time when searching for new libraries when migrating to new language. Currently, it only supports language to Python but it can change in any time.

# Getting Started

## Prerequisites and Installation

To get started with Lingfo, you need to have the following software installed on your system:

- Python 3.9 or newer

To install the Lingfo library, you can use pip:

`pip install lingfo`

## Basic Setup and Configuration

Once you have installed Lingfo, you need to create a configuration file, `lingfo.conf`, in your project directory. This file will define the settings for Lingfo to work with your code.

Here's an example lingfo.conf file for C/C++:

```ini
[main]
lang = h
lib_path = lib/main.h
safe_mode = yes # if set to yes, lingfo will alert about scripts that it will run

[launch]
exec_command = gcc -o lib/out [file-name]
import_syntax = #include "[file-name]"

[temp_file]
temp_file = $LINGFO_IMPORT $LINGFO_NEWLINE int main() {$LINGFO_FUNCTION($LINGFO_ARGS)$LINGFO_SEMICOLON}
extension = c
```

This configuration file defines the language, library path, compilation command, import syntax, temporary file settings, safe mode, and function pattern for your foreign language code.

`[main]`: This section specifies the language of your source code (lang) and the path to the header file containing your foreign language functions (lib_path).

`[launch]`: This section provides the command to compile your code (exec_command) and the syntax for importing the header file in the generated foreign language code (import_syntax).

`[temp_file]`: This section defines a temporary file to be used during the Lingfo processing. The temp_file value should include placeholders for the import statement, function call, and other necessary information used to compile/link your function.

# Usage Guide

## Importing and Using the Library

To use Lingfo in your Python project, you need to import it and run it to generate the Python bindings for your foreign language code. This will automatically find all functions from library and write the functions to a Python file, so it can be executed.
Here's an example Python script (app.py) that demonstrates how to use Lingfo:

```
from lingfopy.main import Lingfo

if __name__ == "__main__":
    Lingfo()

    # lingfo generates code for us to call in Python
    from out.main import itt_add , double_number

    # Run a function with arguments
    double_number(5)
```

## Running

Now let's start our program and execute our foreign language functions.

If everything goes well, you should see this message: `lingfo   saving indexed functions`.
Congratulations 🎉 ! You are ready to use lingfo now. Just import the functions from `out/` folder that lingfo generated and call the function (e.g `from out.main import example`).
