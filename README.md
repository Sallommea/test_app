# Quiz CLI (quiz-cli)

## Project Overview
Quiz CLI is a small, interactive command-line quiz application built with Node.js (ES modules). It presents multiple-choice questions organized by category, tracks your score, and allows reviewing answers at the end. The project is lightweight and intentionally has no external dependencies.

This repository contains a ready-to-run example under the `test-app/` directory. The top-level README (this file) summarizes the project and points to the runnable application inside `test-app/`.

## Key Features
- Interactive command-line quiz experience
- Multiple categories of questions (e.g., javascript, nodejs, general)
- Configurable number of questions per run and category selection
- Tracks score and displays final results with a review of answers
- Uses ANSI color helpers for a friendly terminal UI
- No external dependencies (uses Node.js built-in modules and ES modules)

## Prerequisites
- Node.js >= 18 (the package.json specifies `engines.node` >=18)
- npm (optional, for running npm scripts)

Note: The project uses ES modules (see `"type": "module"` in package.json). Run the app from the `test-app/` directory or use the provided npm scripts.

## Installation
Clone the repository (if not already) and then either run the app directly with `node` or via the npm script from inside the `test-app/` directory.

Steps:
1. Open a terminal and navigate to the repository
2. Change into the runnable app folder:
   - cd test-app

There are no external dependencies to install, but you can still run:
- npm install
to ensure npm state is set up (not required for dependencies in this project).

## How to Run
From the `test-app/` directory:

- Using npm script:
  - npm start

- Directly with Node:
  - node index.js

Example (from repo root):
- cd test-app
- npm start
or
- cd test-app
- node index.js

There is also a `npm test` script defined in the package metadata (see `test-app/package.json`) — use this to run any provided tests or validation scripts if present.

## Usage
When you run the app it will:
1. Show a banner
2. Prompt you to choose a category (or categories) from the available set
3. Ask how many questions you want to attempt
4. Run through the selected questions one-by-one using a multiple-choice selector UI
5. Track your answers and score
6. Present a final summary and optional review of all questions and your responses

Follow the on-screen prompts to interact with the quiz.

## File Structure
Top-level (summary):
- README.md (this file)
- test-app/ (runnable quiz app)

Contents of test-app/:
- index.js — CLI entrypoint (loads questions, shows banner, prompts user, instantiates Quiz)
- package.json — app metadata (name: quiz-cli, `engines.node` >=18, `"type": "module"`, npm scripts)
- data/questions.json — question data: categories mapping to arrays of multiple-choice questions
- src/colors.js — ANSI color utilities used for styling terminal output
- src/input.js — readline-based input helpers (prompt, select, confirm, pressEnter)
- src/quiz.js — Quiz class and main quiz logic (shuffling, progress, asking questions, scoring, review)

There are some macOS system files included in the repository copy (e.g., `__MACOSX` and `.DS_Store`) which can be ignored or removed.

## How to Add or Edit Questions
Questions are stored in JSON under:
- test-app/data/questions.json

The file groups questions by category (for example: `javascript`, `nodejs`, `general`). Each category maps to an array of multiple-choice question objects. To add or edit questions:

1. Open `test-app/data/questions.json`.
2. Follow the structure used by existing entries in that file. Each entry includes the question text, the set of choices, and the correct answer information (follow the form used by the existing objects to ensure compatibility).
3. Save the file and run the app again:
   - cd test-app
   - npm start

Tip: Keep the structure consistent with existing objects to avoid runtime errors. If you add a new category, ensure it is an object key with an array of question objects.

## Development Notes
- The app is implemented using ES modules (package.json: `"type": "module"`). Use `node` >= 18 to run.
- Input helpers are implemented with Node's `readline` module in `src/input.js`.
- `src/colors.js` provides simple ANSI color formatting — change or extend as desired.
- `src/quiz.js` contains the quiz flow: building a question set, shuffling, presenting choices, tracking answers, and showing results.
- No external packages are required. If you add dependencies, update `package.json` and run `npm install`.

## Testing
- If there are tests configured via the `test` script in `test-app/package.json`, run them via:
  - cd test-app
  - npm test

Otherwise, manual testing can be done by running the app and exercising different categories and question counts.

## Contributing
Contributions are welcome. Suggested workflow:
1. Fork the repository
2. Make changes in a feature branch
3. Ensure code follows the project's ES module structure
4. Update or add questions in `test-app/data/questions.json` if relevant
5. Open a pull request describing your changes

Please avoid committing OS-specific files like `.DS_Store` or `__MACOSX` folders.

## License
This project is provided under the MIT License. See `test-app/package.json` for the license field.

## Acknowledgements
- Built with Node.js and standard Node APIs
- Inspired by simple CLI quiz utilities and interactive terminal apps

---

For detailed implementation or to run the application, open the `test-app/` folder and follow the "How to Run" instructions above.
