# Part 3 Practice

## What is on this page

Ricky/Windows/Beginner:
- [Ricky's Practice](#rickys-practice)
- Goal is to create a rock, paper, scissors game
- Product: [Finished Product](https://github.com/rckpwr/rock_paper_scissors)

Priya/Mac/Intermediate:
- [Priya's Practice](#priyas-practice)
- Goal is to build a Space Shooter game while learn Pygame
- Product: [Finished Product](https://github.com/priyapower/shooter_game)

## Ricky's Practice
Goal is to create a rock, paper, scissors game
- His theory [notes]()
  - What is OOP
- His project [code](https://github.com/rckpwr/rock_paper_scissors/blob/main/rock_paper_scissors.py)
- His project code [annotations]()

## Priya's Practice
Goal is to build a Space Shooter game while learn PyGame
- [Part 0: Pygame, Arcade, and Crafting Game Code](#part-0)
  1. [Getting to Know Pygame and Arcade](#Getting-to-Know-Pygame-and-Arcade)
  1. [Additional Prereqs](#Additional-Prereqs)
  1. [A Brief Intro to Game Design](#A-Brief-Intro-to-Game-Design)
- [Part 1: Initial Setup](#part-1)
  1. [Project Setup for Pygame](#Project-Setup-for-Pygame)
  1. [Install Pygame](#Install-Pygame)
- [Part 2: Getting to Know Pygame](#part-2)
  1. [Building a Basic Pygame Program](#Building-a-Basic-Pygame-Program)
  1. [Pygame Concepts](#Pygame-Concepts)
- [Part 3: Building the Game](#part-3)
  1. [Importing and Initializing Pygame](#Importing-and-Initializing-Pygame)
  1. [Setting Up the Display](#Setting-Up-the-Display)
  1. [Setting Up the Game Loop](#Setting-Up-the-Game Loop)
  1. [Processing Events](#Processing-Events)
  1. [Drawing on the Screen](#Drawing-on-the-Screen)
  1. [Using blit and flip](#Using-blit-and-flip)
- [Part 4: Interacting with Game Objects](#part-4)
  1. [Sprites](#Sprites)
  1. [Sprite Players](#Sprite-Players)
  1. [Sprite User Input](#Sprite-User-Input)
  1. [Sprite Enemies](#Sprite-Enemies)
  1. [Sprite Groups](#Sprite-Groups)
  1. [Custom Events](#Custom-Events)
  1. [Collision Detection](#Collision-Detection)
  1. [Sprite Images](#Sprite-Images)
  1. [Sprite Altering the Object Constructors](#Sprite-Altering-the-Object-Constructors)
  1. [Sprite Adding Background Images](#Sprite-Adding-Background-Images)
- [Part 5: Adding Fun](#part-5)
  1. [Game Speed](#Game-Speed)
  1. [Sound Effects](#Sound-Effects)
- [Part 6: Final Code](#part-6)
  1. [Final Code](#Final-Code)
  1. [Packaging Code for Easy Execution](#Packaging-Code-for-Easy-Execution)

------
### Part 0
------
#### Getting to Know Pygame and Arcade
[Top](#priyas-practice)

- What is Pygame?
  - https://www.pygame.org/news
  - Pygame is a cross-platform group of `Python` modules whose purpose is to assist in 2D game development
    - Cross-platform: can be used on Windows or Linux or Mac
    - Python: an interpreted, high-level, and general-purpose programming language
      - interpreted: a programming language whose implementations execute instructions directly and freely, without previously compiling a program into machine-language instructions (https://www.geeksforgeeks.org/difference-between-compiled-and-interpreted-language/)
      - high-level: designed to simplify programming since it is removed (abstracted) away from the code used to run your computers processor; these languages have easy syntax or are human readable/writeable (https://techterms.com/definition/high-level_language)
      - general-purpose: programming languages that are used for a variety of software needs; in this case Python is used for desktop applications, web applications, developing complex scientific/numeric applications, and so much more. The opposite would be "special purpose programming languages" or "domain specific language", such as SQL, which is a database query/manipulation language
    - Modules: modules are simply packaged up code in certain languages that can perform a certain function. Using modules allows us to keep our code "DRY" and following Single Responsibility Principle. In the case of Pygame, these modules are written in `C` or `Python` whose behaviors are directly related to game development such as handling user input with keystrokes or mouse or setting window sizes, etc.
- What is Arcade?
  - https://arcade.academy/
  - A more recent python library dedicated to 2D game development. This particular library is aimed at programmers who want to dive into game mechanics and design instead of learning complex frameworks.
  - We will not be using this until [Part 5](lessons/6part_5.md)
- Interested in Other libraries or 3D development, see [here](https://codeboje.de/2d-and-3d-game-and-rendering-engines-python/)

#### Additional Prereqs
[Top](#priyas-practice)

- [Python](https://www.python.org/)
- [PyCharm](https://www.jetbrains.com/pycharm/)
- What is PyCharm
  - PyCharm is a python IDE (integrated development environment)
  - We will not be using this until [Part 5](lessons/6part_5.md)
  - https://www.jetbrains.com/pycharm/
- For this project, I will be using [Atom](https://atom.io), a Mac based IDE. For alternate IDE's and comparisons, check out this [resource](https://stackify.com/top-integrated-developer-environments-ides/)

#### A Brief Intro to Game Design
[Top](#priyas-practice)
- **Our games design:**
  - Goal:
    - The goal is avoid incoming obstacles
    - This game exits the loop when:
      - The player is hit by an obstacle
      - The user manually closes the window
  - Player:
    - A player begins on the left side of the screen
    - Players can move left, right, up, and down
    - Players attempt to avoid obstacles by using the direction commands from above
    - Players cannot move off the screen
  - Obstacles:
    - Obstacles enter from the right (randomly)
    - Obstacles move left and straight
    - Obstacles exit the screen left
- This game tutorial does **NOT** cover:
  - multiple lives
  - scorekeeping
  - player attack capabilities
  - advancing levels
  - boss characters
- More Resources on Game Design:
  - https://www.gamasutra.com/view/feature/132341/the_13_basic_principles_of_.php
  - https://www.cgspectrum.com/blog/what-is-game-design
  - https://www.cgspectrum.com/blog/game-development-process
  - https://hackr.io/blog/how-to-code-a-game


### Part 1
------
#### Project Setup for Pygame
[Top](#priyas-practice)
- We are following this [tutorial](https://realpython.com/pygame-a-primer/)
- Instructions from command line for Mac:
- Make a project directory, I used: `mkdir pygame_shooter_game`
- Enter your directory: `cd <project-space>`
  - For me, this is `cd pygame_shooter_game`
- Make sure you have `Python3` [installed](https://www.python.org/downloads/)
  - Need to confirm, in your terminal run `python3 -V`

#### Install Pygame
[Top](#priyas-practice)
- Inside your project folder, run `pip3 install pygame`
- Terminal output:
  ```console
  Collecting pygame
    Downloading pygame-2.0.1-cp39-cp39-macosx_10_9_intel.whl (6.9 MB)
       |████████████████████████████████| 6.9 MB 880 kB/s
  Installing collected packages: pygame
  Successfully installed pygame-2.0.1
  ```
- Ready for something fun? To verify the install, run `python3 -m pygame.examples.aliens` and see a cute alien game window appear
  - It autoruns while playing music and then autoexits!
- Any [issues?](https://www.pygame.org/wiki/GettingStarted)

### Part 2
------
#### Building a Basic Pygame Program
[Top](#priyas-practice)
- Create a practice file in your directory, `touch practice.py`
- Open this file in whatever editor you prefer (like Atom, VS Code, PyCharm, NotePad)
- Add the following code:
  ```py
  # Simple pygame program

  # Import and initialize the pygame library
  import pygame
  pygame.init()

  # Set up the drawing window
  # .display is a pygame module that lets you control the display window and screen
  # .set_mode is a pygame function that initializes a window/screen for display
  # We have a size argument [500, 500]. A size argument is a pair of numbers representing the width and height.
  screen = pygame.display.set_mode([500, 500])

  # This following sets up a GAME LOOP
  # Run until the user asks to quit
  running = True
  while running:

      # This "for" section scans and handles events
      # Did the user click the window close button?
      # event is a pygame module that interacts with events and queues
      # .get will get events from the queue
      for event in pygame.event.get():
          # is a user triggers the quit event
          if event.type == pygame.QUIT:
              # stop running the program
              running = False

      # Fill the background with white
      # (255, 255, 255) = White for RGB
      screen.fill((255, 255, 255))

      # Draw a solid blue circle in the center
      # (255, 255, 255) = Dark Blue for RGB
      # .draw is a pygame module for drawing shapes
      # .circle draws a circle
      # .circle(a, b, c, d)
      # a = screen = surface to draw on
      # b = (0, 0, 250) = color to draw with
      # c = (250, 250) = center (since our screen is 500, 500, this means our center of the circle is the center of the screen)
      # d = 75 = width of the circle
      pygame.draw.circle(screen, (0, 0, 255), (250, 250), 75)

      # Without this code, nothing would appear in our window
      # Flip the display
      # .flip = Update the full display Surface to the screen
      pygame.display.flip()

  # This happens once the loop is completed
  # Done! Time to quit.
  pygame.quit()
  ```
- Run the program with `python3 practice.py`
- A game screen should pop up that looks like [this](https://files.realpython.com/media/pygame-simple.5169327a10a3.png)
- Take a moment and celebrate your first Pygame success!
- ![Celebrate](https://thumbs.gfycat.com/FrighteningWelltodoCero-max-1mb.gif)

#### Pygame Concepts
[Top](#priyas-practice)
- **Initialization vs Modules**
  - Initialization
    - As easy as using `import pygame` and then `pygame.init()`
    - The above init brings in all modules from pygame
    - You can always call specific init's
    - Allows us to work with pygame in windows, linux, or mac
    - https://www.pygame.org/docs/tut/ImportInit.html
  - Modules
    - List: https://www.pygame.org/docs/py-modindex.html
    - Provides access to specific hardware on system
      - `display` gives access to video display
    - Provides access to methods that work with hardware
      - `joystick` gives access to your joystick controller
- **Displays and Surfaces**
  - Pygame also includes many `Classes` available for use, typically for the non-hardware concepts
  - Surfaces: Defines an area in which you can "draw", it is the canvas on which you design your game or create components for use in your game. It basically represents an image. For more [information](https://www.pygame.org/docs/ref/surface.html)
  - Displays: This is what your user sees and interacts with - the window (or full screen) that the game takes place in. For more [information](https://www.pygame.org/docs/ref/display.html)
- **Images and Rects**
  - Images: yes, we can use our surfaces to draw on, however, what if I have an image I want to use, like a background image or an image for my game character? The images module lets us load, save, and work with images in a variety of ways. For our tutorial, we will use images for the player character, the missile objects, and the floating clouds. For more [information](https://www.pygame.org/docs/ref/image.html)
  - Rects: Since rectangles are a heavily used shape inside game design, pygame created an entire module dedicated to the rectangle class. These `rects` can be used for object creation, character creation, collision physics and logic, and more. For more [information](https://www.pygame.org/docs/ref/rect.html)

### Part 3
------
#### Importing and Initializing Pygame
[Top](#priyas-practice)
- Create a practice file in your project directory, `touch shooter_game.py`
- Open this file in whatever editor you prefer (like Atom, VS Code, PyCharm, NotePad)
- Add the following code:
  ```py
  # Import the pygame module
  import pygame

  # Import pygame.locals for easier access to key coordinates
  # Updated to conform to flake8 and black standards
  # Typically, to call on keystrokes, mouse movements, or display attributes, you would need "pygame.K_UP", but if we import them, we can now use "K_UP" directly
  # This is done for readability, reduce type in code, and DRY concepts
  # See more here: https://www.pygame.org/docs/ref/locals.html
  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )
  # Initialize pygame
  pygame.init()
  ```
- If you run this with `python3 shooter_game.py`, no window will open, but you will see confirmation in the terminal output:
  ```console
  pygame 2.0.1 (SDL 2.0.14, Python 3.9.1)
  Hello from the pygame community. https://www.pygame.org/contribute.html
  ```
- How do we see the window? See next section

#### Setting Up the Display
[Top](#priyas-practice)
- So now we get to be able to "draw" on our game
- Which means we first need a canvas
- UPDATE your code with:
  ```py
  # Import the pygame module
  import pygame

  # Import pygame.locals for easier access to key coordinates
  # Updated to conform to flake8 and black standards
  # Typically, to call on keystrokes, mouse movements, or display attributes, you would need "pygame.K_UP", but if we import them, we can now use "K_UP" directly
  # This is done for readability, reduce type in code, and DRY concepts
  # See more here: https://www.pygame.org/docs/ref/locals.html
  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )
  # Initialize pygame
  pygame.init()

  # Define constants for the screen width and height
  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600

  # Build our "canvas/surface"
  # This surface represents the inside dimensions of the window
  # The screen is going to be what we can control
      # The OS controls the windows borders and title bars
  # Creates the screen object
  # The size is determined by the constant SCREEN_WIDTH and SCREEN_HEIGHT
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
  ```
- If you run this with `python3 shooter_game.py`, a window will _very quickly_ open and close
- How do we prevent the window from exiting before we tell it to? See next section

#### Setting Up the Game Loop
[Top](#priyas-practice)
- All games use game loops to control gameplay
- The point of a game loop is to:
  1. Processes user input
  2. Updates the state of all game objects
  3. Updates the display and audio output
  4. Maintains the speed of the game
- Game loops contain **cycles**
  - The quicker code processes in a cycle, the quicker your game runs
- Cycles contain **frames**
  - Frames run until conditions are met or the game is exited
- Before we can begin coding our game loop, we need a way to capture/process user input. See events below.

#### Processing Events
[Top](#priyas-practice)
- User input results in an **event** being generated
  - Key presses
  - Mouse movement
  - Joystick movement
  - Etc...
- Events are placed in the **event queue**
  - We can access and manipulate events from this queue
- **Handling** events is the act of retrieving/manipulating/etc with them
- **Event handler** is the code designated for handling an event
- Events have **types**
- For our game, we are using:
  - Event: Keypresses => type `KEYDOWN`
  - Event: Window Closure => type `QUIT`
- Some types have other data
- For example, our `KEYDOWN` type has a **variable** called `key` that lets us know which key was pressed
- UPDATE our code with:
  ```py
  # Import the pygame module
  import pygame

  # Import pygame.locals for easier access to key coordinates
  # Updated to conform to flake8 and black standards
  # Typically, to call on keystrokes, mouse movements, or display attributes, you would need "pygame.K_UP", but if we import them, we can now use "K_UP" directly
  # This is done for readability, reduce type in code, and DRY concepts
  # See more here: https://www.pygame.org/docs/ref/locals.html
  from pygame.locals import (
    K_UP,
    K_DOWN,
    K_LEFT,
    K_RIGHT,
    K_ESCAPE,
    KEYDOWN,
    QUIT,
  )
  # Initialize pygame
  pygame.init()

  # Define constants for the screen width and height
  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600

  # Build our "canvas/surface"
  # This surface represents the inside dimensions of the window
  # The screen is going to be what we can control
    # The OS controls the windows borders and title bars
  # Creates the screen object
  # The size is determined by the constant SCREEN_WIDTH and SCREEN_HEIGHT
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Variable to keep the main loop running
  running = True

  # Main Loop
  while running:
    # Look at every event in the queue
    for event in pygame.event.get():
        # Did the user hit a key?
        if event.type == KEYDOWN:
            # Was it the escape key? If so, stop the loop
            if event.key == K_ESCAPE:
                running = False
        # Did the user click the window close button? If so, stop the loop
        elif event.type == QUIT:
            running = False
  ```
- If you run this using `python3 shooter_game.py`, it will open a blank (or black) window that you can now close with `ESC` or manually closing the window
- But why is my window blank (or black)? See drawing on the screen below.


#### Drawing on the Screen
[Top](#priyas-practice)
- In the `practice.py` file we drew using `screen.fill()` (background color) and `pygame.draw.circle()` (drew a circle)
- This time, we are going to learn a new one called `.Surface`
- A **Surface** is a rectangular object that we draw upon (imagine a painters canvas)
- UPDATE our code with:
  ```py
  # Import the pygame module
  import pygame

  # Import pygame.locals for easier access to key coordinates
  # Updated to conform to flake8 and black standards
  # Typically, to call on keystrokes, mouse movements, or display attributes, you would need "pygame.K_UP", but if we import them, we can now use "K_UP" directly
  # This is done for readability, reduce type in code, and DRY concepts
  # See more here: https://www.pygame.org/docs/ref/locals.html
  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )
  # Initialize pygame
  pygame.init()

  # Define constants for the screen width and height
  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600

  # Build our "canvas/surface"
  # This surface represents the inside dimensions of the window
  # The screen is going to be what we can control
      # The OS controls the windows borders and title bars
  # Creates the screen object
  # The size is determined by the constant SCREEN_WIDTH and SCREEN_HEIGHT
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Variable to keep the main loop running
  running = True

  # Main Loop
  while running:
      # Look at every event in the queue
      for event in pygame.event.get():
          # Did the user hit a key?
          if event.type == KEYDOWN:
              # Was it the escape key? If so, stop the loop
              if event.key == K_ESCAPE:
                  running = False
          # Did the user click the window close button? If so, stop the loop
          elif event.type == QUIT:
              running = False

      # Background Color
      # Fill the screen with white
      screen.fill((255, 255, 255))

      # Build a surface
      # Create a surface and pass in a tuple containing its length and width
      # Tuple is a python datatype (similar to List, but it is immutable)
      surf = pygame.Surface((50, 50))

      # Surface Color
      # Give the surface a color to separate it from the background
      # Here we filled it in with black
      surf.fill((0, 0, 0))
      # Access the underlying Rect with ".get_rect()"
      # We stored it as variable "rect" for later use
      rect = surf.get_rect()
  ```
- If you run this using `python3 shooter_game.py`, it will still only open the blank/black window from the previous section. We cannot see the surface object we just created
- Why not? See next section

#### Using blit and flip
[Top](#priyas-practice)
- Making a surface wasn't enough
- We need to **blit** the surface we made onto another surface
- What is a [Blit?](https://www.pygame.org/docs/ref/surface.html#pygame.Surface.blit)
  - Blit, of Block Transfer, is how we officially copy one surface onto another
- We have to be careful with our math B/C `.blit` places our surfaces top-left corner at the location we desire. So to center an object, we have to be aware of this.
- What is [Flip?](https://www.pygame.org/docs/ref/display.html#pygame.display.flip)
  - A flip updates the screen with everything that has been drawn since the last flip
  - Without `.flip()` nothing would show up on the screen
- UPDATE our code with:
  ```py
  # Import the pygame module
  import pygame

  # Import pygame.locals for easier access to key coordinates
  # Updated to conform to flake8 and black standards
  # Typically, to call on keystrokes, mouse movements, or display attributes, you would need "pygame.K_UP", but if we import them, we can now use "K_UP" directly
  # This is done for readability, reduce type in code, and DRY concepts
  # See more here: https://www.pygame.org/docs/ref/locals.html
  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )
  # Initialize pygame
  pygame.init()

  # Define constants for the screen width and height
  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600

  # Build our "canvas/surface"
  # This surface represents the inside dimensions of the window
  # The screen is going to be what we can control
      # The OS controls the windows borders and title bars
  # Creates the screen object
  # The size is determined by the constant SCREEN_WIDTH and SCREEN_HEIGHT
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Variable to keep the main loop running
  running = True

  # Main Loop
  while running:
      # Look at every event in the queue
      for event in pygame.event.get():
          # Did the user hit a key?
          if event.type == KEYDOWN:
              # Was it the escape key? If so, stop the loop
              if event.key == K_ESCAPE:
                  running = False
          # Did the user click the window close button? If so, stop the loop
          elif event.type == QUIT:
              running = False

      # Background Color
      # Fill the screen with white
      screen.fill((255, 255, 255))

      # Build a surface
      # Create a surface and pass in a tuple containing its length and width
      # Tuple is a python datatype (similar to List, but it is immutable)
      surf = pygame.Surface((50, 50))

      # Surface Color
      # Give the surface a color to separate it from the background
      # Here we filled it in with black
      surf.fill((0, 0, 0))
      # Access the underlying Rect with ".get_rect()"
      # We stored it as variable "rect" for later use
      rect = surf.get_rect()

      # USING A BLIT - PART 1

      # This line says "Draw our variable surf onto the screen at the center"
      # .blit(the_surface_to_draw, location_to_draw_on)

      # screen.blit(surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))
      # The above code line was commented out because it doesn't quite center the surf variable
      surf_center = (
          (SCREEN_WIDTH-surf.get_width())/2,
          (SCREEN_HEIGHT-surf.get_height())/2
      )
      screen.blit(surf, surf_center)

      # Updates the screen with everything that has been drawn since the last flip
      pygame.display.flip()
  ```
- If you run this using `python3 shooter_game.py`, it will open a window with your surface object centered
- Take a breath! Great job completing the initial setup of the game!
- ![You did it](https://media1.popsugar-assets.com/files/thumbor/kyO0WEHztvatgj7bkXBCYBqTdGc/fit-in/1024x1024/filters:format_auto-!!-:strip_icc-!!-/2015/09/28/873/n/24155406/83ed51c7_edit_img_cover_file_38578534_1443465783_635653281042964107-565532759_Liz-Lemon-Life-is-Happening-30-Rock/i/Funny-Parenting-Milestones.gif)

### Part 4
------
#### Sprites
[Top](#priyas-practice)
- Moving forward, how do we make the game a game?
- In essence, if we know that our game has obstacles that must appear on the right side of the screen and travel to the left, we know that we can draw them using Surfaces
- HOWEVER, how does the game know where to spawn them? Or what is a collision? Or how does the obstacle exit the screen? Etc, etc, etc
- So we use **[Sprites](https://en.wikipedia.org/wiki/Sprite_%28computer_graphics%29)**
- Sprites are 2D representations of something on our screen
  - Kind of like a picture object
- Pygame gives us a [Sprites class](https://www.pygame.org/docs/ref/sprite.html)
- We can create a Class to define an object (like a Player or User Input or Enemies/Obstacles)
- The class should extend the Sprite Class that will allow our Surface to function with the attributes of the class
- **Let's define some Sprites:**
  - This will go in out `shooter_game.py` file, however, it will **NOT** go at the bottom of the code
  - Instead, we will create our new Classes (that extend from Sprite Class) **above** the `pygame.init()` line
- See next section

#### Sprite Players
[Top](#priyas-practice)
- Let's build a Player Class
- **Reminder - the update will have changed some structuring in the code**
- UPDATE your code like so:
  ```py
  import pygame

  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  # Define a Player Object
      # It extends from Sprite class with pygame.sprite.Sprite
  # The surface drawn on the screen is now an attribute of the "player"
  class Player(pygame.sprite.Sprite):
      def __init__(self):
          # super (https://www.w3schools.com/python/ref_func_super.asp)
          # This is used for Inheritance
          # In this case,, it is so we can use the method "__init__()" from Sprite Class
          super(Player, self).__init__()
          # Create a variable on self called surf
          # define surf as a Surface with length and width of 75
          self.surf = pygame.Surface((75, 25))
          # Fill the surface object as White
          self.surf.fill((255, 255, 255))
          # Create a rect variable for later use
          self.rect = self.surf.get_rect()

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Instantiate a player from the Player Class
      # For now, the player is just a white rectangle
  player = Player()

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:
              if event.key == K_ESCAPE:
                  running = False
          elif event.type == QUIT:
              running = False

      # Filling the window screen as Black
      screen.fill((0, 0, 0))

      # Draw the player on the screen
      # Copy the player surface onto the screen
      screen.blit(player.surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))
        # screen.blit(player.surf, player.rect)
      pygame.display.flip()
  ```
- Now if you run `python3 shooter_game.py`, you should see a black window with a white rectangle approximately center
- If you changed the code `screen.blit(player.surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))` to `screen.blit(player.surf, player.rect)`
  - Your white rectangular "player" now appears in the top left corner of the screen
  - It uses the coordinates of the top-left of the screen
  - This is useful when we are getting ready to make our player move
- So now that we've seen how to add some objects, how do we handle user inputs with our 2D objects? See next section

#### Sprite User Input
[Top](#priyas-practice)
- Let's make our Player object controllable by the user!
- We have already worked on interacting with keyboard events (recall "for" function that ran on `pygame.event` where we said if a user hits `esc` it should exit the game)
- We can also grab keystroke events using `pygame.key.get_pressed()` which will return a `dict` containing all `KEYDOWN` events in a queue
- So we need to:
  - Update our player blit onto screen to use `player.rect`
  - Update "Game Loop" for the `.get_pressed()` info
  - Add a method on our Player Class that tells the Player object how to move based on keystrokes
  - Update "Game Loop" to use the new player class method
  - Put safeguards into the new player method for keeping the player object on the screen
- UPDATE your code like so:
  ```py
  import pygame

  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  # Define a Player Object
      # It extends from Sprite class with pygame.sprite.Sprite
  # The surface drawn on the screen is now an attribute of the "player"
  class Player(pygame.sprite.Sprite):
      def __init__(self):
          # super (https://www.w3schools.com/python/ref_func_super.asp)
          # This is used for Inheritance
          # In this case,, it is so we can use the method "__init__()" from Sprite Class
          super(Player, self).__init__()
          # Create a variable on self called surf
          # define surf as a Surface with length and width of 75
          self.surf = pygame.Surface((75, 25))
          # Fill the surface object as White
          self.surf.fill((255, 255, 255))
          # Create a rect variable for later use
          self.rect = self.surf.get_rect()

      # NEW PLAYER CLASS METHOD
      # This method is defining how the player object moves based on keystrokes
      # This takes in pressed_keys (which is defined in the game loop)
      def update(self, pressed_keys):
          # Every key stroke will go through this method, but only land on 1 if-block
          if pressed_keys[K_UP]:
              # .move_ip is move in place and moves according to the current .rect of the object
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          # Keep player on the screen
          # This is a safeguard to prevent a player object from exiting the screen
              # Only obstacles should be able to leave the screen
              # It basically checks all the sides (left, right, top, bottom) and either resets them to to 0 or resets them to the variables for screen width and height
          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Instantiate a player from the Player Class
      # For now, the player is just a white rectangle
  player = Player()

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

      # UPDATE GAME LOOP
      # Get the set of keys pressed and check for user input
      pressed_keys = pygame.key.get_pressed()

      # Update the player sprite based on user keypresses
      player.update(pressed_keys)

      # Filling the window screen as Black
      screen.fill((0, 0, 0))

      # Draw the player on the screen
      # Copy the player surface onto the screen
      screen.blit(player.surf, player.rect)
          # screen.blit(player.surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))
      pygame.display.flip()
  ```
- Now if you run `python3 shooter_game.py`, you should see a black screen with a white player object in the top-left corner.
  - If you use your arrow keys, you can move the object.
  - AND the object cannot exit the screen.
- Now that we have a player object, what about those obstacles? See next section

#### Sprite Enemies
[Top](#priyas-practice)
- We will use similar concepts as the Player Class
- What we will do:
  - Since we want our Enemy's (Obstacle's) to generate randomly, we need the python native module [`random`](https://docs.python.org/3/library/random.html)
  - We will add a `class Enemy` after the Player Class
- UPDATE your code like so:
  ```py
  import pygame

  # NEW IMPORT
  # Import the random module from Python for random numbers
  import random

  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  # Define a Player Object
      # It extends from Sprite class with pygame.sprite.Sprite
  # The surface drawn on the screen is now an attribute of the "player"
  class Player(pygame.sprite.Sprite):
      def __init__(self):
          # super (https://www.w3schools.com/python/ref_func_super.asp)
          # This is used for Inheritance
          # In this case,, it is so we can use the method "__init__()" from Sprite Class
          super(Player, self).__init__()
          # Create a variable on self called surf
          # define surf as a Surface with length and width of 75
          self.surf = pygame.Surface((75, 25))
          # Fill the surface object as White
          self.surf.fill((255, 255, 255))
          # Create a rect variable for later use
          self.rect = self.surf.get_rect()

      # This method is defining how the player object moves based on keystrokes
      # This takes in pressed_keys (which is defined in the game loop)
      def update(self, pressed_keys):
          # Every key stroke will go through this method, but only land on 1 if-block
          if pressed_keys[K_UP]:
              # .move_ip is move in place and moves according to the current .rect of the object
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          # Keep player on the screen
          # This is a safeguard to prevent a player object from exiting the screen
              # Only obstacles should be able to leave the screen
              # It basically checks all the sides (left, right, top, bottom) and either resets them to to 0 or resets them to the variables for screen width and height
          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  # NEW ENEMY CLASS
  # Define the enemy object by extending pygame.sprite.Sprite
  # The surface you draw on the screen is now an attribute of 'enemy'
  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          # initialize the class as a Sprite
          super(Enemy, self).__init__()
          # build a surface object
          self.surf = pygame.Surface((20, 10))
          # Color it white
          self.surf.fill((255, 255, 255))
          # Define it's .rect
          self.rect = self.surf.get_rect(
              # Math for creating a random generation of the Enemy
              # you update rect to be a random location along the right edge of the screen. The center of the rectangle is just off the screen. It’s located at some position between 20 and 100 pixels away from the right edge, and somewhere between the top and bottom edges.
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          # Sets the speed using a randomizer (how fast the enemy moves towards the player)
          self.speed = random.randint(5, 20)

      # Move the sprite based on speed
      # Remove the sprite when it passes the left edge of the screen
      # This only takes self since the enemies move on their own
      def update(self):
          # Makes the enemy object move left on the screen based on it's set (random) speed
          self.rect.move_ip(-self.speed, 0)
          # If the enemy object moves off screen (the right side of the .rext has gone past the left side of the screen)
          if self.rect.right < 0:
              # .kill will prevent this enemy object from being processed further
              self.kill()

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Instantiate a player from the Player Class
      # For now, the player is just a white rectangle
  player = Player()

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

      # Get the set of keys pressed and check for user input
      pressed_keys = pygame.key.get_pressed()

      # Update the player sprite based on user keypresses
      player.update(pressed_keys)

      # Filling the window screen as Black
      screen.fill((0, 0, 0))

      # Draw the player on the screen
      # Copy the player surface onto the screen
      screen.blit(player.surf, player.rect)
          # screen.blit(player.surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))
      pygame.display.flip()
  ```
- Now if you run `python3 shooter_game.py`, we don't see much change.
- Why don't our enemies appear yet? Well, we first need to understand grouping. See next section

#### Sprite Groups
[Top](#priyas-practice)
- A **Sprite Group** holds a group of sprites
- Why do we use groups?
  - We gain access to Group Methods
  - Use case: it will help us track collisions, updates, etc
- What we will do:
  - Below our instance of `player = Player()`, we will make some groups
    - Now, the enemy class `.kill` makes more sense. When we call .kill, it will remove the enemy object from _every_ group that it belongs to
  - Update how we draw our objects to use our groups instead of a single object declaration
- UPDATE your code like so:
  ```py
  import pygame
  # Import the random module from Python for random numbers
  import random

  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  # Define a Player Object
      # It extends from Sprite class with pygame.sprite.Sprite
  # The surface drawn on the screen is now an attribute of the "player"
  class Player(pygame.sprite.Sprite):
      def __init__(self):
          # super (https://www.w3schools.com/python/ref_func_super.asp)
          # This is used for Inheritance
          # In this case,, it is so we can use the method "__init__()" from Sprite Class
          super(Player, self).__init__()
          # Create a variable on self called surf
          # define surf as a Surface with length and width of 75
          self.surf = pygame.Surface((75, 25))
          # Fill the surface object as White
          self.surf.fill((255, 255, 255))
          # Create a rect variable for later use
          self.rect = self.surf.get_rect()

      # This method is defining how the player object moves based on keystrokes
      # This takes in pressed_keys (which is defined in the game loop)
      def update(self, pressed_keys):
          # Every key stroke will go through this method, but only land on 1 if-block
          if pressed_keys[K_UP]:
              # .move_ip is move in place and moves according to the current .rect of the object
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          # Keep player on the screen
          # This is a safeguard to prevent a player object from exiting the screen
              # Only obstacles should be able to leave the screen
              # It basically checks all the sides (left, right, top, bottom) and either resets them to to 0 or resets them to the variables for screen width and height
          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  # Define the enemy object by extending pygame.sprite.Sprite
  # The surface you draw on the screen is now an attribute of 'enemy'
  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          # initialize the class as a Sprite
          super(Enemy, self).__init__()
          # build a surface object
          self.surf = pygame.Surface((20, 10))
          # Color it white
          self.surf.fill((255, 255, 255))
          # Define it's .rect
          self.rect = self.surf.get_rect(
              # Math for creating a random generation of the Enemy
              # you update rect to be a random location along the right edge of the screen. The center of the rectangle is just off the screen. It’s located at some position between 20 and 100 pixels away from the right edge, and somewhere between the top and bottom edges.
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          # Sets the speed using a randomizer (how fast the enemy moves towards the player)
          self.speed = random.randint(5, 20)

      # Move the sprite based on speed
      # Remove the sprite when it passes the left edge of the screen
      # This only takes self since the enemies move on their own
      def update(self):
          # Makes the enemy object move left on the screen based on it's set (random) speed
          self.rect.move_ip(-self.speed, 0)
          # If the enemy object moves off screen (the right side of the .rext has gone past the left side of the screen)
          if self.rect.right < 0:
              # .kill will prevent this enemy object from being processed further
              self.kill()

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Instantiate a player from the Player Class
      # For now, the player is just a white rectangle
  player = Player()

  # CREATING SPRITE GROUPS
  # Create groups to hold enemy sprites and all sprites

  # - enemies is used for collision detection and position updates
  enemies = pygame.sprite.Group()
  # - all_sprites is used for rendering
  all_sprites = pygame.sprite.Group()
  all_sprites.add(player)

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

      # Get the set of keys pressed and check for user input
      pressed_keys = pygame.key.get_pressed()

      # Update the player sprite based on user keypresses
      player.update(pressed_keys)

      # Filling the window screen as Black
      screen.fill((0, 0, 0))

      # Draw the player on the screen
      # Copy the player surface onto the screen
          # screen.blit(player.surf, player.rect)
          # screen.blit(player.surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))

      # NEW DRAWING USING GROUPS
      # Draw all sprites
      for entity in all_sprites:
          screen.blit(entity.surf, entity.rect)

      pygame.display.flip()
  ```
- UNFORTUNATELY, if you run `python3 shooter_game.py`, we still don't see the changes we are looking for (our enemies)
  - We could hardcode in enemies, but the game wouldn't be fun after the pre-written enemies were done
- So, how do we make dynamic enemies (aka - a steady flow of enemies that only stop when the game exits)? See next section

#### Custom Events
[Top](#priyas-practice)
- We could write in some enemy objects, but instead let's write in a **custom event** that creates those enemy objects for us
- Our custom event should
  - Make a new enemy object
  - Add it to the relevant sprite groups (`all_sprites` and `enemies`)
- What we are going to do:
  - Create a custom event (above our player instantiation)
    -
  - Update our "Event Loop" to handle the custom event
  - Update our "Game Loop" to handle enemy updates
- UPDATE your code like so:
  ```py
  import pygame
  # Import the random module from Python for random numbers
  import random

  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  # Define a Player Object
      # It extends from Sprite class with pygame.sprite.Sprite
  # The surface drawn on the screen is now an attribute of the "player"
  class Player(pygame.sprite.Sprite):
      def __init__(self):
          # super (https://www.w3schools.com/python/ref_func_super.asp)
          # This is used for Inheritance
          # In this case,, it is so we can use the method "__init__()" from Sprite Class
          super(Player, self).__init__()
          # Create a variable on self called surf
          # define surf as a Surface with length and width of 75
          self.surf = pygame.Surface((75, 25))
          # Fill the surface object as White
          self.surf.fill((255, 255, 255))
          # Create a rect variable for later use
          self.rect = self.surf.get_rect()

      # This method is defining how the player object moves based on keystrokes
      # This takes in pressed_keys (which is defined in the game loop)
      def update(self, pressed_keys):
          # Every key stroke will go through this method, but only land on 1 if-block
          if pressed_keys[K_UP]:
              # .move_ip is move in place and moves according to the current .rect of the object
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          # Keep player on the screen
          # This is a safeguard to prevent a player object from exiting the screen
              # Only obstacles should be able to leave the screen
              # It basically checks all the sides (left, right, top, bottom) and either resets them to to 0 or resets them to the variables for screen width and height
          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  # Define the enemy object by extending pygame.sprite.Sprite
  # The surface you draw on the screen is now an attribute of 'enemy'
  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          # initialize the class as a Sprite
          super(Enemy, self).__init__()
          # build a surface object
          self.surf = pygame.Surface((20, 10))
          # Color it white
          self.surf.fill((255, 255, 255))
          # Define it's .rect
          self.rect = self.surf.get_rect(
              # Math for creating a random generation of the Enemy
              # you update rect to be a random location along the right edge of the screen. The center of the rectangle is just off the screen. It’s located at some position between 20 and 100 pixels away from the right edge, and somewhere between the top and bottom edges.
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          # Sets the speed using a randomizer (how fast the enemy moves towards the player)
          self.speed = random.randint(5, 20)

      # Move the sprite based on speed
      # Remove the sprite when it passes the left edge of the screen
      # This only takes self since the enemies move on their own
      def update(self):
          # Makes the enemy object move left on the screen based on it's set (random) speed
          self.rect.move_ip(-self.speed, 0)
          # If the enemy object moves off screen (the right side of the .rext has gone past the left side of the screen)
          if self.rect.right < 0:
              # .kill will prevent this enemy object from being processed further
              self.kill()

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # MAKE A CUSTOM EVENT
  # Create a custom event for adding a new enemy
  # Pygame defines events using integers, so the following code calls on the last pygame event saved (USEREVENT) and adds 1 to ensure a unique id
  ADDENEMY = pygame.USEREVENT + 1
  # This inserts the new event at regular intervals (250 milliseconds, or 4 times in a second)
  pygame.time.set_timer(ADDENEMY, 250) # What would this look like if randomized?

  # Instantiate a player from the Player Class
      # For now, the player is just a white rectangle
  player = Player()

  # Create groups to hold enemy sprites and all sprites
  # - enemies is used for collision detection and position updates
  enemies = pygame.sprite.Group()
  # - all_sprites is used for rendering
  all_sprites = pygame.sprite.Group()
  all_sprites.add(player)

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

          # UPDATE EVENT LOOP WITH CUSTOM EVENT
          # Add a new enemy
          elif event.type == ADDENEMY:
              # Create the new enemy and add it to sprite groups
              new_enemy = Enemy()
              enemies.add(new_enemy)
              all_sprites.add(new_enemy)

      # Get the set of keys pressed and check for user input
      pressed_keys = pygame.key.get_pressed()

      # Update the player sprite based on user keypresses
      player.update(pressed_keys)

      # UPDATE GAME LOOP FOR ENEMY UPDATES
      # Update enemy position for the enemies group
      enemies.update()

      # Filling the window screen as Black
      screen.fill((0, 0, 0))

      # Draw the player on the screen
      # Copy the player surface onto the screen
          # screen.blit(player.surf, player.rect)
          # screen.blit(player.surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))

      # Draw all sprites
      for entity in all_sprites:
          screen.blit(entity.surf, entity.rect)

      pygame.display.flip()
  ```
- FINALLY! Now if you run `python3 shooter_game.py`, we see our enemies!
  - You can move your player object to "avoid" the enemy obstacles
- HOWEVER, when you do "collide" with an enemy, nothing happens... WHY? See next section for collision detection

#### Collision Detection
[Top](#priyas-practice)
- Our game design has a "collision" concept, wherein the player object "hits" a enemy object, they have then collided
- This requires "non-trivial math" that occurs when two sprites overlap each other
- To handwrite collision detection can be cumbersome, so YAY FOR PYGAME
  - Pygame has native [collision detection methods](https://www.pygame.org/docs/ref/sprite.html#pygame.sprite.collide_rect)
- We will be using `.spritecollideany()` or sprite collide any
- What we are doing:
  - Update "Game Loop" (under drawing sprites) for collider logic
- UPDATE your code like so:
  ```py
  import pygame
  # Import the random module from Python for random numbers
  import random

  from pygame.locals import (
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  # Define a Player Object
      # It extends from Sprite class with pygame.sprite.Sprite
  # The surface drawn on the screen is now an attribute of the "player"
  class Player(pygame.sprite.Sprite):
      def __init__(self):
          # super (https://www.w3schools.com/python/ref_func_super.asp)
          # This is used for Inheritance
          # In this case,, it is so we can use the method "__init__()" from Sprite Class
          super(Player, self).__init__()
          # Create a variable on self called surf
          # define surf as a Surface with length and width of 75
          self.surf = pygame.Surface((75, 25))
          # Fill the surface object as White
          self.surf.fill((255, 255, 255))
          # Create a rect variable for later use
          self.rect = self.surf.get_rect()

      # This method is defining how the player object moves based on keystrokes
      # This takes in pressed_keys (which is defined in the game loop)
      def update(self, pressed_keys):
          # Every key stroke will go through this method, but only land on 1 if-block
          if pressed_keys[K_UP]:
              # .move_ip is move in place and moves according to the current .rect of the object
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          # Keep player on the screen
          # This is a safeguard to prevent a player object from exiting the screen
              # Only obstacles should be able to leave the screen
              # It basically checks all the sides (left, right, top, bottom) and either resets them to to 0 or resets them to the variables for screen width and height
          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  # Define the enemy object by extending pygame.sprite.Sprite
  # The surface you draw on the screen is now an attribute of 'enemy'
  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          # initialize the class as a Sprite
          super(Enemy, self).__init__()
          # build a surface object
          self.surf = pygame.Surface((20, 10))
          # Color it white
          self.surf.fill((255, 255, 255))
          # Define it's .rect
          self.rect = self.surf.get_rect(
              # Math for creating a random generation of the Enemy
              # you update rect to be a random location along the right edge of the screen. The center of the rectangle is just off the screen. It’s located at some position between 20 and 100 pixels away from the right edge, and somewhere between the top and bottom edges.
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          # Sets the speed using a randomizer (how fast the enemy moves towards the player)
          self.speed = random.randint(5, 20)

      # Move the sprite based on speed
      # Remove the sprite when it passes the left edge of the screen
      # This only takes self since the enemies move on their own
      def update(self):
          # Makes the enemy object move left on the screen based on it's set (random) speed
          self.rect.move_ip(-self.speed, 0)
          # If the enemy object moves off screen (the right side of the .rext has gone past the left side of the screen)
          if self.rect.right < 0:
              # .kill will prevent this enemy object from being processed further
              self.kill()

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  # Create a custom event for adding a new enemy
  # Pygame defines events using integers, so the following code calls on the last pygame event saved (USEREVENT) and adds 1 to ensure a unique id
  ADDENEMY = pygame.USEREVENT + 1
  # This inserts the new event at regular intervals (250 milliseconds, or 4 times in a second)
  pygame.time.set_timer(ADDENEMY, 250) # What would this look like if randomized?

  # Instantiate a player from the Player Class
      # For now, the player is just a white rectangle
  player = Player()

  # Create groups to hold enemy sprites and all sprites
  # - enemies is used for collision detection and position updates
  enemies = pygame.sprite.Group()
  # - all_sprites is used for rendering
  all_sprites = pygame.sprite.Group()
  all_sprites.add(player)

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

          # UPDATE EVENT LOOP WITH CUSTOM EVENT
          # Add a new enemy
          elif event.type == ADDENEMY:
              # Create the new enemy and add it to sprite groups
              new_enemy = Enemy()
              enemies.add(new_enemy)
              all_sprites.add(new_enemy)

      # Get the set of keys pressed and check for user input
      pressed_keys = pygame.key.get_pressed()

      # Update the player sprite based on user keypresses
      player.update(pressed_keys)

      # Update enemy position for the enemies group
      enemies.update()

      # Filling the window screen as Black
      screen.fill((0, 0, 0))

      # Draw the player on the screen
      # Copy the player surface onto the screen
          # screen.blit(player.surf, player.rect)
          # screen.blit(player.surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))

      # Draw all sprites
      for entity in all_sprites:
          screen.blit(entity.surf, entity.rect)

      # ADD COLLIDER LOGIC
      # Check if any enemies have collided with the player
          # our .spritecollideany is taking on 2 args: player and enemies
      if pygame.sprite.spritecollideany(player, enemies):
          # If so, then remove the player and stop the loop
          player.kill()
          running = False

      pygame.display.flip()
  ```
- Now if you run `python3 shooter_game.py`, we actually experience the collision logic!
  - **NOTE** - my game enemy objects are suuuuuper fast
    - Potential updates:
      - Change `self.speed = random.randint(5, 20)` to `self.speed = random.randint(3, 7)`
      - Change `pygame.time.set_timer(ADDENEMY, 250)` to `pygame.time.set_timer(ADDENEMY, random.randint(250, 600))`
- So now that we have a working game, how do we make it pretty? See next section

#### Sprite Images
[Top](#priyas-practice)
- Let's begin replacing our basic black backgrounds and white objects with images
- We will need some sound clips and images for our player, enemy, and background
  - To grab the ones used in this tutorial, don't forget to download [source code](https://realpython.com/bonus/pygame-sample-code/)
- I added a media folder to my project directory (`mkdir media`) and saved all my media files under this folder
- See next to begin updating code for images

#### Sprite Altering the Object Constructors
[Top](#priyas-practice)
- What we are doing:
  - Update the locals import for RLEACCEL (a constant that helps pygame render more quickly on non-accelerated displays)
  - Update player class for new surface object that imports from file
  - Update enemy class for new surface object that imports from file
- UPDATE your code like so:
  ```py
  import pygame
  import random

  # UPDATE LOCALS
  from pygame.locals import (
      # RLEACCEL is the flag to denote Surface which is RLE encoded
      RLEACCEL,
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  class Player(pygame.sprite.Sprite):
      def __init__(self):
          super(Player, self).__init__()
          # UPDATE PLAYER CLASS WITH NEW SURFACE OBJECT
          # Loads an image from the disk
              # From custom file path
              # And converts for optimization for future .blit calls
          self.surf = pygame.image.load("media/jet.png").convert()
          # Sets a color that pygame will render as transparent (in this case white since the jet.png has a white background)
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect()

      def update(self, pressed_keys):
          if pressed_keys[K_UP]:
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          super(Enemy, self).__init__()
          # UPDATE ENEMY CLASS
          # Load missile image
          self.surf = pygame.image.load("media/missile.png").convert()
          # Set transparent background
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect(
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          self.speed = random.randint(3, 7)

      def update(self):
          self.rect.move_ip(-self.speed, 0)
          if self.rect.right < 0:
              self.kill()

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  ADDENEMY = pygame.USEREVENT + 1
  pygame.time.set_timer(ADDENEMY, random.randint(250, 600))

  player = Player()

  enemies = pygame.sprite.Group()
  all_sprites = pygame.sprite.Group()
  all_sprites.add(player)

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

          elif event.type == ADDENEMY:
              new_enemy = Enemy()
              enemies.add(new_enemy)
              all_sprites.add(new_enemy)

      pressed_keys = pygame.key.get_pressed()

      player.update(pressed_keys)

      enemies.update()

      screen.fill((0, 0, 0))

      for entity in all_sprites:
          screen.blit(entity.surf, entity.rect)

      if pygame.sprite.spritecollideany(player, enemies):
          player.kill()
          running = False

      pygame.display.flip()
  ```
- Now if you run `python3 shooter_game.py`, we see a jet and missiles graphics instead of white blocks!
- But... is it fully pretty? What about a background image? See next section

#### Sprite Adding Background Images
[Top](#priyas-practice)
- We could import a static image as our background
- HOWEVER, why not make our game a little more fun and have clouds floating by
- So... we will make a new class (Cloud Class) that will randomly send cloud objects (a new custom event) to the screen
- What we are doing:
  - Add a new Cloud Class
  - Add custom event for ADDCLOUD
  - Add a group for our clouds
  - Update "Event Loo"p" for custom cloud events
  - Update "Game Loop" for updates on clouds
  - Change background color to sky blue
- UPDATE your code like so:
  ```py
  import pygame
  import random

  from pygame.locals import (
      # RLEACCEL is the flag to denote Surface which is RLE encoded
      RLEACCEL,
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  class Player(pygame.sprite.Sprite):
      def __init__(self):
          super(Player, self).__init__()
          # Loads an image from the disk
              # From custom file path
              # And converts for optimization for future .blit calls
          self.surf = pygame.image.load("media/jet.png").convert()
          # Sets a color that pygame will render as transparent (in this case white since the jet.png has a white background)
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect()

      def update(self, pressed_keys):
          if pressed_keys[K_UP]:
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          super(Enemy, self).__init__()
          # Load missile image
          self.surf = pygame.image.load("media/missile.png").convert()
          # Set transparent background
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect(
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          self.speed = random.randint(3, 7)

      def update(self):
          self.rect.move_ip(-self.speed, 0)
          if self.rect.right < 0:
              self.kill()

  # ADD A NEW CLOUD CLASS
  # Define the cloud object by extending pygame.sprite.Sprite
  # Use an image for a better-looking sprite
  class Cloud(pygame.sprite.Sprite):
      def __init__(self):
          super(Cloud, self).__init__()
          self.surf = pygame.image.load("media/cloud.png").convert()
          self.surf.set_colorkey((0, 0, 0), RLEACCEL)
          # The starting position is randomly generated
          self.rect = self.surf.get_rect(
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
              )
          )
          self.speed = random.randint(1, 5)

      # Move the cloud based on a constant speed
      # Remove the cloud when it passes the left edge of the screen
      def update(self):
          self.rect.move_ip(-self.speed, 0)
          if self.rect.right < 0:
              self.kill()

  pygame.init()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  ADDENEMY = pygame.USEREVENT + 1
  pygame.time.set_timer(ADDENEMY, random.randint(250, 600))

  # ADD CUSTOM EVENT
  ADDCLOUD = pygame.USEREVENT + 2
  pygame.time.set_timer(ADDCLOUD, random.randint(700, 1200))

  # ADD NEW GROUP FOR CLOUDS
  # Create groups to hold enemy sprites, cloud sprites, and all sprites
  player = Player()
  enemies = pygame.sprite.Group()
  # - clouds is used for position updates
  clouds = pygame.sprite.Group()
  all_sprites = pygame.sprite.Group()
  all_sprites.add(player)

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

          elif event.type == ADDENEMY:
              new_enemy = Enemy()
              enemies.add(new_enemy)
              all_sprites.add(new_enemy)

          # UPDATE EVENT LOOP FOR CLOUD EVENT
          # Add a new cloud
          elif event.type == ADDCLOUD:
              # Create a new cloud object from Cloud Class
              new_cloud = Cloud()
              # Add this object to our clouds group
              clouds.add(new_cloud)
              # Add this object to our all_sprites group
              all_sprites.add(new_cloud)

      pressed_keys = pygame.key.get_pressed()
      player.update(pressed_keys)
      enemies.update()
      # ADD CLOUD UPDATES
      clouds.update()

      # CHANGE BACKGROUND COLOR TO SKY BLUE
      screen.fill((135, 206, 250))

      for entity in all_sprites:
          screen.blit(entity.surf, entity.rect)

      if pygame.sprite.spritecollideany(player, enemies):
          player.kill()
          running = False

      pygame.display.flip()
  ```
- Now if you run `python3 shooter_game.py`, we see our beautiful background with custom clouds floating by
- Remember how I handled the enemies passing to quickly? Is that the only thing we can do? See next section

### Part 5
------
#### Game Speed
[Top](#priyas-practice)
- Your game speed is dependent on your local machine
  > The reason for this is that the game loop processes frames as fast as the processor and environment will allow. Since all the sprites move once per frame, they can move hundreds of times each second. The number of frames handled each second is called the frame rate, and getting this right is the difference between a playable game and a forgettable one.
  >
  > -- Real Python Tutorial

- For our code, we need to slow down our frame rate to make this playable for users
- What we are doing:
  - Return our enemy speed range to (5, 20)
  - Update custom events with values that make sense for your framerate
  - Add clock after our initialization of pygame
  - After our .flip, add our custom frame rate selection
- UPDATE your code like so:
  ```py
  import pygame
  import random

  from pygame.locals import (
      # RLEACCEL is the flag to denote Surface which is RLE encoded
      RLEACCEL,
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  class Player(pygame.sprite.Sprite):
      def __init__(self):
          super(Player, self).__init__()
          # Loads an image from the disk
              # From custom file path
              # And converts for optimization for future .blit calls
          self.surf = pygame.image.load("media/jet.png").convert()
          # Sets a color that pygame will render as transparent (in this case white since the jet.png has a white background)
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect()

      def update(self, pressed_keys):
          if pressed_keys[K_UP]:
              self.rect.move_ip(0, -5)
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          super(Enemy, self).__init__()
          # Load missile image
          self.surf = pygame.image.load("media/missile.png").convert()
          # Set transparent background
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect(
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          # RETURNED TO ORIGINAL VALUES
          self.speed = random.randint(5, 20)

      def update(self):
          self.rect.move_ip(-self.speed, 0)
          if self.rect.right < 0:
              self.kill()

  # Define the cloud object by extending pygame.sprite.Sprite
  # Use an image for a better-looking sprite
  class Cloud(pygame.sprite.Sprite):
      def __init__(self):
          super(Cloud, self).__init__()
          self.surf = pygame.image.load("media/cloud.png").convert()
          self.surf.set_colorkey((0, 0, 0), RLEACCEL)
          # The starting position is randomly generated
          self.rect = self.surf.get_rect(
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
              )
          )
          self.speed = random.randint(1, 5)

      # Move the cloud based on a constant speed
      # Remove the cloud when it passes the left edge of the screen
      def update(self):
          self.rect.move_ip(-self.speed, 0)
          if self.rect.right < 0:
              self.kill()

  pygame.init()

  # ADD CLOCK UNDER PYGAME INIT
  # Setup the clock for a decent framerate
  clock = pygame.time.Clock()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  ADDENEMY = pygame.USEREVENT + 1
  # UPDATE CUSTOM EVENT VALUES
  pygame.time.set_timer(ADDENEMY, random.randint(250, 750))

  # UPDATE CUSTOM EVENT VALUES
  ADDCLOUD = pygame.USEREVENT + 2
  pygame.time.set_timer(ADDCLOUD, random.randint(500, 1000))

  # Create groups to hold enemy sprites, cloud sprites, and all sprites
  player = Player()
  enemies = pygame.sprite.Group()
  # - clouds is used for position updates
  clouds = pygame.sprite.Group()
  all_sprites = pygame.sprite.Group()
  all_sprites.add(player)

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

          elif event.type == ADDENEMY:
              new_enemy = Enemy()
              enemies.add(new_enemy)
              all_sprites.add(new_enemy)

          # Add a new cloud
          elif event.type == ADDCLOUD:
              # Create a new cloud object from Cloud Class
              new_cloud = Cloud()
              # Add this object to our clouds group
              clouds.add(new_cloud)
              # Add this object to our all_sprites group
              all_sprites.add(new_cloud)

      pressed_keys = pygame.key.get_pressed()
      player.update(pressed_keys)
      enemies.update()
      clouds.update()

      screen.fill((135, 206, 250))

      for entity in all_sprites:
          screen.blit(entity.surf, entity.rect)

      if pygame.sprite.spritecollideany(player, enemies):
          player.kill()
          running = False

      pygame.display.flip()

      # ADD CUSTOM FRAMERATE
      # Ensure program maintains a rate of 45 frames per second
      clock.tick(45)
  ```
- Now if we run our game with `python3 shooter_game.py`, we will notice the game becoming more playable (change your .tick value if you need faster or slower frame rates on your local maching)
- But what about some music? See next section

#### Sound Effects
[Top](#priyas-practice)
- Pygame gives us [mixer](https://www.pygame.org/docs/ref/mixer.html) that helps us handle sounds
- What we are doing:
  - Initialize mixer _above_ pygames init (The use case for above is to gain access to changing mixer defaults)
  - Load up our music/sound files (for our code, it will go under our object/group initialization)
  - Add sound files to our Player Classe
  - Add sound files to our "Game Loop" collide function
  - Add music exit outside the "Game Loop"
- UPDATE your code like so:
  ```py
  import pygame
  import random

  from pygame.locals import (
      # RLEACCEL is the flag to denote Surface which is RLE encoded
      RLEACCEL,
      K_UP,
      K_DOWN,
      K_LEFT,
      K_RIGHT,
      K_ESCAPE,
      KEYDOWN,
      QUIT,
  )

  class Player(pygame.sprite.Sprite):
      def __init__(self):
          super(Player, self).__init__()
          # Loads an image from the disk
              # From custom file path
              # And converts for optimization for future .blit calls
          self.surf = pygame.image.load("media/jet.png").convert()
          # Sets a color that pygame will render as transparent (in this case white since the jet.png has a white background)
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect()

      def update(self, pressed_keys):
          if pressed_keys[K_UP]:
              self.rect.move_ip(0, -5)
              # ADD SOUND TO PLAYER CLASS
              move_up_sound.play()
          if pressed_keys[K_DOWN]:
              self.rect.move_ip(0, 5)
              # ADD SOUND TO PLAYER CLASS
              move_down_sound.play()
          if pressed_keys[K_LEFT]:
              self.rect.move_ip(-5, 0)
          if pressed_keys[K_RIGHT]:
              self.rect.move_ip(5, 0)

          if self.rect.left < 0:
              self.rect.left = 0
          elif self.rect.right > SCREEN_WIDTH:
              self.rect.right = SCREEN_WIDTH
          if self.rect.top <= 0:
              self.rect.top = 0
          elif self.rect.bottom >= SCREEN_HEIGHT:
              self.rect.bottom = SCREEN_HEIGHT

  class Enemy(pygame.sprite.Sprite):
      def __init__(self):
          super(Enemy, self).__init__()
          # Load missile image
          self.surf = pygame.image.load("media/missile.png").convert()
          # Set transparent background
          self.surf.set_colorkey((255, 255, 255), RLEACCEL)
          self.rect = self.surf.get_rect(
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
             )
          )
          # RETURNED TO ORIGINAL VALUES
          self.speed = random.randint(5, 20)

      def update(self):
          self.rect.move_ip(-self.speed, 0)
          if self.rect.right < 0:
              self.kill()

  # Define the cloud object by extending pygame.sprite.Sprite
  # Use an image for a better-looking sprite
  class Cloud(pygame.sprite.Sprite):
      def __init__(self):
          super(Cloud, self).__init__()
          self.surf = pygame.image.load("media/cloud.png").convert()
          self.surf.set_colorkey((0, 0, 0), RLEACCEL)
          # The starting position is randomly generated
          self.rect = self.surf.get_rect(
              center=(
                  random.randint(SCREEN_WIDTH + 20, SCREEN_WIDTH + 100),
                  random.randint(0, SCREEN_HEIGHT),
              )
          )
          self.speed = random.randint(1, 5)

      # Move the cloud based on a constant speed
      # Remove the cloud when it passes the left edge of the screen
      def update(self):
          self.rect.move_ip(-self.speed, 0)
          if self.rect.right < 0:
              self.kill()

  # INITIALIZE MIXER
  # Setup for sounds. Defaults are good.
  pygame.mixer.init()

  pygame.init()

  # Setup the clock for a decent framerate
  clock = pygame.time.Clock()

  SCREEN_WIDTH = 800
  SCREEN_HEIGHT = 600
  screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

  ADDENEMY = pygame.USEREVENT + 1
  pygame.time.set_timer(ADDENEMY, random.randint(250, 750))

  ADDCLOUD = pygame.USEREVENT + 2
  pygame.time.set_timer(ADDCLOUD, random.randint(500, 1000))

  # Create groups to hold enemy sprites, cloud sprites, and all sprites
  player = Player()
  enemies = pygame.sprite.Group()
  # - clouds is used for position updates
  clouds = pygame.sprite.Group()
  all_sprites = pygame.sprite.Group()
  all_sprites.add(player)

  # LOAD THE MUSIC/SOUNDS
  # Load and play background music
  # Sound source: http://ccmixter.org/files/Apoxode/59262
  # License: https://creativecommons.org/licenses/by/3.0/
  pygame.mixer.music.load("media/Apoxode_-_Electric_1.mp3")
  # loops=-1 tells it to loop the music and never end
  pygame.mixer.music.play(loops=-1)

  # Load all sound files for our effects
  # Sound sources: Jon Fincher
  move_up_sound = pygame.mixer.Sound("media/Rising_putter.ogg")
  move_down_sound = pygame.mixer.Sound("media/Falling_putter.ogg")
  collision_sound = pygame.mixer.Sound("media/Collision.ogg")

  running = True
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:

              if event.key == K_ESCAPE:
                  running = False

          elif event.type == QUIT:
              running = False

          elif event.type == ADDENEMY:
              new_enemy = Enemy()
              enemies.add(new_enemy)
              all_sprites.add(new_enemy)

          # Add a new cloud
          elif event.type == ADDCLOUD:
              # Create a new cloud object from Cloud Class
              new_cloud = Cloud()
              # Add this object to our clouds group
              clouds.add(new_cloud)
              # Add this object to our all_sprites group
              all_sprites.add(new_cloud)

      pressed_keys = pygame.key.get_pressed()
      player.update(pressed_keys)
      enemies.update()
      clouds.update()

      screen.fill((135, 206, 250))

      for entity in all_sprites:
          screen.blit(entity.surf, entity.rect)

      if pygame.sprite.spritecollideany(player, enemies):
          # ADD COLLISION SOUND
          # Stop any moving sounds
          move_up_sound.stop()
          move_down_sound.stop()
          # And play the collision sound
          collision_sound.play()

          player.kill()
          running = False

      pygame.display.flip()

      # Ensure program maintains a rate of 45 frames per second
      clock.tick(45)

  # END ALL SOUND
  # All done! Stop and quit the mixer.
  pygame.mixer.music.stop()
  pygame.mixer.quit()
  ```
- Now if we run our game with `python3 shooter_game.py`, we will get a full working game with sounds!
- **Error Side Note:** My collision sounds aren't playing because it is exiting the game before we can hear it.
- FUTURE: (If I wanted to update this game)
  - I could make an exit function that doesn't close the game, but gives you an option to start over
    - I could establish a starting page
    - I could establish an ending animation (collision)
  - I could add a points tracker
  - I could add "leaderboards"
  - I could add a local Versus option (player 1 plays, then player 2 || player 1 plays, then CPU plays)
  - I could customize my window size, the graphics, sounds, etc
  - I could package this game for easy download/execution by other users

### Part 6
------
#### Final Code
[Top](#priyas-practice)

Code
- [Repo](https://github.com/priyapower/shooter_game)
- [Practice Code](https://github.com/priyapower/shooter_game/blob/main/learning_code_and_annotations/1practice.py)
- [Game Setup](https://github.com/priyapower/shooter_game/blob/main/learning_code_and_annotations/2shooter_game_setup.py)
- [Working Game](https://github.com/priyapower/shooter_game/blob/main/learning_code_and_annotations/3shooter_game_working.py)
- The final code: [Game with Images, Speed, and Sound](https://github.com/priyapower/shooter_game/blob/main/shooter_game_final.py)

Annotations
- [Practice Code Annotations](https://github.com/priyapower/shooter_game/blob/main/learning_code_and_annotations/1practice_annotations.py)
- [Game Setup Annotations](https://github.com/priyapower/shooter_game/blob/main/learning_code_and_annotations/2shooter_game_setup_annotations.py)
- [Working Game Annotations](https://github.com/priyapower/shooter_game/blob/main/learning_code_and_annotations/3shooter_game_working_annotations.py)
- The final code annotations: [Game with Images, Speed, and Sound](https://github.com/priyapower/shooter_game/blob/main/learning_code_and_annotations/4shooter_game_final_annotations.py)


#### Packaging Code for Easy Execution
[Top](#priyas-practice)

Sources for use when ready for this section:
- https://pythonprogramming.net/converting-pygame-executable-cx_freeze/
- https://www.pygame.org/project-pyg.exe-2830-.html
- https://stackoverflow.com/questions/54210392/how-can-i-convert-pygame-to-exe
- https://www.youtube.com/watch?v=BIWqt6NICrw
- https://www.pyinstaller.org
