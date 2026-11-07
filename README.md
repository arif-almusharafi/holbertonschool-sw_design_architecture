# Holberton School - Software Design and Architecture

Projects about designing software before writing it: UML diagrams and design patterns.

## Projects

| Folder | What is inside |
| --- | --- |
| [uml_intro](uml_intro/) | A class diagram and a sequence diagram for a small library system, written in Mermaid |
| [design_patterns](design_patterns/) | Python examples of three design patterns: Factory, Observer and Decorator |

## uml_intro

The system is a library where users borrow books through loans.

### Class diagram (`0-class_diagram.mmd`)

```mermaid
classDiagram
    Library "1" o-- "0..*" Book
    Library "1" o-- "0..*" User
    Library "1" *-- "0..*" Loan
    Loan "0..*" --> "1" User
    Loan "0..*" --> "1" Book
    Book  : +str title
    Book  : +str author
    Book : +bool state
    Book : +mark_as_unavailable()
    Book : +mark_as_available()
    class User {
      +str name
      +str email
    }
    class Loan {
      +str start_date
      +str end_date
      +close_loan()
    }
    class Library {
      +add_book()
      +register_user()
      +create_loan()
    }
```

### Sequence diagram (`1-sequence_diagram.mmd`)

What happens when a user creates a loan:

```mermaid
sequenceDiagram
    participant User
    participant Library
    participant Book
    User->>Library: create_loan
    Library ->> Book: mark_as_unavailable
    create participant Loan
    Library ->> Loan: create_loan
    Library-->>User: loan created
```

## design_patterns

| File | Pattern | Idea |
| --- | --- | --- |
| `0-factory.py` | Factory | One place creates objects, so the caller does not choose the exact class |
| `1-observer.py` | Observer | Objects subscribe and get notified when something changes |
| `2-decorator.py` | Decorator | Add new behavior to an object without changing its class |

## How to use

- The `.mmd` files are Mermaid diagrams. GitHub shows them as pictures, and you can also paste them into [mermaid.live](https://mermaid.live).
- Run a pattern example with `python3 file_name.py`.

## Author

Arif Almusharafi - [GitHub](https://github.com/arif-almusharafi)
