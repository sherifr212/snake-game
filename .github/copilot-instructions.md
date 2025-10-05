# Copilot Instructions for Snake Game

This repository contains a TypeScript-based Snake game built with the Phaser.js HTML5 game framework. These instructions will help Copilot understand the project structure, coding standards, and development workflow.

## Project Overview

- **Framework**: Phaser.js 2.x for game engine functionality
- **Language**: TypeScript compiled to ES5 JavaScript
- **Architecture**: Object-oriented design with separate classes for game entities
- **Browser Target**: HTML5-compatible browsers with Canvas support
- **Development Environment**: Visual Studio with TypeScript tooling

## Project Structure

```
SnakeGame/
├── index.html          # Main HTML entry point
├── SnakeGame.csproj    # Visual Studio project file
├── Resources/          # Game assets (PNG sprites)
│   ├── BodyBead.png    # Snake body segment sprite
│   ├── HeadBead.png    # Snake head sprite
│   └── Prey.png        # Food/prey sprite
└── Scripts/
    ├── app.ts          # Main application entry point and game loop
    ├── SnakeGame.ts    # Core game logic and state management
    ├── Bead.ts         # Snake segment (bead) entity class
    ├── Prey.ts         # Food/prey entity class
    ├── phaser.d.ts     # Phaser.js TypeScript definitions
    ├── pixi.d.ts       # PIXI.js TypeScript definitions
    ├── p2.d.ts         # p2 physics TypeScript definitions
    └── _references.js  # TypeScript reference file
```

## Core Architecture

### Main Classes

1. **Application** (`app.ts`): Main entry point, manages Phaser.Game instance and game loop
2. **SnakeGame** (`SnakeGame.ts`): Core game logic, snake movement, collision detection, scoring
3. **Bead** (`Bead.ts`): Represents individual snake segments (head and body)
4. **Prey** (`Prey.ts`): Represents food items that the snake consumes

### Game Flow

1. Application initializes Phaser.Game with 810x600 canvas
2. SnakeGame handles preload, create, and update lifecycle
3. Snake starts with 6 segments moving right
4. Game clock ticks every 100ms to update snake position
5. Collision detection for walls, self-collision, and food consumption
6. Score tracking and game over states

## Development Guidelines

### TypeScript Standards

- Use ES5 target for broad browser compatibility
- Leverage strong typing throughout the codebase
- Use enum for Direction (Up, Down, Right, Left)
- Follow object-oriented principles with clear class responsibilities
- Use Phaser.js types from included definition files

### Code Style

- Use camelCase for variables and methods
- Use PascalCase for classes and enums
- Static properties for sprite paths and configuration
- Bind methods properly for Phaser lifecycle callbacks
- Keep sprite sizes consistent (30px squares for all game entities)

### Game Constants

- Game dimensions: 810x600 pixels
- Game clock tick: 100ms intervals
- Bead size: 30x30 pixels
- Initial snake size: 6 segments
- Starting direction: Right

## Build Process

### TypeScript Compilation

The project uses Visual Studio's TypeScript compiler with these settings:
- Target: ES5
- Source maps enabled in Debug mode
- Comments preserved in Debug mode
- Automatic compilation on save

### Manual Compilation

For command-line compilation:
```bash
cd SnakeGame/Scripts
tsc *.ts --target es5 --skipLibCheck
```

### Dependencies

- **Phaser.js**: Included as `phaser.js` in Scripts folder
- **Type Definitions**: All necessary `.d.ts` files are included
- **Assets**: PNG sprites in Resources folder

## Testing Approach

### Manual Testing

- Open `index.html` in a web browser
- Test snake movement with arrow keys
- Verify collision detection (walls and self)
- Test food consumption and score increment
- Verify game over scenarios

### Key Test Scenarios

1. **Movement**: Snake responds to arrow key input correctly
2. **Growth**: Snake grows when eating prey
3. **Boundaries**: Snake dies when hitting walls
4. **Self-collision**: Snake dies when hitting itself
5. **Scoring**: Score increases when prey is consumed
6. **Prey placement**: New prey appears randomly after consumption

## Common Development Tasks

### Adding New Features

1. Identify the appropriate class for the feature
2. Update TypeScript interfaces if needed
3. Implement the feature following existing patterns
4. Test in browser environment
5. Ensure no TypeScript compilation errors

### Modifying Game Mechanics

- **Speed changes**: Modify `Application.GameClockTick` value
- **Size changes**: Update `Application.GameWidth/GameHeight`
- **Snake size**: Modify initial `snakeSize` in SnakeGame
- **Sprite changes**: Update paths in static properties

### Debugging

- Use browser developer tools for runtime debugging
- Check TypeScript compilation errors in Visual Studio
- Verify asset paths are correct
- Test game state transitions thoroughly

## File Dependencies

### Critical Dependencies

- `app.ts` → depends on `SnakeGame.ts`
- `SnakeGame.ts` → depends on `Bead.ts`, `Prey.ts`
- All files depend on `phaser.d.ts` for Phaser.js typing
- HTML loads compiled JavaScript files in correct order

### Load Order in HTML

1. `phaser.js` (framework)
2. `app.js` (main application)
3. `SnakeGame.js` (game logic)
4. `Bead.js` (snake segments)
5. `prey.js` (food entities)

## Performance Considerations

- Game runs at ~10 FPS (100ms tick rate)
- Sprites are reused rather than created/destroyed
- Collision detection is grid-based for efficiency
- Minimal DOM manipulation for score display

## Browser Compatibility

- Requires HTML5 Canvas support
- Tested with modern browsers (Chrome, Firefox, Safari, Edge)
- No external dependencies beyond included Phaser.js
- Responsive to keyboard input via Phaser's input system

## Troubleshooting

### Common Issues

1. **TypeScript compilation errors**: Check type definitions are properly referenced
2. **Sprites not loading**: Verify file paths in Resources folder
3. **Game not starting**: Check browser console for JavaScript errors
4. **Input not working**: Ensure Phaser.Game is properly initialized
5. **Performance issues**: Monitor game loop timing and sprite count

### Debug Mode

Enable TypeScript source maps for easier debugging:
- Set TypeScript project to Debug configuration
- Use browser dev tools to step through TypeScript source
- Check game state variables in SnakeGame class instance

When making changes to this codebase, always consider the game's real-time nature and the interdependencies between the game entities. Test thoroughly in a browser environment since this is a client-side HTML5 game.