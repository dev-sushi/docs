# Debugging

If you encounter any issues while using Sushi, you can enable verbose mode to output extra debugging messages, which can be helpful in identifying and resolving problems.

To enable verbose mode, update your `sushi.conf` configuration file by changing the verbose option inside the `[launch]` section to "yes" and restart your application. With verbose mode enabled, Sushi will display detailed information about its internal processes, such as function parsing.

Example of updated `sushi.conf` with verbose mode enabled:

```ini
[main]
lang = h
lib_path = lib/main.h

[launch]
exec_command = gcc -o lib/out [file-name]
import_syntax = #include "[file-name]"
verbose = yes

[temp_file]
temp_file = $SUSHI_IMPORT $SUSHI_NEWLINE int main() {$SUSHI_FUNCTION($SUSHI_ARGS)$SUSHI_SEMICOLON}
extension = c

[index]
function_pattern = ^[^\n()]+\s+(?!if|for)\b\w+\s*\([^()]*\)\s*$
```

In addition to using verbose mode, it's recommended to check the [issues](https://github.com/dev-sushi/sushi/issues) for any existing solutions to your problem. If you don't find an issue related to your bug, feel free to create a new issue and provide as much information as possible to help diagnose and fix the problem.
