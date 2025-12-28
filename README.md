# Tetris Game

A modern implementation of the classic Tetris game built with C++ and SFML (Simple and Fast Multimedia Library). Features multiple difficulty modes, progressive challenges, and a clean user interface.

![Game Version](https://img.shields.io/badge/version-1.0-blue)
![C++](https://img.shields.io/badge/C++-17-00599C?logo=cplusplus)
![SFML](https://img.shields.io/badge/SFML-3.0-8CC445)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6)

## Features

### Game Modes
- **Beginner Mode**: 4 block types (I, O, T, L), normal falling speed
- **Advanced Mode**: All 7 classic Tetromino types, 30% faster falling speed

### Gameplay Features
- **Ghost Piece**: Shows where the current piece will land
- **Hold Piece**: Save a piece for later use (press C)
- **Hard Drop**: Instantly drop piece to the bottom (press Space)
- **Soft Drop**: Speed up falling (hold Down Arrow)
- **Progressive Difficulty**: Every 5 minutes, a bottom row becomes permanently locked
- **Level System**: Difficulty increases every 10 lines cleared
- **Scoring System**: Points awarded based on lines cleared simultaneously
  - 1 Line: 10 × Level
  - 2 Lines: 30 × Level
  - 3 Lines: 60 × Level
  - 4 Lines (Tetris): 100 × Level

### User Interface
- Clean, modern UI with dual-column layout
- Real-time score, level, and lines cleared tracking
- Next piece preview
- Hold piece display
- Countdown timer for difficulty progression
- Locked rows indicator
- Comprehensive controls panel
- High scores leaderboard (top 10)
- Pause menu with multiple options
- Help screen with complete game instructions

## Requirements

### System Requirements
- **Operating System**: Windows 10/11
- **Compiler**: MinGW-w64 (g++ 8.0 or higher)
- **C++ Standard**: C++17 or higher
- **SFML**: Version 3.0 or higher

### Dependencies
- SFML Graphics
- SFML Window
- SFML System
- Arial font (arial.ttf)

## Installation

### Option 1: Using Pre-compiled Binary
1. Download the latest release
2. Extract all files to a folder
3. Ensure `arial.ttf` is in the same directory
4. Run `Tetris.exe`

### Option 2: Compile from Source

#### Prerequisites
1. **Install MSYS2** (if not already installed)
   ```bash
   Download from: https://www.msys2.org/
   ```

2. **Install MinGW-w64 and SFML**
   ```bash
   pacman -S mingw-w64-x86_64-gcc
   pacman -S mingw-w64-x86_64-sfml
   ```

3. **Install Arial font**
   - Place `arial.ttf` in the project directory
   - Or copy from `C:\Windows\Fonts\arial.ttf`

#### Building the Game

**On Windows:**
```batch
# Simply run the compilation script
compile.bat

# Or build and run immediately
run.bat
```

**Using CMake:**
```bash
mkdir build
cd build
cmake ..
cmake --build .
```

The compilation script automatically:
- Detects MSYS2/MinGW installation
- Finds SFML libraries
- Compiles all source files
- Links dependencies
- Copies required DLLs

## Controls

| Action | Key |
|--------|-----|
| Move Left | Left Arrow |
| Move Right | Right Arrow |
| Soft Drop | Down Arrow |
| Rotate Clockwise | Up Arrow |
| Hard Drop | Space |
| Hold Piece | C |
| Pause Game | P |

### Menu Navigation
- **Up/Down Arrows**: Navigate menu options
- **Enter**: Select option
- **Escape**: Return to previous menu (in help/scores screens)

## Game Rules

1. **Objective**: Clear lines by completing horizontal rows with blocks
2. **Line Clearing**: Completed rows disappear and award points
3. **Game Over**: Occurs when blocks stack to the top of the board
4. **Level Progression**: Every 10 lines cleared increases the level and speed
5. **Locked Rows**: Every 5 minutes, one bottom row becomes locked (cannot be cleared)

## Project Structure

```
tetris game/
├── main.cpp              # Entry point
├── Game.cpp/h            # Main game loop and state management
├── Board.cpp/h           # Game board and grid logic
├── Tetromino.cpp/h       # Tetromino piece definitions and rotations
├── Renderer.cpp/h        # All rendering and drawing operations
├── Menu.cpp/h            # Menu system (main, pause, help, scores)
├── ScoreManager.cpp/h    # Score tracking and high scores management
├── CMakeLists.txt        # CMake build configuration
├── compile.bat           # Windows compilation script
├── compile.sh            # Linux/Mac compilation script
├── run.bat               # Windows build and run script
├── arial.ttf             # Required font file
├── highscores.txt        # High scores storage
└── README.md             # This file
```

## Technical Details

### Architecture
- **Object-Oriented Design**: Clean separation of concerns
- **Entity-Component Pattern**: Modular game components
- **State Machine**: Manages game states (Menu, Playing, Paused, Game Over)
- **MVC-inspired Structure**: Renderer handles all drawing, Game handles logic

### Performance
- **Frame Rate**: Capped at 60 FPS
- **Window Size**: 900×720 pixels
- **Board Size**: 10×20 cells
- **Block Size**: 30×30 pixels

### Data Persistence
- High scores saved to `highscores.txt`
- Player names stored with scores
- Automatic file creation if not present

## Development

### Building for Development
```batch
# Compile with debug symbols
g++ -g -std=c++17 *.cpp -I"path/to/SFML/include" -L"path/to/SFML/lib" ^
    -lsfml-graphics-3 -lsfml-window-3 -lsfml-system-3 -o Tetris.exe
```

### Adding New Features
The modular structure makes it easy to extend:
- **New Tetromino types**: Modify `Tetromino.cpp`
- **Different scoring**: Edit `ScoreManager.cpp`
- **UI changes**: Update `Renderer.cpp`
- **New game modes**: Extend `Game.cpp`

## Troubleshooting

### Common Issues

**"Failed to load arial.ttf"**
- Ensure `arial.ttf` is in the same directory as the executable
- Copy from `C:\Windows\Fonts\arial.ttf` if needed

**"SFML DLLs not found"**
- The compile script should copy DLLs automatically
- Manually copy from `C:\msys64\mingw64\bin\`:
  - `sfml-graphics-3.dll`
  - `sfml-window-3.dll`
  - `sfml-system-3.dll`
  - Additional dependencies as needed

**"g++ not found"**
- Install MSYS2 and MinGW-w64
- Add MinGW to system PATH: `C:\msys64\mingw64\bin`

**Game window not appearing**
- Check if antivirus is blocking the executable
- Verify all SFML DLLs are present
- Run from command prompt to see error messages

## Credits

**Developer**: Rafay  
**Library**: SFML (Simple and Fast Multimedia Library)  
**Font**: Arial (Microsoft Typography)

## License

This project is provided as-is for educational and entertainment purposes.

SFML is licensed under the zlib/png license.

## Changelog

### Version 1.0 (December 2025)
- Initial release
- Two difficulty modes
- Progressive difficulty system
- High scores leaderboard
- Complete menu system
- Ghost piece feature
- Hold piece functionality
- Locked rows mechanic
- Dual-column UI layout

## Future Enhancements

Potential features for future versions:
- [ ] Multiplayer mode
- [ ] Custom key bindings
- [ ] Sound effects and music
- [ ] Themes and color schemes
- [ ] Custom difficulty settings
- [ ] Replay system
- [ ] Statistics tracking
- [ ] Online leaderboard

## Contact

For bugs, suggestions, or contributions, please open an issue or contact the developer.

---

**Enjoy the game! Try to beat the high score!** 🎮
