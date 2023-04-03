**Warning: this page includes things about how to setup configuration which can change [in any time](https://github.com/dev-sushi/sushi/issues/22).**

Sushi is a library that allows you to use functions from any language, in any language (tl;dr it's foreign function interface). The goal is to eliminate wasted time when searching for new libraries when migrating to new language. Currently, it only supports language to Python but it can change in any time.

# Getting Started
## Prerequisites and Installation
To get started with Sushi, you need to have the following software installed on your system:

* Python 3.9 or newer

To install the Sushi library, you can use pip:

`pip install sushipy`


## Basic Setup and Configuration
Once you have installed Sushi, you need to create a configuration file, `sushi.conf`, in your project directory. This file will define the settings for Sushi to work with your code.

Here's an example sushi.conf file for C/C++:

```
[main]
lang = h
lib_path = lib/main.h

[launch]
exec_command = gcc -o lib/out [file-name]
import_syntax = #include "[file-name]"

[temp_file]
temp_file = $SUSHI_IMPORT $SUSHI_NEWLINE int main() {$SUSHI_FUNCTION($SUSHI_ARGS)$SUSHI_SEMICOLON}
extension = c

[index]
function_pattern = ^[^\n()]+\s+(?!if|for)\b\w+\s*\([^()]*\)\s*$
```
This configuration file defines the language, library path, compilation command, import syntax, temporary file settings, and function pattern for your foreign language code.

`[main]`: This section specifies the language of your source code (lang) and the path to the header file containing your foreign language functions (lib_path).

`[launch]`: This section provides the command to compile your code (exec_command) and the syntax for importing the header file in the generated foreign language code (import_syntax).

`[temp_file]`: This section defines a temporary file to be used during the Sushi processing. The temp_file value should include placeholders for the import statement, function call, and other necessary information used to compile/link your function.

`[index]`: Regular expression pattern to match function names.

# Usage Guide
## Importing and Using the Library

To use Sushi in your Python project, you need to import it and run it to generate the Python bindings for your foreign language code. This will automatically find all functions from library and write the functions to a Python file, so it can be executed. 
Here's an example Python script (app.py) that demonstrates how to use Sushi:

```
from sushipy.main import Sushi

if __name__ == "__main__":
    Sushi()

    # sushi generates code for us to call in Python
    from out.main import itt_add , double_number
    
    # Run a function with arguments
    double_number(5)
```

## Running
Now let's start our program and execute our foreign language functions.

If everything goes well, you should see this message: `sushi   saving indexed functions`.
Congratulations 🎉 ! You are ready to use sushi now. Just import the functions  from `out/` folder that sushi generated and call the function (e.g `from out.main import example`).
