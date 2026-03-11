# Quiz CLI

## Project Overview

Quiz CLI is a small interactive command-line quiz game written in modern JavaScript (ES modules). It runs on Node.js (>=18) and provides multiple categories of programming-related questions (JavaScript, Node.js, General Programming). The CLI presents multiple-choice questions, tracks your score, and shows a results summary with review of incorrect answers.

## Features

- Multiple question categories (JavaScript, Node.js, General Programming)
- Configurable number of questions per session (All / 3 / 5)
- Shuffled questions each run
- Progress bar and per-question feedback
- Colorized terminal output (ANSI colors)
- Simple, dependency-free implementation using Node.js built-ins

## File Structure

```
test-app/
  index.js                # Entry point - orchestrates the CLI flow
  package.json            # Project metadata and scripts (start/test)
  data/
    questions.json        # JSON file containing categories and questions
  src/
    input.js              # Readline-based input helpers (prompt, select, confirm)
    quiz.js               # Quiz logic and Quiz class
    colors.js             # ANSI color helpers for colored output
  README.md               # Project documentation (this file)
```

## Setup Instructions

1. Clone the repository

```bash
git clone https://github.com/Sallommea/test_app.git
cd test-app/test-app
```

2. Ensure you have Node.js 18 or newer installed (package.json specifies engines: >=18.0.0)

3. Install dependencies (this project has no external dependencies, but installing ensures environment readiness):

```bash
npm install
```

4. Run the application

```bash
npm start
# or
node index.js
```

## Usage Examples

- Start the app:

```bash
npm start
```

- In the interactive prompt:
  1. Choose a category from the list (e.g. "JavaScript Basics")
  2. Choose how many questions to answer (All / 3 / 5)
  3. Answer questions by entering the number corresponding to your choice
  4. Press Enter between questions to continue
  5. At the end you will see your score, a performance message, and a review of incorrect answers
  6. Choose whether to play again when prompted

## Adding or Editing Questions

Questions are stored in JSON at `data/questions.json` in the following structure:

```
{
  "categories": {
    "javascript": {
      "name": "JavaScript Basics",
      "questions": [
        {
          "question": "...",
          "options": ["opt1", "opt2", "opt3"],
          "answer": 0,            # index of correct option
          "explanation": "..."  # optional
        }
      ]
    }
  }
}
```

To add new categories or questions, edit this file and follow the same shape.

## Development Notes

- Entry point: `index.js` — loads questions, displays menu, and runs the Quiz class
- Core logic lives in `src/quiz.js` which implements the Quiz class and rendering
- Input helpers are in `src/input.js` and use Node's `readline` API
- `src/colors.js` provides small utility functions to colorize terminal output using ANSI codes
- The project intentionally has no external dependencies to keep it lightweight and easy to inspect

## Requirements

- Node.js >= 18.0.0
- POSIX-compatible terminal for ANSI color support (most modern terminals)

## License

This project uses the MIT License (see package.json).
