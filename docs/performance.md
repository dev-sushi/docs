## Cache

To make sure that we don't have to repeat the same things even if there weren't any changes, sushi uses cache. Inside cache it saves all things like last executed code or indexed functions.

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
if (argv[$SUSHI_ARG_NUM] == "$SUSHI_UUID") {$SUSHI_CODE()$SUSHI_SEMICOLON} $SUSHI_ELSE_START else if (argv[$SUSHI_ARG_NUM] == "$SUSHI_UUID") {$SUSHI_CODE()$SUSHI_SEMICOLON}
```

-   `$SUSHI_ARG_NUM` = what argument number to call (e.g argv[0], argv[1])
-   `$SUSHI_UUID` = uuid for functions
-   `$SUSHI_CODE` = function that will be executed
-   `$SUSHI_SEMICOLON` = ;
-   `$SUSHI_ELSE_START` = tells sushi that here starts else statement and if statement ends
