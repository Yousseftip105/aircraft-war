# Aircraft War: a Java shooter built with design patterns

A 2D vertical shooter written in Java. I built it in stages over several labs for my object-oriented software engineering course at Harbin Institute of Technology (Shenzhen). In each lab I added a feature and refactored the code with a classic design pattern.

![Gameplay screenshot](images/screenshot.png)

## Features

- **Hero aircraft** controlled by the player, with HP capped at 200
- **Three kinds of enemies**
  - Mob enemy: flies straight down
  - Elite enemy: drifts sideways, shoots, and can drop a power-up
  - Boss enemy: appears every 300 points (one at a time), hovers left and right, fires a ring of 20 bullets and drops 0–2 power-ups
- **Three power-ups**
  - Health supply: restores HP
  - Fire supply: switches the hero to a 5-bullet spread shot
  - Super fire supply: switches the hero to a 20-bullet circular shot

## Design patterns used

| Pattern | Where | Why |
| --- | --- | --- |
| Singleton | `HeroAircraft` (double-checked locking) | Guarantees one hero per game and gives one global access point |
| Factory Method | `EnemyFactory` → `MobFactory`, `EliteFactory`, `BossFactory`; `SupplyFactory` → `HpSupplyFactory`, `FireSupplyFactory`, `SuperFireSupplyFactory` | Moves object creation out of the game loop, so a new enemy or supply type means a new factory instead of edits to `Game` |
| Strategy | `ShootStrategy` → `StraightShoot`, `SpreadShoot`, `CircularShoot` | Lets any aircraft change how it shoots at runtime (for example after picking up a power-up) |

The class diagrams are in the `uml/` folder (PlantUML).

## Project structure

```
src/
  aircraft/      Hero, mob, elite and boss aircraft
  basic/         Base flying object
  supply/        Health, fire and super fire supplies
  factory/       Enemy and supply factories
  shoot/         Shooting strategies
  application/   Game loop, main window, image loading
uml/             PlantUML class diagrams
images/          Game sprites
```

## How to run

1. Install a JDK (version 11 or later) and IntelliJ IDEA.
2. Open this folder as a project in IntelliJ.
3. Run the `Main` class in the `application` package.

## What I learned

- Splitting a program into classes with one clear responsibility each
- When Singleton, Factory Method and Strategy help, and what problem each solves
- Refactoring working code step by step without breaking existing features
- Drawing UML class diagrams to plan changes before coding
