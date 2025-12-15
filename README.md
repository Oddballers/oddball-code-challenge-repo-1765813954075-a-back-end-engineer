# oddball-code-challenge-repo-1765813954075-a-back-end-engineer

# Coding Challenge

## Problem Description
Dear Candidate, you are applying for a Back End Engineer position at our company. This challenge is designed to assess your skills at a senior level, particularly in building a RESTful API using Node.js and TypeScript.

## Requirements
1. Implement a RESTful API for managing a collection of books.
2. The API should support the following endpoints:
   - `GET /books` - Retrieve a list of all books.
   - `GET /books/:id` - Retrieve a single book by ID.
   - `POST /books` - Create a new book.
   - `PUT /books/:id` - Update an existing book.
   - `DELETE /books/:id` - Delete a book by ID.
3. Ensure proper error handling and validation for each endpoint.
4. Store the book data in memory (no database required).

## Technical Specifications  
- Use Node.js with TypeScript.
- Use Express.js as the web framework.
- Follow RESTful best practices.
- Ensure code is modular and well-documented.

## Starter Files

### File 1: `server.ts`
```typescript
import express, { Request, Response } from 'express';

const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

let books: { id: number; title: string; author: string }[] = [];

app.get('/books', (req: Request, res: Response) => {
    res.json(books);
});

app.get('/books/:id', (req: Request, res: Response) => {
    const book = books.find(b => b.id === parseInt(req.params.id));
    if (!book) {
        res.status(404).send('Book not found');
    }
    res.json(book);
});

app.post('/books', (req: Request, res: Response) => {
    const { title, author } = req.body;
    const newBook = { id: books.length + 1, title, author };
    books.push(newBook);
    res.status(201).json(newBook);
});

app.put('/books/:id', (req: Request, res: Response) => {
    const { title, author } = req.body;
    const bookIndex = books.findIndex(b => b.id === parseInt(req.params.id));
    if (bookIndex === -1) {
        res.status(404).send('Book not found');
    }
    const updatedBook = { id: parseInt(req.params.id), title, author };
    books[bookIndex] = updatedBook;
    res.json(updatedBook);
});

app.delete('/books/:id', (req: Request, res: Response) => {
    const bookIndex = books.findIndex(b => b.id === parseInt(req.params.id));
    if (bookIndex === -1) {
        res.status(404).send('Book not found');
    }
    books.splice(bookIndex, 1);
    res.status(204).send();
});

app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
});
```

### File 2: `bookModel.ts`
```typescript
interface Book {
    id: number;
    title: string;
    author: string;
}

let books: Book[] = [];

const addBook = (book: Book) => {
    books.push(book);
};

const getBooks = () => {
    return books;
};

const getBookById = (id: number) => {
    return books.find(book => book.id === id);
};

const updateBook = (id: number, updatedBook: Book) => {
    const index = books.findIndex(book => book.id === id);
    if (index !== -1) {
        books[index] = updatedBook;
    }
};

const deleteBook = (id: number) => {
    books = books.filter(book => book.id !== id);
};

export { addBook, getBooks, getBookById, updateBook, deleteBook };
```

### File 3: `errorHandler.ts`
```typescript
import { Request, Response, NextFunction } from 'express';

const errorHandler = (err: Error, req: Request, res: Response, next: NextFunction) => {
    console.error(err);
    res.status(500).json({ message: 'An unexpected error occurred' });
};

export default errorHandler;
```

## Sample Data
You can use the following sample data for testing your API:
```json
[
  { "id": 1, "title": "1984", "author": "George Orwell" },
  { "id": 2, "title": "To Kill a Mockingbird", "author": "Harper Lee" },
  { "id": 3, "title": "The Great Gatsby", "author": "F. Scott Fitzgerald" }
]
```

## Evaluation Criteria
- Correctness of API functionality.
- Code quality and organization.
- Proper error handling and validation.
- Use of TypeScript features effectively.
- Clarity and readability of code.

## Submission Instructions
Please submit your solution as a zip file containing the following:
- All the source code files (`server.ts`, `bookModel.ts`, `errorHandler.ts`).
- A README file with instructions on how to run your API.
- Any additional files you created during your implementation.

Make sure to complete the challenge within 90 minutes. Good luck!