To create a lingfo project, follow the [install guide](../getting-started). This is required.

## Basic steps

Installing lingfo into your project is easy, you will just need to know some basics about your language to configure it (or you could find a pre-made configuration on GitHub).

Configuration won't be covered, because it's already [here](../configuration/basic). We will cover only how to use lingfo in the real world. Configuration file name: `lingfo.conf`.

After configuring, we can move to launching lingfo for the first time. Be sure that folder `out/` (as output) is empty. If not, this folder will be automatically cleared.

Somewhere in your Python file (recommended is the main file) import class Lingfo from the main package. Import should look like this: `from lingfo.main import Lingfo`. Lingfo class is the main class of lingfo. It won't trigger any function execution, rather just index and save functions.

We will now need to run this, to make sure our output file (out/) is ready to use. Inside the output file, there all functions from another language be saved, so we can execute them. After running it, if everything goes well you should see files inside that output folder, which was mentioned later.

## Running functions

Let's now import our generated functions as a normal Python library. For example, if you want to import: `lib/main.hpp` just use `out/main.hpp` etc.
You can now use all functions that were originally in your library, as Python functions. This guide will follow [cpp example](https://github.com/lingfo/lingfo/blob/main/examples/cpp/app.py) so we have only one function to use. Let's try it!

Function name is `helloWorld()` inside `lib/main.hpp`, so the import will be `import out.main`.

!!! Warning

    Remember to always call your functions after Lingfo class is executed, so there won't be any conflicts.

Inside the Python file, we just need to simply call, and run it. Output of this function will be now shown on the terminal.
Congratulations! You now learned how to call simple functions, but what about classes?

## Classes

Calling classes is the same process as calling functions. You just need to import this class and call functions from it.

## Multiple execute

If we are using multiple functions or classes from library, it's important to use lingfo built-in support for it. Otherwise all progress will be lost on every function/class launch. To use multiple functions, import `MultipleExecute` from `execute` like so: `from lingfo.execute import MultipleExecute`. This is using Python built in with a statement, so using it looks like this: `with MultipleExecute():`, and inside that just call all your functions you need to execute.

Before launching, be sure that you toggled `multiple_execute` to true in `lingfo.conf`. Thats it!

## Variables

<!--TODO-->
