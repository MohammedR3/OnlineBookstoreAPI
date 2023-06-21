

# Online Bookstore API

This is a RESTful API for an online bookstore, built with Spring Boot.

---

## Setup

This project uses the H2 in-memory database. No additional setup is required to use the database.

To run the project, use the following command:

```powershell
./mvnw spring-boot:run
```

## API Endpoints

### GET /api/books

Retrieves a list of all books. You can add query parameters to search for books by title, author, or ISBN, and to paginate the results.

Example usage:

```powershell
# Get all books
$response = Invoke-WebRequest -Uri http://localhost:8081/api/books

# Search for books with "Example" in the title
$response = Invoke-WebRequest -Uri "http://localhost:8081/api/books?title=Example"

```

### GET /api/books/{id}

Retrieves a specific book by its ID.

Example usage:

```powershell
$response = Invoke-WebRequest -Uri http://localhost:8081/api/books/1
```

### POST /api/books

Adds a new book to the bookstore.

Example usage:

```powershell
$body = @{
    title = "Example Book"
    author = "Example Author"
    isbn = "1234567890"
    price = 19.99
    publicationYear = 2023
} | ConvertTo-Json

$response = Invoke-WebRequest -Uri http://localhost:8081/api/books -Method POST -Body $body -ContentType "application/json"
```

### PUT /api/books/{id}

Updates an existing book's information.

Example usage:

```powershell
$body = @{
    title = "Updated Title"
    author = "Updated Author"
    isbn = "1234567890"
    price = 19.99
    publicationYear = 2023
} | ConvertTo-Json

$response = Invoke-WebRequest -Uri http://localhost:8081/api/books/1 -Method PUT -Body $body -ContentType "application/json"
```

### DELETE /api/books/{id}

Deletes a book from the bookstore.

Example usage:

```powershell
$response = Invoke-WebRequest -Uri http://localhost:8081/api/books/1 -Method DELETE
```
