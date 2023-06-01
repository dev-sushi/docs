## Cache

To make sure that we don't have to repeat the same things even if there weren't any changes, lingfo uses cache. Inside cache it saves all things like last executed code or indexed functions.

## One time compile

**warning: this function is still in development**

Tired of waiting for your app to compile when changing what function to call? One time compile (as the name says) compiles the app only one time. Even when you import other function. It works by putting inside temp file some if statements with uuids to check if uuid that was passed in temp file argument match if statement uuid. If yes, it executes the function.

Example:

```cpp
if (argv[0] == "uuid") {example();}
else if (argv[1]) == "uuid") {nextExample();}
```

To use it, just add to configuration for `launch` section `one_compile = yes` and `if_statement = ...`
`if_statement` is template for if statements that will be generated.

Example would look like this:

```cpp
if (argv[$LINGFO_ARG_NUM] == "$LINGFO_UUID") {$LINGFO_CODE()$LINGFO_SEMICOLON} $LINGFO_ELSE_START else if (argv[$LINGFO_ARG_NUM] == "$LINGFO_UUID") {$LINGFO_CODE()$LINGFO_SEMICOLON}
```

- `$LINGFO_ARG_NUM` = what argument number to call (e.g argv[0], argv[1])
- `$LINGFO_UUID` = uuid for functions
- `$LINGFO_CODE` = function that will be executed
- `$LINGFO_SEMICOLON` = ;
- `$LINGFO_ELSE_START` = tells lingfo that here starts else statement and if statement ends
