## Basics of sushi

Sushi compiles or interprets the code to create a runnable file which then can be executed, displaying the output in the terminal. Removing the translation step allows for code to run at its native language speed.

## Deep look into sushi

Sushi at its core, is just a simple python app. Modules like cache or [one-time-compile](../what-is-oc) are the things that make sushi more interesting. But, what is hidden inside that "simple python app"? Few things. Let's start with the main one, which is file indexing:

### file indexing

Sushi for file indexing uses [tree-sitter](https://tree-sitter.github.io/tree-sitter/), which allows to detect functions without using regex (as used before). There's not much to explain here, but here are some basics of how it works:

First, it parses the code with tree-sitter to convert it to a tree. This tree then can be used with sushi to get all functions from the file. After that, it grabs from these functions file name and arguments and saves it to (currently) python output file.

### output file

Output file is another important thing that is required to make sushi work. Here are all functions that sushi indexed in one file. But why do we need it? The answer is simple: we need it to execute functions. When designing sushi, we considered 2 ways on how to execute functions:

-   providing function name to Execute() function
-   automatically finding file name and executing it.

To ensure best developer experience, we choose the second option. Using that, we were able to make sure that this will be easy to use when using arguments or not, when running multiple functions etc.
