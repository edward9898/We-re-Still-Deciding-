# We-re-Still-Deciding-

## Game Concept
A launch-night roleplaying game where the player enters a game store competing against other customers to find and purchase the last copy of GTA VI.

Explore the store, solve five puzzles, and outlast the other customers to win. This is a fan-made prototype and is not affiliated with the game or its publisher.

## Play
- Open `index.html` in a modern web browser. No installation or build step is needed.
- Move with **WASD** or the **arrow keys**; the on-screen arrows also work.
- Walk onto each glowing puzzle station and choose an answer.
- Rivals navigate the aisles toward you. Get beside one and press **Space** (or use the shove button) twice to send them out of the race; they can shove you back and reduce your health.
- Track your health, clue count, and rivals left in the map HUD. Find the first-aid kit near the entrance to restore health.
- Reach checkout after solving all five puzzles and clearing every rival to win. Losing all health ends the run.
- Press **E** to interact with a puzzle station while standing on it.
- After a win or loss, choose **Play again** to restart.

## Team Members and Responsibilities

### Eddie
- World map and player movement
- Combat system
- Enemy/customer encounters
- Player health and winning conditions

### JCronk
- Five puzzles and riddles
- Store environment and design
- Colors and visual design
- Dialogue and world descriptions

## Game Features
- Interactive store map and keyboard/touch controls
- Five multiple-choice puzzles
- Rival encounters, health, and a first-aid pickup
- Checkout objective and win/loss conditions
- Last-copy checkout after completing every objective

## Six Pillars of Computer Science

The following examples describe how the six pillars would be represented in a C++ implementation of the game. The repository currently implements the playable fan-made prototype in HTML, CSS, and JavaScript; no C++ source files are present, so the C++ structures below are **planned** unless a feature is already demonstrated in the current prototype.

### 1. Variables (including vectors)

- **Implemented in the prototype:** The player and rivals use stored variables for their health, movement position, solved-puzzle count, and combat state. The HUD reads these values to display the player's health and the number of rivals remaining.
- **Planned C++ implementation:** The player and enemy health, attack damage, and player position would be stored in variables such as `int playerHealth`, `int enemyHealth`, `int attackDamage`, and `float playerX`/`float playerY`.
- A `std::vector` could store the map locations and checkpoints, the active enemy or rival objects, and the puzzle data. This allows the game to add, remove, or process each map item dynamically rather than writing a separate variable for every possible item.

### 2. Algebra

- **Implemented in the prototype:** Combat and health behavior use numerical calculations, such as reducing health after an enemy shove and restoring health when the player collects a first-aid kit.
- **Planned C++ implementation:** Combat damage could be calculated with expressions such as `damage = attackDamage - enemyDefense`. Health could be updated with `playerHealth -= damage` or `playerHealth += healthRestore`. Player statistics might include damage, defense, movement speed, or puzzle score, and the game could calculate results from a formula such as `finalDamage = attackDamage + bonusDamage - targetDefense`.
- These calculations would keep combat and player progression consistent and measurable.

### 3. Input and Output

- **Implemented in the prototype:** Keyboard input with **WASD**, the arrow keys, **Space**, and **E** moves the player, shoves rivals, and interacts with puzzle stations. The browser interface outputs dialogue, puzzle choices, clues, health, and win/loss results.
- **Planned C++ implementation:** Keyboard input could be read by a game framework or console input function, with movement keys controlling the player's position and dedicated keys triggering attack, interaction, and puzzle answers. Output could include console text or a graphical interface that displays store information, dialogue, clue feedback, remaining rivals, and the final result.

### 4. Branches

- **Implemented in the prototype:** Conditional logic determines whether a shove succeeds, whether a rival or the player loses all health, whether a puzzle answer is correct, and whether the player reaches the checkout after completing every objective.
- **Planned C++ implementation:** `if` and `else` statements could decide that an attack succeeds only when the player is close enough to a rival, that an enemy is defeated when `enemyHealth <= 0`, and that a puzzle is solved only when the selected answer matches the correct answer. Additional conditions could determine whether the player wins or loses:

  ```cpp
  if (playerHealth <= 0) {
      // Display the losing state
  } else if (puzzlesSolved == 5 && rivalsRemaining == 0) {
      // Display the winning state
  }
  ```

### 5. Loops

- **Implemented in the prototype:** The browser game loop repeatedly checks player movement, rival movement, combat interactions, health changes, objectives, and win/loss conditions while the run continues.
- **Planned C++ implementation:** A main `while` loop could keep the game running until the player wins or loses. `for` or `while` loops could process repeated player actions and combat turns, continue updating movement while a key is held or active, and iterate through vectors to update every rival or puzzle station. Loops would also allow a player to try another action or another puzzle answer after a failed choice.

### 6. Functions

- **Implemented in the prototype:** The prototype separates behavior into JavaScript functions for movement, combat, puzzle interaction, dialogue, rendering, and restarting the game.
- **Planned C++ implementation:** Separate C++ functions would organize player movement, combat, puzzles, dialogue, and game progression. For example, `movePlayer()`, `performAttack()`, `checkPuzzleAnswer()`, `showDialogue()`, and `checkGameState()` would divide the program into focused responsibilities. These functions could call one another so that movement leads to interaction checks, combat updates health, and game-state checks determine when to continue, restart, or end the run.