# Advanced Python Calculator for Software Engineering Graduate Course

## Project Overview

This midterm requires the development of an advanced Python-based calculator application. Designed to underscore the importance of professional software development practices, the application integrates clean, maintainable code, the application of design patterns, comprehensive logging, dynamic configuration via environment variables, sophisticated data handling with Pandas, and a command-line interface (REPL) for real-time user interaction.

## Project Submission

# Setup

## Setup Instructions
1. Clone the repo
2. CD into the project folder
3. Create a virtual environment
4. Activate the virtual environment (VE)
5. Install Requirements

## Test Commands
- `pytest` run all tests
- `pytest --pylint --cov` <- Run Pylint and Coverage (Can be run independently)

# Usage

## Functionality

### Calculator Operations:

You can perform basic arithmetic operations such as addition, subtraction, multiplication, and division. This functionality is enhanced by a plugin architecture and dynamic loading design, which enables the seamless addition of new features to the plugins folder without the need for hardcoding.

Here are the specific commands for each operation:

- **addition**: Performs addition.
- **subtract**: Executes subtraction.
- **multiply**: Handles multiplication.
- **divide**: Performs division.
- **menu**: Displays a list of available commands.
- **exit**: Closes the application.

The menu command dynamically updates to include any new plugins added in the future, ensuring that all available commands are always visible. Feel free to customize placeholders like greet, exit, and goodbye as needed for your application.

### History Management:

The application utilizes robust data management techniques to handle operations effectively.

Commands for managing data include:

- **load**: Retrieves the history of performed operations.
- **clear**: Erases the existing history.
- **delete**: Removes specific indexed data entries.
- **save**: Stores the history of operations.

All operation history is stored in `./data/calculation_history.csv`. The system seamlessly reads from and writes to this CSV file, ensuring efficient data handling and persistence.

### Configuration via Environment Variables:

The application stores its configuration details, including development and testing environment variables, in a .env file.

https://github.com/NikhilInampudi/Calc-Midterm/blob/70db676a76f5b99e72a06fda2f9615fab61f7a9a/app/__init__.py#L30-L37

### REPL Interface:

![REPL pattern](https://github.com/NikhilInampudi/Calc-Midterm/blob/506fba3f08b2811f7a0bbd580a7ffe70b5924130/REPL.png)

This application operates using the Read-Evaluate-Print-Loop (REPL) pattern.

## Design Patterns

### Implementation and Application:

This application incorporates a range of design patterns to optimize its architecture and functionality. Specifically:

- **Facade Pattern**: Streamlines Pandas data manipulation by providing a unified interface.
  
- **Command Pattern**: Forms the foundation of the application's REPL (Read-Evaluate-Print Loop), facilitating modular command execution.

- **Factory Method, Singleton, and Strategy Patterns**: Enhance the application's flexibility and scalability. The Factory Method pattern supports dynamic object creation, Singleton ensures singular instance management, and the Strategy Pattern enables adaptable algorithm selection.

These design patterns collectively bolster the application's structure, fostering maintainability, extensibility, and efficiency across its various components and operations.

1. **Singleton Pattern**:
   The `App` class functions as a singleton, ensuring the existence of only one instance throughout the application. This is enforced through a private constructor and a static initialization method (`__init__`), which manages the class instantiation process.

  https://github.com/NikhilInampudi/Calc-Midterm/blob/506fba3f08b2811f7a0bbd580a7ffe70b5924130/app/__init__.py#L11-L18

2. **Factory Method Pattern**:
 The `CommandHandler` class acts as a factory for generating command objects (`Command` instances). It offers a `register_command` method to enlist various command types and an `execute_command` method to execute these commands based on their assigned names.

  https://github.com/NikhilInampudi/Calc-Midterm/blob/506fba3f08b2811f7a0bbd580a7ffe70b5924130/app/commands/__init__.py#L9-L20

3. **Command Pattern**:
 The `Command` abstract base class defines a standardized way to execute commands through its `execute` method. Concrete command classes, such as `AddCommand`, adhere to this interface by encapsulating specific operations. This approach effectively separates the sender (who invokes the commands) from the receiver (objects that carry out the actions), promoting extensibility and adaptability within the application's design.

   https://github.com/NikhilInampudi/Calc-Midterm/blob/506fba3f08b2811f7a0bbd580a7ffe70b5924130/app/plugins/addition/__init__.py#L8-L10

4. **Iterator Pattern**:
   The `load_plugins` method within the `App` class systematically traverses all modules within the `app.plugins` package using `pkgutil.iter_modules`. This method dynamically loads and initializes plugin classes, exemplifying the iterator pattern. This pattern allows for seamless traversal of a collection (in this case, modules) while maintaining abstraction and preventing direct exposure of underlying details.

   https://github.com/NikhilInampudi/Calc-Midterm/blob/506fba3f08b2811f7a0bbd580a7ffe70b5924130/app/__init__.py#L40-L52

5. **Template Method Pattern**: The `Command` class establishes a blueprint with its abstract method `execute()`, which must be implemented by concrete command classes. This structure ensures a standardized approach to executing commands, enabling customization of specific operations while preserving a uniform interface across diverse command implementations.

6. **Strategy Pattern**: Although not defined as an independent class, the `execute()` method within each concrete command class functions as a strategy for executing specific operations. This approach encapsulates varying strategies within command objects, allowing the application to dynamically choose and execute different strategies as needed during runtime.

### Try/Catch/Except
Implemented exception handling to demonstrate both "Look Before You Leap" (LBYL) and "Easier to Ask for Forgiveness than Permission" (EAFP) approaches.

   https://github.com/NikhilInampudi/Calc-Midterm/blob/506fba3f08b2811f7a0bbd580a7ffe70b5924130/app/plugins/multiply/__init__.py#L8-L19

  ## Testing and Code Quality

### Comprehensive Tests Using pytest:

The test cases reside in the `tests` folder and primarily employ unit testing alongside assertions to validate various scenarios. These tests significantly enhance the application's robustness by covering a wide range of possible outcomes.

- `pytest` run all tests
- `pytest --pylint --cov` <- Run Pylint and Coverage (Can be run independently)

Test Coverage = 96%
![Test Coverage](https://github.com/NikhilInampudi/Calc-Midterm/blob/60c3b0a8474f7b9cf3cf42c377e0d9bf69a70837/Coverage%20Test.png)


## Version Control, Documentation, and Logging

GitHub Actions automates the execution of all tests upon code pushes or merges.

### Commit History:

This repository maintains a clear and informative commit history, ensuring it serves as a valuable reference.

### Logging Practices:

The application implements dynamic logging configuration using environment variables. It features a sophisticated logging system that captures critical steps during operations, including detailed application activities, data manipulations, errors, and informative messages. This logging setup ensures robust error handling and exception management without disrupting application functionality. Overall, logging is extensively utilized throughout the application instead of relying on print statements.

- `logging.info`: Records events and details about the execution flow at specific points in the code.
- `logging.error`: Captures and logs error messages and exceptions encountered during code execution.

https://github.com/NikhilInampudi/Calc-Midterm/blob/60c3b0a8474f7b9cf3cf42c377e0d9bf69a70837/app/plugins/multiply/__init__.py#L8-L19

![Logging](https://github.com/NikhilInampudi/Calc-Midterm/blob/4b1fb3d36acc8166d4c6b24ad3af8a0767756201/Logging%20Info%20.png)

