# Debugging

If you encounter any issues while using Lingfo, you can enable verbose mode to output extra debugging messages, which can be helpful in identifying and resolving problems.

To enable verbose mode, update your `lingfo.conf` configuration file by changing the verbose option inside the `[launch]` section to "yes" and restart your application. With verbose mode enabled, Lingfo will display detailed information about its internal processes, such as function parsing.

Example:

```ini
[launch]
exec_command = gcc -o lib/out [file-name]
import_syntax = #include "[file-name]"
verbose = yes
```

In addition to using verbose mode, it's recommended to check the [issues](https://github.com/lingfo/lingfo/issues) for any existing solutions to your problem. If you don't find an issue related to your bug, feel free to create a new issue and provide as much information as possible to help diagnose and fix the problem.
