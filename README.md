# Library App

## Description

Library App is a modular C# solution for managing a library system. It supports core library operations such as managing books, authors, patrons, and loans. The project is organized into separate layers for application logic, infrastructure, and a console interface, following best practices for maintainability and testability.

## Project Structure

- AccelerateDevGitHubCopilot.sln
- README.md
- src/
  - Library.ApplicationCore/
    - Library.ApplicationCore.csproj
    - Entities/
    - Enums/
    - Interfaces/
    - Services/
  - Library.Console/
    - Library.Console.csproj
    - appSettings.json
    - CommonActions.cs
    - ConsoleApp.cs
    - ConsoleState.cs
    - Program.cs
    - Json/
      - Authors.json
      - BookItems.json
      - Books.json
      - Loans.json
      - Patrons.json
  - Library.Infrastructure/
    - Library.Infrastructure.csproj
    - Data/
- tests/
  - UnitTests/
    - LoanFactory.cs

## Key Classes and Interfaces

### Key Classes and Interfaces

- **Entities** (`src/Library.ApplicationCore/Entities/`)
    - **Book**: Represents a book in the library, including title, author, ISBN, and availability.
    - **Author**: Stores author details such as name and biography.
    - **Patron**: Represents a library user, tracking their personal info and current loans.
    - **Loan**: Tracks the borrowing and return of books, linking books and patrons with due dates.
    - *Impact*: These classes define the core data structures used throughout the application, ensuring consistency and clarity in how library data is represented.

- **Enums** (`src/Library.ApplicationCore/Enums/`)
    - **BookStatus**: Indicates if a book is available, checked out, or reserved.
    - **LoanStatus**: Tracks the state of a loan (active, overdue, returned).
    - *Impact*: Enums provide type safety and readability for domain-specific states, reducing bugs from invalid values.

- **Interfaces** (`src/Library.ApplicationCore/Interfaces/`)
    - **IBookRepository, IAuthorRepository, IPatronRepository, ILoanRepository**: Define contracts for data access and manipulation for each entity.
    - **ILibraryService**: Specifies high-level operations such as checking out books, returning books, and searching.
    - *Impact*: Interfaces decouple implementation from usage, making the codebase easier to test, extend, and maintain.

- **Services** (`src/Library.ApplicationCore/Services/`)
    - **LibraryService**: Implements `ILibraryService`, containing business logic for library operations (e.g., loan validation, book availability checks).
    - *Impact*: Centralizes business rules, ensuring consistent behavior and simplifying future enhancements.

- **ConsoleApp** (`src/Library.Console/ConsoleApp.cs`)
    - **ConsoleApp**: The main entry point; manages application flow, user input, and output.
    - *Impact*: Provides a clear starting point for running and debugging the application.

- **CommonActions** (`src/Library.Console/CommonActions.cs`)
    - **CommonActions**: Contains reusable methods for common console operations (e.g., displaying menus, handling input).
    - *Impact*: Promotes code reuse and keeps the console UI logic organized.

- **Data** (`src/Library.Infrastructure/Data/`)
    - **JsonDataStore, Repository Implementations**: Handle reading/writing entity data to JSON files, implementing repository interfaces.
    - *Impact*: Abstracts data persistence, allowing for easy replacement or extension (e.g., switching to a database in the future).

*For new developers*: Understanding these classes and interfaces is essential for contributing effectively. They form the backbone of the application, and changes here can have wide-reaching effects. Always consult these abstractions before implementing new features or refactoring existing code.

## Usage

1. **Build the Solution**
   - Open the solution in Visual Studio or run:
     ```
     dotnet build [AccelerateDevGitHubCopilot.sln](http://_vscodecontentref_/0)
     ```

2. **Run the Console Application**
   - Navigate to the `src/Library.Console` directory and run:
     ```
     dotnet run --project [Library.Console.csproj](http://_vscodecontentref_/1)
     ```

3. **Configuration and Data**
   - Edit `appSettings.json` for configuration.
   - Modify JSON files in `src/Library.Console/Json/` to update initial data for authors, books, patrons, and loans.

4. **Testing**
   - Run unit tests from the `tests/UnitTests` project:
     ```
     dotnet test [UnitTests.csproj](http://_vscodecontentref_/2)
     ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
