# Quiz App - Spring Boot Project

A simple RESTful Quiz App to manage quiz sessions, fetch questions, submit answers, and get stats.

---

## Features:
1. Start a new quiz session.
2. Fetch a random question.
3. Submit an answer and check correctness.
4. Get quiz stats (correct/incorrect answers).

---

## Tech Stack:
- **Java 17**
- **Spring Boot 3.x**
- **Spring Data JPA**
- **H2 Database** (in-memory)
- **Maven**

---

## Setup Instructions:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/quiz-app.git
   cd quiz-app
   ```

2. **Build and run**:
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

3. **H2 Console**:
   - URL: `http://localhost:8080/h2-console`
   - JDBC URL: `jdbc:h2:mem:testdb`
   - Username: `sa`
   - Password: *(leave blank)*

---

## API Endpoints:

### 1. Start Quiz Session
- **Method**: `POST`  
- **URL**: `/api/quiz/start`  
- **Response**:
    ```json
    "Quiz session started. Call '/api/quiz/question' to get your first question."
    ```

### 2. Get Random Question
- **Method**: `GET`  
- **URL**: `/api/quiz/question`  
- **Response**:
    ```json
    {
      "id": 1,
      "question": "What is the capital of France?",
      "optionA": "Berlin",
      "optionB": "Madrid",
      "optionC": "Paris",
      "optionD": "Rome"
    }
    ```

### 3. Submit Answer
- **Method**: `POST`  
- **URL**: `/api/quiz/submit?questionId={id}&answer={answer}`  
- **Example**:
    ```
    POST /api/quiz/submit?questionId=1&answer=Paris
    ```
- **Response** (Correct Answer):
    ```json
    "Correct answer!"
    ```
- **Response** (Incorrect Answer):
    ```json
    "Incorrect answer. The correct answer is: Paris"
    ```

### 4. Get Quiz Stats
- **Method**: `GET`  
- **URL**: `/api/quiz/stats`  
- **Response**:
    ```json
    {
      "totalQuestionsAnswered": 3,
      "correctAnswers": 2,
      "incorrectAnswers": 1
    }
    ```

---

## Database Schema:

| **Field**          | **Type**    | **Description**         |
|---------------------|-------------|-------------------------|
| `id`               | `Long`      | Primary Key             |
| `question`         | `String`    | Quiz question text      |
| `optionA`, `optionB`, `optionC`, `optionD` | `String` | Options for the question |
| `correctAnswer`    | `String`    | Correct answer text     |

---

## Example Data:

The database is preloaded with the following questions:

1. **Question**: "What is the capital of France?"  
   - Options: A) Berlin, B) Madrid, C) Paris, D) Rome  
   - Correct Answer: `Paris`

2. **Question**: "What is 2 + 2?"  
   - Options: A) 3, B) 4, C) 5, D) 6  
   - Correct Answer: `4`

---

## Testing APIs:

Use **Postman**, **cURL**, or any API testing tool:

### Start a Quiz Session
```bash
curl -X POST http://localhost:8080/api/quiz/start
```

### Get a Random Question
```bash
curl -X GET http://localhost:8080/api/quiz/question
```

### Submit an Answer
```bash
curl -X POST "http://localhost:8080/api/quiz/submit?questionId=1&answer=Paris"
```

### Get Quiz Stats
```bash
curl -X GET http://localhost:8080/api/quiz/stats
```

---

## Run in IDE:

1. Open the project in **IntelliJ IDEA** or **Eclipse**.
2. Build the project.
3. Run `QuizAppApplication.java`.

---
