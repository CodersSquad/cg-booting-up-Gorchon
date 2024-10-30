
---

# Computer Graphics Program - Part 1

This is the first part of a computer graphics 1st task using Python, `moderngl`, and `pygame` to create an animated window.

## Prerequisites

- **Python 3**: Ensure that Python 3/ Python is installed on your system. You can check this by running:
  ```bash
  python3 --versions
  ```
    ```bash
  python --versions
  ```

## Setup

### Step 1: Create and Activate the Virtual Environment (Mac)

1. Open your terminal.
2. Navigate to the project directory  `cg-booting-up-Gorchon `  where `01_hello_world.py` is located.
3. Create a virtual environment:
   ```bash
   python3 -m venv myenv
   ```
   Replace `myenv` with any name you prefer for your environment.
4. Activate the virtual environment:
   ```bash
   source myenv/bin/activate
   ```
   Once activated, your terminal prompt should change to show the environment's name.

### Step 2: Install Dependencies

With the virtual environment activated, install the required packages using `pip`:

```bash
pip install moderngl pygame
```

This will install `moderngl` for OpenGL rendering and `pygame` for creating the window and handling events.

### Step 3: Run the Program

To start the program, run:

```bash
python 01_hello_world.py
```

The program opens an 800x800 pixel window with OpenGL rendering, changing background colors based on sine waves.

## Program Description

This script defines a `Scene` class that uses `moderngl` to manage an OpenGL context and clears the display to a color that changes over time. `pygame` is used to manage the display window and handle events, such as closing the window. The program continuously updates the display until the user exits.

```python
import math
import os
import sys
import moderngl
import pygame

os.environ['SDL_WINDOWS_DPI_AWARENESS'] = 'permonitorv2'

pygame.init()
pygame.display.set_mode((800, 800), flags=pygame.OPENGL | pygame.DOUBLEBUF, vsync=True)

class Scene:
    def __init__(self):
        self.ctx = moderngl.get_context()

    def render(self):
        now = pygame.time.get_ticks() / 1000.0
        r = math.sin(now + 0.0) * 0.5 + 0.5
        g = math.sin(now + 2.1) * 0.5 + 0.5
        b = math.sin(now + 4.2) * 0.5 + 0.5
        self.ctx.clear(r, g, b)

scene = Scene()

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    scene.render()
    pygame.display.flip()
```

## Troubleshooting

If you encounter any errors, ensure you have activated the virtual environment and installed the dependencies. If any issues persist, confirm that `pygame` and `moderngl` are properly installed and compatible with your Python version.





# Computer Graphics Program - Part 2

This is the second part of a computer graphics program that builds on the first by introducing multiple objects with OpenGL, `moderngl`, and `pygame`.

## Prerequisites

- Ensure that **Python 3** is installed on your system.
- Ensure the following packages are installed:
  - `numpy`
  - `moderngl`
  - `pygame`
  - `PyGLM` 



## Setup

### Step 1: Activate the Virtual Environment (Mac)

1. Open your terminal.
2. Navigate to the project directory where `06_multiple_objects.py` is located.
3. Activate the virtual environment you used for Part 1 (if it’s named `myenv`, activate it with this command):
   ```bash
   source myenv/bin/activate
   ```

### Step 2: Install Additional Dependencies

With the virtual environment activated, install the required packages if they are not already installed:

```bash
pip install numpy moderngl pygame PyGLM
```

This will ensure all necessary libraries are available for rendering and managing objects.

### Step 3: Run the Program

To start the program, execute:

```bash
python 06_multiple_objects.py
```

The program will open an 800x800 pixel window, displaying multiple objects rendered in different colors with dynamic positions and transformations.

## Program Description

This script defines a `Scene` class that manages multiple objects rendered with `moderngl`. The program also uses `pygame` for window management and event handling, allowing users to close the window with the `QUIT` event. 

Each object in the scene has:
- Dynamic color and position, which change in real time.
- A camera matrix to provide a 3D perspective.

The `Scene` class handles the setup of the OpenGL context, shaders, and geometry, as well as the `perspective` function for the projection matrix.

### Troubleshooting

If you encounter any errors:
1. Verify that the virtual environment is activated and all dependencies are installed.
2. Confirm that your Python and OpenGL versions are compatible with your system.

