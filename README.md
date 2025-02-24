# 3D Maze Game Demo

A web-based 3D game featuring a procedurally generated maze and an animated soldier character, built with Three.js.

## Overview

This project demonstrates a 3D maze game where players control a soldier character through a procedurally generated maze environment. The game features smooth character animations, collision detection, and dynamic camera controls.

## Architecture

### Core Components Flow
```mermaid
graph TD
    A[Game Initialization] --> B[Scene Setup]
    B --> C[Asset Loading]
    C --> D[Game Loop]
    
    subgraph "Scene Setup"
        B1[Create Three.js Scene]
        B2[Setup Renderer]
        B3[Configure Lighting]
        B4[Generate Maze]
    end
    
    subgraph "Asset Loading"
        C1[Load Soldier Model]
        C2[Generate Textures]
        C3[Setup Animations]
    end
    
    subgraph "Game Loop"
        D1[Update Physics]
        D2[Process Input]
        D3[Update Animations]
        D4[Render Scene]
    end
    
    B --> B1 & B2 & B3 & B4
    C --> C1 & C2 & C3
    D --> D1 --> D2 --> D3 --> D4
```

### Movement System
```mermaid
graph LR
    A[Input Detection] --> B[Movement Vector]
    B --> C{Collision Check}
    C -->|No Collision| D[Update Position]
    C -->|Collision| E[Cancel Movement]
    D --> F[Update Animation]
    D --> G[Update Camera]
```

## Implementation Details

### Core Technologies
- Three.js (r128) for 3D rendering
- GLTFLoader for model loading
- OrbitControls for camera management

### Key Features

#### 1. Procedural Maze Generation
```mermaid
classDiagram
    class MazeGenerator {
        +mazeSize: number
        +cellSize: number
        +createMaze()
        +generateWalls()
        +setupColliders()
    }
    
    class Cell {
        +position: Vector3
        +isWall: boolean
        +createGeometry()
    }
    
    MazeGenerator --> Cell
```

#### 2. Character Control System
```mermaid
classDiagram
    class MovementController {
        +speed: number
        +direction: Vector3
        +processInput()
        +updatePosition()
        +checkCollisions()
    }
    
    class AnimationSystem {
        +mixer: AnimationMixer
        +actions: Map
        +updateAnimation()
        +transitionTo()
    }
    
    MovementController --> AnimationSystem
```

## Setup and Controls

### Installation
1. No installation required - runs directly in browser
2. All dependencies loaded via CDN:
   ```html
   <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
   <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/loaders/GLTFLoader.js"></script>
   <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script>
   ```

### Controls
```mermaid
graph LR
    A[Player Input] --> B[Movement]
    A --> C[Camera]
    
    subgraph "Movement Controls"
        B1[W - Forward]
        B2[S - Backward]
        B3[A - Left]
        B4[D - Right]
    end
    
    subgraph "Camera Controls"
        C1[Mouse Drag - Rotate]
        C2[Mouse Wheel - Zoom]
    end
    
    B --> B1 & B2 & B3 & B4
    C --> C1 & C2
```

## Technical Features

### 1. Lighting System
- Ambient light for base illumination
- Hemisphere light for sky/ground contrast
- Directional light for shadows
- Point light for atmosphere

### 2. Texture Generation
- Procedurally generated textures for walls and floor
- Custom patterns and grid systems
- Dynamic material properties

### 3. Collision Detection
```mermaid
graph TD
    A[Movement Input] --> B[Calculate New Position]
    B --> C[Create Bounding Box]
    C --> D{Check Wall Collisions}
    D -->|Collision| E[Prevent Movement]
    D -->|No Collision| F[Update Position]
```

### 4. Animation System
- Smooth transitions between idle and run states
- Animation mixing for fluid movement
- State-based animation control

## Performance Optimizations

### 1. Rendering
- Efficient use of geometries and materials
- Proper disposal of unused resources
- Optimized render loop

### 2. Physics
- Simple but effective collision detection
- Optimized bounding box calculations
- Efficient movement calculations

### 3. Memory Management
- Texture reuse across similar objects
- Proper cleanup of unused resources
- Optimized asset loading

## Debug Features

The game includes a debug overlay showing:
- Current position (X, Y, Z)
- Rotation angle
- Movement state

## Code Structure

### Main Components
```mermaid
graph TD
    A[index.html] --> B[Scene Setup]
    A --> C[Game Logic]
    A --> D[Event Handlers]
    
    subgraph "Scene Components"
        B1[Lighting]
        B2[Camera]
        B3[Maze]
        B4[Character]
    end
    
    subgraph "Game Systems"
        C1[Movement]
        C2[Collisions]
        C3[Animations]
        C4[Updates]
    end
    
    B --> B1 & B2 & B3 & B4
    C --> C1 & C2 & C3 & C4
```

## Future Enhancements

```mermaid
graph LR
    A[Current Features] --> B[Planned Updates]
    
    subgraph "Planned Features"
        B1[Advanced Maze Algorithms]
        B2[Multiple Character Types]
        B3[Power-ups and Collectibles]
        B4[Level Progression]
    end
    
    B --> B1 & B2 & B3 & B4
```

## Contributing

Feel free to contribute to this project by:
1. Forking the repository
2. Creating a feature branch
3. Committing your changes
4. Opening a pull request

## License

This project is open source and available under the MIT License.

## Credits
- Three.js for 3D rendering engine
- Soldier model from Three.js examples
- Procedurally generated textures for maze elements
