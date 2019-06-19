# Python Style Guide

Readability is a core goal of Python code. Readable code makes it easier for new users, and makes the project easier to maintain and test.  To help keep your code readable, consider the top 10 tenets of writing Python code in the Van Valen Lab:

1. **KISS (Keep It Simple, Stupid!)**

    Writing simple, small functions makes everyone's life easier.

2. **DRY (Don't Repeat Yourself)**

    Consider functions or classes if you find yourself repeating code.​

3. **Comment your code when necessary!**

    Explain your code, but don’t waste lines with obvious comments.​ Comments can often be unnecessary if a good variable name is used.

4. **Clean Code > Clever Code**

    Clever list comprehensions aren't as good as having a clean and obvious list.

5. **Refactor Early and Often**

    If you find code that is unclear or confusing, refactor it! The libraries are always looking to improve.

6. **Keep your style consistent with the code base**

    Everyone has their own preferred code style, but keeping the style consistent across the entire codebase will keep the project more readable generally.

7. **Limit Line Lengths**

    No one should have to scroll side-to-side to read a line of code. PEP requires 79 characters or less, but the lab's limit is 100.

8. **Only catch known Exceptions**

    Don't blindly catch `Exception`, as there may be strange behavior that gets hidden. Catch only expected errors, like `TypeError`.

9. **Document Code**

    Use docstrings starting with the triple-quote `"""` under each user-defined function and class to explain what the code does, and what the inputs and outputs are.

10. **Lint and Test your code often!**

    Consider writing your tests first (Test Driven Development)​. This helps to reduce future work and prevents broken code from entering the code base.

Please also review the Best of the [Best Practices (BBOP) Guide to Python](https://gist.github.com/sloria/7001839).
