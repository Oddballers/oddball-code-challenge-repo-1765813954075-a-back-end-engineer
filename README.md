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