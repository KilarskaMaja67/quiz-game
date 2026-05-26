# Quiz Game

A lightweight, responsive quiz application built using vanilla JavaScript, modern Web APIs, and CSS state modifiers. The app dynamically loads questions, prevents double-submissions, and features a smooth, real-time progress bar.

---

## Interactive Gameplay & View States

The application functions as a Single Page Application (SPA), using simple CSS class toggles (`.screen.active`) to transition between different screens without reloading the page.

### 1. Welcome Screen
The landing page primes the user and prepares the question dataset before the game begins.

![Start Screen](assets/start.png)

### 2. Instant Feedback (Correct Answer)
When a user selects the correct option, the choice highlights in green and the controls instantly lock to prevent multiple submissions.

![Correct Answer Flow](assets/example.png)

### 3. Error Handling (Incorrect Answer)
If a user selects the wrong answer, their choice highlights in red while the correct answer is simultaneously revealed to help with learning retention.

![Incorrect Answer Feedback](assets/wrong.png)

---

## Key Features & Architecture

### 1. View State Machine
Instead of using complex page routing, the application includes three modular containers in the HTML layout (`#start-screen`, `#quiz-screen`, and `#result-screen`).
* **Screen Swapping:** Managed by adding or removing an `.active` class via JavaScript `classList`.
* **Layout Control:** Hidden screens use `display: none`, while the active screen switches to `display: block`.

### 2. Double-Submit Protection
To keep scoring accurate, the engine locks interactive controls the moment an option is clicked:
* **Input Guard:** A state flag (`answersDisabled = true`) stops any further clicks once a selection is made.
* **Visual Matrix:** The app loops through all options, applies color-coded classes (`.correct` or `.incorrect`), and disables future interaction.

### 3. Live Progress Bar
Features a smooth tracking indicator to keep players updated on their progress:
* Calculates the current progress using a simple percentage formula: `(currentQuestionIndex / totalQuestions) * 100`.
* Applies the percentage directly to a CSS width property, animated with a smooth transition (`transition: width 0.3s ease`).

---

## Technical Highlights

* **Separation of Concerns:** Questions are cleanly organized inside a modular array of objects containing the question text, option choices, and correct answer flags.
* **Timed Transitions:** Uses `setTimeout()` to pause the screen for exactly 1000ms after an answer is selected, giving the user time to see the feedback before the next question loads.
* **Dynamic Results:** Computes custom end-game messages (e.g., "Perfect!", "Great job!") based on the user's final score percentage.

---

## Quick Start

You can run this project locally without needing any build tools, servers, or package managers:

1. Clone the repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/vanilla-js-quiz-game.git](https://github.com/YOUR_USERNAME/vanilla-js-quiz-game.git)
