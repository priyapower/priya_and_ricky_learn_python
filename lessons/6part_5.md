# THIS PAGE IS STILL UNDER CONSTRUCTION
---

# Part 5 Practice
----
## What is on this page

Ricky/Windows/Beginner:
- [Ricky's Practice](#rickys-practice)
- Goal is to create a ToDo App with Flask
- Product: [Finished Product]()

Priya/Mac/Intermediate:
- [Priya's Practice](#priyas-practice)
- Goal is to build a 2D side scroller with interactive levels using Arcade
- Product: [Finished Product]()

## Ricky's Practice
Goal is to create a ToDo App with Flask
- His theory [notes]()
- His project [code]()
- His project code [annotations]()

## Priya's Practice
Goal is to build a 2D side scroller with interactive levels using Arcade
- [Part 0: New Information](#part-0)
  1. [Arcade](#Arcade)
  1. [PyCharm](#PyCharm)
  1. [The Tutorial](#The-Tutorial)
- [Part 1: Settup for Arade](#part-1)
  1. [Installing Arcade](#Installing-Arcade)
  1. [Getting to Know PyCharm](#Getting-to-Know-PyCharm)
  1. [What is a Tiled Map Editor](#What-is-a-Tiled-Map-Editor)
- [Part 2: Building the Base Game](#part-2)
  1. [Install and Open a Window](#Install-and-Open-a-Window)
  1. [Add Sprites](#Add-Sprites)
  1. [Add User Control](#Add-User-Control)
  1. [Add Gravity](#Add-Gravity)
  1. [Add Scrolling](#Add-Scrolling)
  1. [Add Coins and Sounds](#Add-Coins-and-Sounds)
  1. [Halfway Demo](#Halfway-Demo)
  1. [Display the Score](#Display-the-Score)
  1. [Use a Map Editor](#Use-a-Map-Editor)
  1. [Multiple Levels and Other Layers](#Multiple-Levels-and-Other-Layers)
  1. [Add Ladders, Properties, and a Moving Platform](#Add-Ladders-Properties-and-a-Moving-Platform)
  1. [Add Character Animations and Better Keyboard Control](#Add-Character Animations-and-Better-Keyboard-Control)
- [Part 3: Adding Physics using Pymunk](#part-3)
  1. [What is Pymunk](#What-is-Pymunk)
- [Part 4: The Final Code](#part-4)
  1. [Final Code](#Final-Code)
  1. [An Executable Program](#An-Executable-Program)

------
### Part 0
------
#### Arcade
[Top](#priyas-practice)
- https://arcade.academy/
- A more recent python library dedicated to 2D game development. This particular library is aimed at programmers who want to dive into game mechanics and design instead of learning complex frameworks.
- BLARG___________________________________

#### Pycharm
[Top](#priyas-practice)
- https://www.jetbrains.com/pycharm/
- PyCharm is a python IDE (integrated development environment)
- BLARG___________________________________

#### The Tutorial
[Top](#priyas-practice)
- [Arcade Simple Tutorial](https://arcade.academy/examples/platform_tutorial/index.html)

### Part 1
------
#### Installing Arcade
[Top](#priyas-practice)
- Python3
  - Mine is currently `3.9.1`, however, I needed to install a lower version for arcade, so now I have `3.8.2` for my virtual environment
  - BLARG___________________________________
- PyCharm
  - BLARG___________________________________
  - https://arcade.academy/installation_mac.html
BLARG___________________________________
- Forked and Cloned the Arcade Template
  - Renamed the folder on my local
    - `mv template arcade_scroller_game`
  - Made a new repo on github
  - To connect to new repo:
    - Had to `git remove rm origin` (confirmed with `git remote -v`)
    - Before I could add my "real" remote
- Confirm directory in PyCharm
  - Opened `arcade_shooter_game` directory in PyCharm
- Virtual Environment Setup through PyCharm
  - ![virtenv](https://user-images.githubusercontent.com/49959312/104354891-23c0e000-54c7-11eb-98c9-4f2366ea119f.png)
  - Create
  - Confirm in background task section in bottom-right
  - Some sort of error with pip:
    ```console
    Collecting arcade
      Using cached arcade-2.5.2-py3-none-any.whl (38.3 MB)
    Collecting numpy==1.19.2
      Using cached numpy-1.19.2.zip (7.3 MB)
      Installing build dependencies: started
      Installing build dependencies: finished with status 'done'
      Getting requirements to build wheel: started
      Getting requirements to build wheel: finished with status 'done'
        Preparing wheel metadata: started
        Preparing wheel metadata: finished with status 'done'
    Collecting pillow~=8.0
      Using cached Pillow-8.1.0-cp39-cp39-macosx_10_10_x86_64.whl (2.2 MB)
    Collecting pyglet<2,>=1.5.11
      Using cached pyglet-1.5.14-py3-none-any.whl (1.1 MB)
    Collecting pymunk~=5.7
      Using cached pymunk-5.7.0-py2.py3-none-macosx_10_13_x86_64.whl (201 kB)
    Collecting cffi!=1.13.1
      Using cached cffi-1.14.4-cp39-cp39-macosx_10_9_x86_64.whl (177 kB)
    Collecting pycparser
      Using cached pycparser-2.20-py2.py3-none-any.whl (112 kB)
    Collecting pytiled-parser==0.9.4a3
      Using cached pytiled_parser-0.9.4a3-py3-none-any.whl (15 kB)
    Collecting attrs
      Using cached attrs-20.3.0-py2.py3-none-any.whl (49 kB)
    Collecting pyyaml~=5.3
      Using cached PyYAML-5.3.1.tar.gz (269 kB)
    Collecting shapely~=1.7
      Using cached Shapely-1.7.1.tar.gz (383 kB)

        ERROR: Command errored out with exit status 1:
         command: /Users/priyapower/.virtualenvs/arcade/bin/python -c 'import sys, setuptools, tokenize; sys.argv[0] = '"'"'/private/var/folders/ll/fyjn36hj0xq19gbf7csdgqq40000gn/T/pip-install-pquyj68e/shapely_7976ee692d0e4e4d85b67fa1af3399d9/setup.py'"'"'; __file__='"'"'/private/var/folders/ll/fyjn36hj0xq19gbf7csdgqq40000gn/T/pip-install-pquyj68e/shapely_7976ee692d0e4e4d85b67fa1af3399d9/setup.py'"'"';f=getattr(tokenize, '"'"'open'"'"', open)(__file__);code=f.read().replace('"'"'\r\n'"'"', '"'"'\n'"'"');f.close();exec(compile(code, __file__, '"'"'exec'"'"'))' egg_info --egg-base /private/var/folders/ll/fyjn36hj0xq19gbf7csdgqq40000gn/T/pip-pip-egg-info-_hx6g7wz
             cwd: /private/var/folders/ll/fyjn36hj0xq19gbf7csdgqq40000gn/T/pip-install-pquyj68e/shapely_7976ee692d0e4e4d85b67fa1af3399d9/
        Complete output (12 lines):
        Failed `CDLL(/Library/Frameworks/GEOS.framework/Versions/Current/GEOS)`
        Failed `CDLL(/opt/local/lib/libgeos_c.dylib)`
        Failed `CDLL(/usr/local/lib/libgeos_c.dylib)`
        Traceback (most recent call last):
          File "<string>", line 1, in <module>
          File "/private/var/folders/ll/fyjn36hj0xq19gbf7csdgqq40000gn/T/pip-install-pquyj68e/shapely_7976ee692d0e4e4d85b67fa1af3399d9/setup.py", line 85, in <module>
            from shapely._buildcfg import geos_version_string, geos_version, \
          File "/private/var/folders/ll/fyjn36hj0xq19gbf7csdgqq40000gn/T/pip-install-pquyj68e/shapely_7976ee692d0e4e4d85b67fa1af3399d9/shapely/_buildcfg.py", line 190, in <module>
            lgeos = load_dll('geos_c', fallbacks=alt_paths)
          File "/private/var/folders/ll/fyjn36hj0xq19gbf7csdgqq40000gn/T/pip-install-pquyj68e/shapely_7976ee692d0e4e4d85b67fa1af3399d9/shapely/_buildcfg.py", line 162, in load_dll
            raise OSError(
        OSError: Could not find library geos_c or load any of its variants ['/Library/Frameworks/GEOS.framework/Versions/Current/GEOS', '/opt/local/lib/libgeos_c.dylib', '/usr/local/lib/libgeos_c.dylib']
        ----------------------------------------
    ERROR: Command errored out with exit status 1: python setup.py egg_info Check the logs for full command output.
    WARNING: You are using pip version 20.3.1; however, version 20.3.3 is available.
    You should consider upgrading via the '/Users/priyapower/.virtualenvs/arcade/bin/python -m pip install --upgrade pip' command.
    ```
  - Potentially, it was a Python version issue. Arcade doesn't currently connect to 3.9.1 ([source](https://stackoverflow.com/questions/65326869/problem-in-installing-arcade-package-in-python))
    - So I installed 3.8
    - Made a new virtual environment with 3.8
    - Reinstalled arcade (either using the prompt when you open `requirements.txt` or my using `pip install arcade` in the Pycharm terminal)
  - SUCCESS!
- If you would like to setup a virtual environment using pip:
  - **DISCLAIMER: The rest of this tutorial assumes you are using Pycharm, a virtual environment from Pycharm, and the terminal inside Pycharm**
  - BLARG___________________________________

#### Getting to Know PyCharm
[Top](#priyas-practice)
- BLARG___________________________________
- https://www.tutorialspoint.com/pycharm/index.htm

#### What is a Tiled Map Editor
[Top](#priyas-practice)
- "Tiled is a 2D level editor that helps you develop the content of your game. Its primary feature is to edit tile maps of various forms, but it also supports free image placement as well as powerful ways to annotate your level with extra information used by the game. Tiled focuses on general flexibility while trying to stay intuitive." ([resource](https://doc.mapeditor.org/en/stable/manual/introduction/))
- To install:
  - https://www.mapeditor.org
  - Click on [download now](https://thorbjorn.itch.io/tiled) at itch.io
  - This pulls up an option to donate, or you can click on the link "No thanks, just take me to the downloads"
  - I downloaded the `Mac OS (Snapshot)` version
    - My downloads wouldn't auto-start, even with pop-up blocker disabled on the page, so I had to click on "Downloads not starting?" and enable alternate downloads
  - Once I had the application downloaded, I moved it into my Applications folder (for Mac users) and went through the process of opening an application that isn't from the App Store or a verified developer ([source](https://support.apple.com/guide/mac-help/open-a-mac-app-from-an-unidentified-developer-mh40616/mac))
  - Now I can officially open `Tiled`!
- Enjoyed this map editor, considering [supporting](https://www.mapeditor.org/donate) the program

### Part 2
------
#### Install and Open a Window
[Top](#priyas-practice)
- First download the [zip](https://arcade.academy/_static/platform_tutorial.zip) and add these files to the project directory
  - New File Tree
  - ![filetree](https://user-images.githubusercontent.com/49959312/104370161-ae133f00-54db-11eb-9291-409d449aa618.png)
  - [Source](https://kenney.nl)
- If the download above fails, please clone my repo]() BLARG___________________________________
- Our Window is going to be **Fixed Size** versus **Resizable** or **Full Screen**
- _We are very lucky_, this tutorial came with some preloaded files:
  - This section works with is `01_open_window.py`
- To test opening a window, open your terminal in Pycharm (this ensures you are still in your virtual environment)
  - Run: `python 01_open_window.py`
  - This should open a blank window with a `cornflower blue` background
  - ![blank window](https://user-images.githubusercontent.com/49959312/104385204-048a7880-54f0-11eb-8e46-ca56921ae85d.png)
- Since we were given starter files, let's try to understand the open_window file (code annotation):
  ```py
  """
  Platformer Game
  """
  # Imports arcade library
  import arcade

  # Constants needed for this file
  # These represent our fixed window screen
  SCREEN_WIDTH = 1000
  SCREEN_HEIGHT = 650
  SCREEN_TITLE = "Platformer"

  # Creates a MyGame Class that passes the arcade Window class
  # (The Window class forms the basis of most advanced games that use Arcade. It represents a window on the screen, and manages events.)
  class MyGame(arcade.Window):
      """
      Main application class.
      """

      # Initializes this class
      def __init__(self):

          # Call the parent class (Window Class from arcade) and set up the window based on the constants from above
          super().__init__(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)

          # This lets us set a background color, specifically using the CSS color schemes, selecting cornflower_blue
          arcade.set_background_color(arcade.csscolor.CORNFLOWER_BLUE)

      # This will eventually hold our setup
      def setup(self):
          """ Set up the game here. Call this function to restart the game. """
          pass

      # This will eventually hold our drawing functions
      def on_draw(self):
          """ Render the screen. """

          # Get Arcade to actually do some of the drawing commands that we issue
          arcade.start_render()
          # Code to draw the screen goes here

  # This function is outside the MyGame class so that it can call an instance of that class
  def main():
      """ Main method """
      # Call an instance of the MyGame class and set it to the variable "window"
      window = MyGame()
      # Call the .setup function from MyGame class
      window.setup()
      # Run the app
      arcade.run()

  if __name__ == "__main__":
      main()
  ```
- Things to practice:
  1. Change the screen size
    - I updated my constants and see the screen size change when I open the window (run `python 01_open_window.py`)
      ```py
      SCREEN_WIDTH = 1200
      SCREEN_HEIGHT = 1200
      ```
  2. Change the title
    - I updated my constants and see the window title change when I open the window
      ```py
      SCREEN_TITLE = "Priya's 2D FunHouse"
      ```
  3. Change the background color
    - See the documentation for [arcade.color package](https://arcade.academy/arcade.color.html#color)
    - See the documentation for [arcade.csscolor package](https://arcade.academy/arcade.csscolor.html#csscolor)
    - I updated the section that sets background color and see the color change when I open the window
      ```py
      arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)
      ```
  4. Make a [Resizable Window](https://arcade.academy/examples/resizable_window.html#resizable-window)
    - Lots of updates were necessary to make this code run:
      ```py
      """
      Platformer Game
      """
      import arcade

      SCREEN_WIDTH = 600
      SCREEN_HEIGHT = 600
      SCREEN_TITLE = "Priya's 2D Funhouse"
      # Resizeable window
      START = 0
      END = 2000
      STEP = 50

      class MyGame(arcade.Window):
          """
          Main application class.
          """

          # Now the initialize can take in width, height, and title
          def __init__(self, width, height, title):
              # the Windows class initialization sets resizable to true
              super().__init__(width, height, title, resizable=True)

              arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

          def on_resize(self, width, height):
              """ This method is automatically called when the window is resized. """

              # Call the parent. Failing to do this will mess up the coordinates, and default to 0,0 at the center and the
              # edges being -1 to 1.
              super().on_resize(width, height)

              print(f"Window resized to: {width}, {height}")

          def on_draw(self):
              """ Render the screen. """

              arcade.start_render()

              # The following is to visually see the resize happening because it basically creates Quadrant I of the Cartesean Plane with increments by 50

              # Draw the y labels
              i = 0
              for y in range(START, END, STEP):
                  arcade.draw_point(0, y, arcade.color.BLUE, 5)
                  arcade.draw_text(f"{y}", 5, y, arcade.color.BLACK, 12, anchor_x="left", anchor_y="bottom")
                  i += 1

              # Draw the x labels.
              i = 1
              for x in range(START + STEP, END, STEP):
                  arcade.draw_point(x, 0, arcade.color.BLUE, 5)
                  arcade.draw_text(f"{x}", x, 5, arcade.color.BLACK, 12, anchor_x="left", anchor_y="bottom")
                  i += 1

      def main():
          MyGame(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)
          arcade.run()

      if __name__ == "__main__":
          main()
      ```
    - The image below shows my resizable window with terminal output as it changes
    - ![Resized Window](https://user-images.githubusercontent.com/49959312/104385170-f89eb680-54ef-11eb-8eec-a7bfbefb5ff0.png)
  5. Make a Window with [Full Screen Options](https://arcade.academy/examples/full_screen_example.html#full-screen-example)
    - I updated the section that sets background color and see the color change when I open the window
      ```py
      """
      Platformer Game
      """
      import arcade
      # Imports os from python (operating system interfaces)
      import os

      SCREEN_WIDTH = 800
      SCREEN_HEIGHT = 600
      SCREEN_TITLE = "Priya's 2D Funhouse - Full Screen"

      # Possible Sprite constant
      SPRITE_SCALING = 0.5
      # How many pixels to keep as a minimum margin between the character and the edge of the screen.
      VIEWPORT_MARGIN = 40
      MOVEMENT_SPEED = 5

      class MyGame(arcade.Window):
          """ Main application class. """

          def __init__(self):
              """
              Initializer
              """
              # Open a window in full screen mode. Remove fullscreen=True if
              # you don't want to start this way.
              super().__init__(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE, fullscreen=True)

              # Set the working directory (where we expect to find files) to the same
              # directory this .py file is in. You can leave this out of your own
              # code, but it is needed to easily run the examples using "python -m"
              # as mentioned at the top of this program.
              file_path = os.path.dirname(os.path.abspath(__file__))
              os.chdir(file_path)

              # This will get the size of the window, and set the viewport to match.
              # So if the window is 1000x1000, then so will our viewport. If
              # you want something different, then use those coordinates instead.
              width, height = self.get_size()
              self.set_viewport(0, width, 0, height)
              arcade.set_background_color(arcade.color.FLIRT)
              self.example_image = arcade.load_texture(":resources:images/tiles/boxCrate_double.png")

          def on_draw(self):
              """
              Render the screen.
              """

              arcade.start_render()

              # Get viewport dimensions
              left, screen_width, bottom, screen_height = self.get_viewport()

              text_size = 18
              # Draw text on the screen so the user has an idea of what is happening
              arcade.draw_text("Press F to toggle between full screen and windowed mode, unstretched.",
                               screen_width // 2, screen_height // 2 - 20,
                               arcade.color.WHITE, text_size, anchor_x="center")
              arcade.draw_text("Press S to toggle between full screen and windowed mode, stretched.",
                               screen_width // 2, screen_height // 2 + 20,
                               arcade.color.WHITE, text_size, anchor_x="center")

              # Draw some boxes on the bottom so we can see how they change
              for x in range(64, 800, 128):
                  y = 64
                  width = 128
                  height = 128
                  arcade.draw_texture_rectangle(x, y, width, height, self.example_image)

          def on_key_press(self, key, modifiers):
              """Called whenever a key is pressed. """
              if key == arcade.key.F:
                  # User hits f. Flip between full and not full screen.
                  self.set_fullscreen(not self.fullscreen)

                  # Get the window coordinates. Match viewport to window coordinates
                  # so there is a one-to-one mapping.
                  width, height = self.get_size()
                  self.set_viewport(0, width, 0, height)

              if key == arcade.key.S:
                  # User hits s. Flip between full and not full screen.
                  self.set_fullscreen(not self.fullscreen)

                  # Instead of a one-to-one mapping, stretch/squash window to match the
                  # constants. This does NOT respect aspect ratio. You'd need to
                  # do a bit of math for that.
                  self.set_viewport(0, SCREEN_WIDTH, 0, SCREEN_HEIGHT)

      def main():
          """ Main method """
          MyGame()
          arcade.run()

      if __name__ == "__main__":
          main()
      ```
    - The image below shows my resizable window with terminal output as it changes
    - ![Full Screen Window](https://user-images.githubusercontent.com/49959312/104387776-11f63180-54f5-11eb-8f12-0ecef2e6c2a1.png)
  6. **LOOKING FOR MORE?** See the documentation for the [Window](https://arcade.academy/arcade.html#arcade.Window) class to get an idea of everything it can do.
- Now that we've got a basic window setup, let's add some sprites

#### Add Sprites
[Top](#priyas-practice)
- Recall that [Sprites](https://gamingshift.com/sprites-in-games/) are 2D images/animations we can use. They may represent a player, enemies, background imagery, objects that players interact with, etc...
- For this tutorial, we are building off the original, fixed-size window
- In fact, we have a starter file for ourselves called `02_draw_sprites.py` that we can play around with
- When I run it, I see our lovely blue background window with static images of a player on some sort of walkway and three crates
- ![original sprite](https://user-images.githubusercontent.com/49959312/104391177-94362400-54fc-11eb-8b0e-c809dfd0ebe4.png)
- To fully understand this code, let's annotate it:
  ```py
  """
  Platformer Game
  """
  import arcade

  # Constants
  SCREEN_WIDTH = 1000
  SCREEN_HEIGHT = 650
  SCREEN_TITLE = "Priya's 2D Funhouse"

  # Constants used to scale our sprites from their original size
  CHARACTER_SCALING = 1
  TILE_SCALING = 0.5
  COIN_SCALING = 0.5

  class MyGame(arcade.Window):
      """
      Main application class.
      """

      # The __init__ creates the variables.
      def __init__(self):

          # Call the parent class and set up the window
          super().__init__(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)

          # These are 'lists' that keep track of our sprites. Each sprite should
          # go into a list.
          # The None keyword is used to define a null value, or no value at all.
          # Basically, we are just setting up these variables on self, but they currently have no value

          # For coins we pick up
          self.coin_list = None
          # For walls we can't move through
          self.wall_list = None
          # For our player
          self.player_list = None
          # Separate variable that holds the single player sprite
          self.player_sprite = None
          # We are still filling in background color with a pretty purple/red/pink color
          arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

      # The setup actually creates the object instances, such as graphical sprites.
      # WHY keep init separate from setup?
          # With a setup method split out, later on we can easily add “restart/play again” functionality to the game.
          # A simple call to setup will reset everything.
          # Later, we can expand our game with different levels, and have functions such as setup_level_1 and setup_level_2.
      def setup(self):
          """ Set up the game here. Call this function to restart the game. """
          # Create the Sprite lists
          # The player_list saves the entire SpriteList()
          # The SpriteList class optimizes drawing, movement, and collision detection.
          self.player_list = arcade.SpriteList()
          # The wall_list and coin_list use spatial hashing
          # Spatial hashing speeds the time it takes to find collisions, but increases the time it takes to move a sprite.
          # Since we don’t expect the walls or coins to move, we'll turn on spatial hashing for these lists.
          # This doesn't apply to player because a player will move a lot
          self.wall_list = arcade.SpriteList(use_spatial_hash=True)
          self.coin_list = arcade.SpriteList(use_spatial_hash=True)

          # Set up the player, specifically placing it at these coordinates.
          # Our resource lives in the images folder
          # The optional second parameter will scale the sprite up or down
              # Example: if scaling is set to 0.5, and the the sprite is 128x128, then both width and height will be scaled down 50% for a 64x64 sprite.
          self.player_sprite = arcade.Sprite(":resources:images/animated_characters/female_adventurer/femaleAdventurer_idle.png",
                                             CHARACTER_SCALING)
          # Where is the sprite on the screen?
          # Options for setting:
              # Sprite attribute center_x and center_y (https://arcade.academy/arcade.html?highlight=sprite%20top#arcade.Sprite.top)
              # Sprite attribute top, bottom, left, and right (https://arcade.academy/arcade.html?highlight=sprite%20top#arcade.Sprite.top)
              # Sprite attribute position (https://arcade.academy/arcade.html?highlight=sprite%20top#arcade.Sprite.top)
          self.player_sprite.center_x = 64
          self.player_sprite.center_y = 128
          # Add the player_sprite to the player_list
          self.player_list.append(self.player_sprite)

          # Create the ground
          # This shows using a loop to place multiple sprites horizontally
              # This range is static, how would we update this for a resizable window?
          for x in range(0, 1250, 64):
              # Grab the wall picture from our images folder
              # Set scaling
              wall = arcade.Sprite(":resources:images/tiles/grassMid.png", TILE_SCALING)
              # Set the x value to be dynamic for the loop
              wall.center_x = x
              # Set the y value to be static (the ground will only be so tall)
              wall.center_y = 32
              # Add this wall sprite to the wall list
              self.wall_list.append(wall)

          # Put some crates on the ground
          # This shows using a coordinate list to place sprites
          # This is static information - how would this be updated if we had a resizable window?
          coordinate_list = [[256, 96],
                             [512, 96],
                             [768, 96]]

          # For each coordinate in the list above
          for coordinate in coordinate_list:
              # Add a crate on the ground
              wall = arcade.Sprite(":resources:images/tiles/boxCrate_double.png", TILE_SCALING)
              # This uses position which takes both an x and y
              wall.position = coordinate
              # Add this crate sprite to the wall list
              self.wall_list.append(wall)

      def on_draw(self):
          """ Render the screen. """

          # Clear the screen to the background color
          arcade.start_render()

          # Draw our sprites
          self.wall_list.draw()
          self.coin_list.draw()
          self.player_list.draw()

  def main():
      """ Main method """
      window = MyGame()
      window.setup()
      arcade.run()

  if __name__ == "__main__":
      main()
  ```
- Things you can attempt with this code:
  1. Adjust the code and try putting sprites in new positions.   ||   Use different images for sprites (see the images folder).
    ```py
    # Make these changes in def setup
    # UPDATE IMAGES
    self.player_sprite1 = arcade.Sprite("images/player_1/player_stand.png",
                                        CHARACTER_SCALING)
    # ADD A SECOND PLAYER
    self.player_sprite2 = arcade.Sprite("images/player_2/player_stand.png",
                                        CHARACTER_SCALING)
    # NEW POSITION FOR PLAYERS
    self.player_sprite1.position = (256, 180)
    self.player_sprite2.position = (512, 195)
    self.player_list.append(self.player_sprite1)
    self.player_list.append(self.player_sprite2)
    ```
    ![Updated sprite](https://user-images.githubusercontent.com/49959312/104391100-69e46680-54fc-11eb-8af9-c29377ddf11a.png)

  2. Practice placing individually, via a loop, and by coordinates in a list.
  3. **LOOKING FOR MORE?** See the [Sprite Class](https://arcade.academy/arcade.html#arcade.Sprite) and the [Sprite List Class](https://arcade.academy/arcade.html#arcade.SpriteList)
- Now that we can now add sprites to our screen, how do we move them?

#### Add User Control
[Top](#priyas-practice)
- DEETS
- In fact, we have a starter file for ourselves called `03_user_control.py` that we can play around with
- When I run it, I see the same game file as the last section, HOWEVER, now I can move my player!
- To fully understand this code, let's annotate it:
  ```py
  """
  Platformer Game
  """
  import arcade

  SCREEN_WIDTH = 1000
  SCREEN_HEIGHT = 650
  SCREEN_TITLE = "Platformer"

  CHARACTER_SCALING = 1
  TILE_SCALING = 0.5
  COIN_SCALING = 0.5

  # Movement speed of player, in pixels per frame
  PLAYER_MOVEMENT_SPEED = 5

  class MyGame(arcade.Window):
      """
      Main application class.
      """

      def __init__(self):
          super().__init__(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)

          self.coin_list = None
          self.wall_list = None
          self.player_list = None
          self.player_sprite = None

          # Our physics engine
          # Currently it is just a variable, but the engine will be set below
          self.physics_engine = None

          arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

      def setup(self):
          """ Set up the game here. Call this function to restart the game. """
          self.player_list = arcade.SpriteList()
          self.wall_list = arcade.SpriteList(use_spatial_hash=True)
          self.coin_list = arcade.SpriteList(use_spatial_hash=True)

          self.player_sprite = arcade.Sprite(":resources:images/animated_characters/female_adventurer/femaleAdventurer_idle.png",
                                             CHARACTER_SCALING)
          self.player_sprite.center_x = 64
          self.player_sprite.center_y = 128
          self.player_list.append(self.player_sprite)

          for x in range(0, 1250, 64):
              wall = arcade.Sprite(":resources:images/tiles/grassMid.png", TILE_SCALING)
              wall.center_x = x
              wall.center_y = 32
              self.wall_list.append(wall)

          # Create the 'physics engine'
          # https://arcade.academy/arcade.html#arcade.PhysicsEngineSimple
              # Simplistic physics engine for use in games without gravity, such as top-down games.
              # It is easier to get started with this engine than more sophisticated engines like PyMunk.
              # Note, it does not currently handle rotation.
          # This engine is what keeps our player from being able to walk through walls or solid objects or fall through the ground
          # Noticed that I can walk off the edge of the screen, so that safeguard isn't in place yet
              # The PhysicsEngineSimple class takes two parameters: The moving sprite, and a list of sprites the moving sprite can’t move through.
              # So we either need to set another engine with params for the edges, or there is another method coming later
              # We are allowed to have more than one simple physics engine
          self.physics_engine = arcade.PhysicsEngineSimple(self.player_sprite, self.wall_list)

          # Put some crates on the ground
          # This shows using a coordinate list to place sprites
          coordinate_list = [[256, 96],
                             [512, 96],
                             [768, 96]]

          for coordinate in coordinate_list:
              # Add a crate on the ground
              wall = arcade.Sprite(":resources:images/tiles/boxCrate_double.png", TILE_SCALING)
              wall.position = coordinate
              self.wall_list.append(wall)

      def on_draw(self):
          """ Render the screen. """

          # Clear the screen to the background color
          arcade.start_render()

          # Draw our sprites
          self.wall_list.draw()
          self.coin_list.draw()
          self.player_list.draw()

      # on_key_press: https://arcade.academy/arcade.html#arcade.View.on_key_press
      def on_key_press(self, key, modifiers):
          """Called whenever a key is pressed. """
          # If a user presses Up, W, or Space
          if key == arcade.key.UP or key == arcade.key.W or key == arcade.key.SPACE:
              # change_y: https://arcade.academy/arcade.html?highlight=change_y#arcade.Sprite.change_y
              # Increases the velocity in the y-plane by the players set speed
              self.player_sprite.change_y = PLAYER_MOVEMENT_SPEED
          # If a user presses Down or S
          elif key == arcade.key.DOWN or key == arcade.key.S:
              # Decreases the velocity in the y-plane by the players set speed
              self.player_sprite.change_y = -PLAYER_MOVEMENT_SPEED
          # If a user presses Left or A
          elif key == arcade.key.LEFT or key == arcade.key.A:
              # change_x: https://arcade.academy/arcade.html?highlight=change_y#arcade.Sprite.change_x
              # Decreases the velocity in the x-plane by the players set speed
              self.player_sprite.change_x = -PLAYER_MOVEMENT_SPEED
          # If a user presses Right or D
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              # Increases the velocity in the x-plane by the players set speed
              self.player_sprite.change_x = PLAYER_MOVEMENT_SPEED

      # on_key_release: https://arcade.academy/arcade.html#arcade.View.on_key_release
      def on_key_release(self, key, modifiers):
          """Called when the user releases a key. """
          # This allows a user to press and hold a key because if you release the key, it will reset the velocity to 0
          if key == arcade.key.UP or key == arcade.key.W:
              self.player_sprite.change_y = 0
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.player_sprite.change_y = 0
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.player_sprite.change_x = 0
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.player_sprite.change_x = 0

      # on_update: https://arcade.academy/arcade.html?highlight=on_update#arcade.Sprite.on_update
      def on_update(self, delta_time):
          """ Movement and game logic """
          # Move the player with the physics engine
          self.physics_engine.update()

  def main():
      """ Main method """
      window = MyGame()
      window.setup()
      arcade.run()

  if __name__ == "__main__":
      main()
  ```
- Awesome, let's play with this bit of code
  1. Our player can fly off the screen && some key strokes interfere with each (_If the player hits both left and right keys at the same time, then lets off the left one, we expect the player to move right. This method won’t support that._).
    - If you want a slightly more complex method that does, see [Better Move By Keyboard](https://arcade.academy/examples/sprite_move_keyboard_better.html#sprite-move-keyboard-better).
    - The above information also covers preventing the user from falling off the edge of the screen
    - My updated code (my player no longer flies off the screen and my keystrokes don't interfere!):
      ```py
      """
      Platformer Game
      """
      import arcade

      SCREEN_WIDTH = 1000
      SCREEN_HEIGHT = 650
      SCREEN_TITLE = "Platformer"

      CHARACTER_SCALING = 1
      TILE_SCALING = 0.5
      COIN_SCALING = 0.5

      PLAYER_MOVEMENT_SPEED = 5

      # Our player is now an entire Class
      class Player(arcade.Sprite):

          def update(self):
              """ Move the player """
              # Move player.
              # Remove these lines if physics engine is moving player.
              self.center_x += self.change_x
              self.center_y += self.change_y

              # Check for out-of-bounds
              if self.left < 0:
                  self.left = 0
              elif self.right > SCREEN_WIDTH - 1:
                  self.right = SCREEN_WIDTH - 1

              if self.bottom < 0:
                  self.bottom = 0
              elif self.top > SCREEN_HEIGHT - 1:
                  self.top = SCREEN_HEIGHT - 1

      class MyGame(arcade.Window):
          """
          Main application class.
          """

          def __init__(self, width, height, title):
              super().__init__(width, height, title)

              self.coin_list = None
              self.wall_list = None
              self.player_list = None
              self.player_sprite = None
              self.physics_engine = None

              # Track the current state of what key is pressed
              self.left_pressed = False
              self.right_pressed = False
              self.up_pressed = False
              self.down_pressed = False

              arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

          def setup(self):
              """ Set up the game here. Call this function to restart the game. """
              self.player_list = arcade.SpriteList()
              self.wall_list = arcade.SpriteList(use_spatial_hash=True)
              self.coin_list = arcade.SpriteList(use_spatial_hash=True)

              # Changes which class it calls from arcade.Sprite() to Player()
              self.player_sprite = Player(":resources:images/animated_characters/female_adventurer/femaleAdventurer_idle.png",
                                                 CHARACTER_SCALING)
              self.player_sprite.center_x = 64
              self.player_sprite.center_y = 128
              self.player_list.append(self.player_sprite)

              for x in range(0, 1250, 64):
                  wall = arcade.Sprite(":resources:images/tiles/grassMid.png", TILE_SCALING)
                  wall.center_x = x
                  wall.center_y = 32
                  self.wall_list.append(wall)

              self.physics_engine = arcade.PhysicsEngineSimple(self.player_sprite, self.wall_list)

              coordinate_list = [[256, 96],
                                 [512, 96],
                                 [768, 96]]

              for coordinate in coordinate_list:
                  wall = arcade.Sprite(":resources:images/tiles/boxCrate_double.png", TILE_SCALING)
                  wall.position = coordinate
                  self.wall_list.append(wall)

          def on_draw(self):
              """ Render the screen. """
              arcade.start_render()

              self.wall_list.draw()
              self.coin_list.draw()
              self.player_list.draw()

          def on_key_press(self, key, modifiers):
              """Called whenever a key is pressed. """

              if key == arcade.key.UP or key == arcade.key.W or key == arcade.key.SPACE:
                  self.up_pressed = True
              elif key == arcade.key.DOWN or key == arcade.key.S:
                  self.down_pressed = True
              elif key == arcade.key.LEFT or key == arcade.key.A:
                  self.left_pressed = True
              elif key == arcade.key.RIGHT or key == arcade.key.D:
                  self.right_pressed = True

          def on_key_release(self, key, modifiers):
              """Called when the user releases a key. """

              if key == arcade.key.UP or key == arcade.key.W:
                  self.up_pressed = False
              elif key == arcade.key.DOWN or key == arcade.key.S:
                  self.down_pressed = False
              elif key == arcade.key.LEFT or key == arcade.key.A:
                  self.left_pressed = False
              elif key == arcade.key.RIGHT or key == arcade.key.D:
                  self.right_pressed = False

          def on_update(self, delta_time):
              """ Movement and game logic """

              # Calculate speed based on the keys pressed
              self.player_sprite.change_x = 0
              self.player_sprite.change_y = 0

              if self.up_pressed and not self.down_pressed:
                  self.player_sprite.change_y = PLAYER_MOVEMENT_SPEED
              elif self.down_pressed and not self.up_pressed:
                  self.player_sprite.change_y = -PLAYER_MOVEMENT_SPEED
              if self.left_pressed and not self.right_pressed:
                  self.player_sprite.change_x = -PLAYER_MOVEMENT_SPEED
              elif self.right_pressed and not self.left_pressed:
                  self.player_sprite.change_x = PLAYER_MOVEMENT_SPEED

              # Call update to move the sprite
              # If using a physics engine, call update player to rely on physics engine
              # for movement, and call physics engine here.
              self.player_list.update()
              self.physics_engine.update()

      def main():
          """ Main method """
          window = MyGame(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)
          window.setup()
          arcade.run()

      if __name__ == "__main__":
          main()
      ```
  2. **LOOKING FOR MORE?**
    - The Arcade Docs go into more detail about [User Control](http://learn.arcade.academy/chapters/16_user_control/user_control.html#)
- Now that we can control our user, how about some gravity to prevent our user from flying!

#### Add Gravity
[Top](#priyas-practice)
- ![gravity](https://media2.giphy.com/media/3ov9k4e03yTNRWTgYM/giphy.gif)
- Using our starter file: `04_add_gravity.py`
- When I run it, and move my player, especially when I press Up, my character now experiences gravity and must fall back down to the ground!
- The current file doesn't update for better user_control, so I am going to merge the exploration file from the last section with our current gravity file. See this code in the annotations section below.
- To fully understand this code, let's annotate it:
  ```py
  """
  Platformer Game
  """
  import arcade

  SCREEN_WIDTH = 1000
  SCREEN_HEIGHT = 650
  SCREEN_TITLE = "Priya's 2D Funhouse"

  CHARACTER_SCALING = 1
  TILE_SCALING = 0.5
  COIN_SCALING = 0.5

  PLAYER_MOVEMENT_SPEED = 5
  # New constant for gravity
  GRAVITY = 1
  # New constant for player_jump_speed
  PLAYER_JUMP_SPEED = 20

  class Player(arcade.Sprite):
      # Creates boundaries so the player doesn't walk off the edge of the screen
      def update(self):
          """ Move the player """
          if self.left < 0:
              self.left = 0
          elif self.right > SCREEN_WIDTH - 1:
              self.right = SCREEN_WIDTH - 1

          if self.bottom < 0:
              self.bottom = 0
          elif self.top > SCREEN_HEIGHT - 1:
              self.top = SCREEN_HEIGHT - 1

  class MyGame(arcade.Window):
      """
      Main application class.
      """

      def __init__(self, width, height, title):
          super().__init__(width, height, title)

          self.coin_list = None
          self.wall_list = None
          self.player_list = None
          self.player_sprite = None
          self.physics_engine = None

          self.left_pressed = False
          self.right_pressed = False
          self.up_pressed = False
          self.down_pressed = False

          arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

      def setup(self):
          """ Set up the game here. Call this function to restart the game. """
          self.player_list = arcade.SpriteList()
          self.wall_list = arcade.SpriteList(use_spatial_hash=True)
          self.coin_list = arcade.SpriteList(use_spatial_hash=True)

          # This time we've saved the image source to it's own variable for use in the next line
          image_source = ":resources:images/animated_characters/female_adventurer/femaleAdventurer_idle.png"
          self.player_sprite = Player(image_source, CHARACTER_SCALING)
          self.player_sprite.center_x = 64
          self.player_sprite.center_y = 128
          self.player_list.append(self.player_sprite)

          for x in range(0, 1250, 64):
              # Saving the image source in a separate variable for readability
              image_source2 = ":resources:images/tiles/grassMid.png"
              wall = arcade.Sprite(image_source2, TILE_SCALING)
              wall.center_x = x
              wall.center_y = 32
              self.wall_list.append(wall)

          coordinate_list = [[256, 96],
                             [512, 96],
                             [768, 96]]

          for coordinate in coordinate_list:
              # Again, saving the image source in a separate variable for readability
              image_source3 = ":resources:images/tiles/boxCrate_double.png"
              wall = arcade.Sprite(image_source3, TILE_SCALING)
              wall.position = coordinate
              self.wall_list.append(wall)

          # UPDATE TO PHYSICS ENGINE
          # https://arcade.academy/arcade.html?highlight=physicsengineplatformer#arcade.PhysicsEnginePlatformer
          # Create a physics engine for a platformer.
          # Has 4 possible parameters
              # player_sprite (Sprite) – The moving sprite
              # platforms (SpriteList) – The sprites it can’t move through
              # gravity_constant (float) – Downward acceleration per frame
              # ladders (SpriteList) – Ladders the user can climb on
          # We are using the player, the wall, and the gravity constant
          self.physics_engine = arcade.PhysicsEnginePlatformer(self.player_sprite, self.wall_list, GRAVITY)

      def on_draw(self):
          """ Render the screen. """
          arcade.start_render()

          self.wall_list.draw()
          self.coin_list.draw()
          self.player_list.draw()

      def on_key_press(self, key, modifiers):
          """Called whenever a key is pressed. """

          # Sets key directional_presses to true depending if user presses certain keys
          # This accounts for the arrow pad, the AWDS set, and the space bar
          if key == arcade.key.UP or key == arcade.key.W or key == arcade.key.SPACE:
              self.up_pressed = True
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = True
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = True
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = True

      def on_key_release(self, key, modifiers):
          """Called when the user releases a key. """

          # Sets key directional_presses to False if user releases specific key
          if key == arcade.key.UP or key == arcade.key.W:
              self.up_pressed = False
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = False
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = False
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = False

      def on_update(self, delta_time):
          """ Movement and game logic """

          # Calculate speed based on the keys pressed
          # We only need to reset the x value (left and right), since the y value now has a gravity component
          self.player_sprite.change_x = 0

          # If up is triggered
          if self.up_pressed and not self.down_pressed:
              # First check if the physics engine can_jump: https://arcade.academy/arcade.html?highlight=can_jump#arcade.PhysicsEnginePlatformer.can_jump
              # Method that looks to see if there is a floor under the player_sprite.
              # If there is a floor, the player can jump and we return a True.
              if self.physics_engine.can_jump():
                  # Change the y velocity for the player jump
                  self.player_sprite.change_y = PLAYER_JUMP_SPEED
          elif self.down_pressed and not self.up_pressed:
              self.player_sprite.change_y = -PLAYER_MOVEMENT_SPEED
          if self.left_pressed and not self.right_pressed:
              self.player_sprite.change_x = -PLAYER_MOVEMENT_SPEED
          elif self.right_pressed and not self.left_pressed:
              self.player_sprite.change_x = PLAYER_MOVEMENT_SPEED

          # Call update to move the sprite
          # If using a physics engine, call update player to rely on physics engine
          # for movement, and call physics engine here.
          self.player_list.update()
          self.physics_engine.update()

  def main():
      """ Main method """
      window = MyGame(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)
      window.setup()
      arcade.run()

  if __name__ == "__main__":
      main()
  ```
- **LOOKING FOR MORE?**
    - Explore the methods inside the [Simple](https://arcade.academy/arcade.html?highlight=physics%20engine#arcade.PhysicsEngineSimple) and [Platformer](https://arcade.academy/arcade.html?highlight=physics%20engine#arcade.PhysicsEnginePlatformer) physics engines
    - Want your physics to do more, check out [Pymunk](https://arcade.academy/arcade.html?highlight=physics%20engine#arcade.PymunkPhysicsEngine)
      - There is a full [tutorial](https://arcade.academy/tutorials/pymunk_platformer/index.html)
- Now that our player has some "real world" constraints, lets start updating the players world!

#### Add Scrolling
[Top](#priyas-practice)
- When a player moves across the screen and hits the edge of the screen, what should the game do?
  - If you have the arcade original files, your player just flies off the edge and can get lost
  - If you have my updated gravity file with better user control, the player cannot move past the edge
  - In a real game, the player wouldn't dissapear off the edge, instead, the "world" around the player would **scroll**
- Look at my starter file for scrolling, `05_scrolling.py`:
  - I can move my player left and right off the screen edge
  - When I do, the world around me expands!
  - I can see more as I scroll
  - I can even fall off the edge of the ground and my player will now fall forever.
- To fully understand this code, let's annotate the changes:
  ```py
  """
  Platformer Game
  """
  import arcade

  SCREEN_WIDTH = 1000
  SCREEN_HEIGHT = 650
  SCREEN_TITLE = "Platformer"

  CHARACTER_SCALING = 1
  TILE_SCALING = 0.5
  COIN_SCALING = 0.5

  PLAYER_MOVEMENT_SPEED = 3
  GRAVITY = 0.8
  PLAYER_JUMP_SPEED = 15

  # How many pixels to keep as a minimum margin between the character and the edge of the screen.
  # What is the distance between a screen edge and the player before the world begins to scroll?
      # This is what we are declaring as margins for each edge: left, right, bottom, and top
  LEFT_VIEWPORT_MARGIN = 250
  RIGHT_VIEWPORT_MARGIN = 250
  BOTTOM_VIEWPORT_MARGIN = 50
  TOP_VIEWPORT_MARGIN = 100

  class MyGame(arcade.Window):
      """
      Main application class.
      """

      def __init__(self):

          super().__init__(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)

          self.coin_list = None
          self.wall_list = None
          self.player_list = None

          self.player_sprite = None

          self.physics_engine = None

          # MY USER CONTROL UPDATES
          self.left_pressed = False
          self.right_pressed = False
          self.up_pressed = False
          self.down_pressed = False

          # Used to keep track of our scrolling
          # These set the original variables of the game for view_bottom and view_left to the integer value 0
          self.view_bottom = 0
          self.view_left = 0

          arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

      def setup(self):
          """ Set up the game here. Call this function to restart the game. """

          # Used to keep track of our scrolling
          # Why is this created in __init__ as well as in setup?
              # Potentially for the "restart" option?
          self.view_bottom = 0
          self.view_left = 0

          self.player_list = arcade.SpriteList()
          self.wall_list = arcade.SpriteList()
          self.coin_list = arcade.SpriteList()

          image_source = ":resources:images/animated_characters/female_adventurer/femaleAdventurer_idle.png"
          self.player_sprite = arcade.Sprite(image_source, CHARACTER_SCALING)
          self.player_sprite.center_x = 64
          self.player_sprite.center_y = 96
          self.player_list.append(self.player_sprite)

          for x in range(0, 1250, 64):
              image_source2 = ":resources:images/tiles/grassMid.png"
              wall = arcade.Sprite(image_source2, TILE_SCALING)
              wall.center_x = x
              wall.center_y = 32
              self.wall_list.append(wall)

          coordinate_list = [[256, 96],
                             [512, 96],
                             [768, 96]]

          for coordinate in coordinate_list:
              image_source3 = ":resources:images/tiles/boxCrate_double.png"
              wall = arcade.Sprite(image_source3, TILE_SCALING)
              wall.position = coordinate
              self.wall_list.append(wall)

          self.physics_engine = arcade.PhysicsEnginePlatformer(self.player_sprite,
                                                               self.wall_list,
                                                               GRAVITY)

      def on_draw(self):
          """ Render the screen. """

          arcade.start_render()

          self.wall_list.draw()
          self.coin_list.draw()
          self.player_list.draw()

      def on_key_press(self, key, modifiers):
          """Called whenever a key is pressed. """
          # MY USER CONTROL UPDATES
          if key == arcade.key.UP or key == arcade.key.W or key == arcade.key.SPACE:
              self.up_pressed = True
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = True
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = True
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = True

      def on_key_release(self, key, modifiers):
          """Called when the user releases a key. """
          # MY USER CONTROL UPDATES
          if key == arcade.key.UP or key == arcade.key.W:
              self.up_pressed = False
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = False
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = False
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = False

      def on_update(self, delta_time):
          """ Movement and game logic """
          # MY USER CONTROL UPDATES
          self.player_sprite.change_x = 0

          if self.up_pressed and not self.down_pressed:
              if self.physics_engine.can_jump():
                  self.player_sprite.change_y = PLAYER_JUMP_SPEED
          elif self.down_pressed and not self.up_pressed:
              self.player_sprite.change_y = -PLAYER_MOVEMENT_SPEED
          if self.left_pressed and not self.right_pressed:
              self.player_sprite.change_x = -PLAYER_MOVEMENT_SPEED
          elif self.right_pressed and not self.left_pressed:
              self.player_sprite.change_x = PLAYER_MOVEMENT_SPEED

          self.player_list.update()
          # Move the player with the physics engine
          self.physics_engine.update()

          # --- Manage Scrolling ---

          # Track if we need to change the viewport
          # Begins with a boolean variable, "changed", that is set to false (used further down in "if changed" block)
          changed = False

          # Scroll left
          # This sets up the view_left (which is set to 0) summed with the custom margin we set for the left edge
          left_boundary = self.view_left + LEFT_VIEWPORT_MARGIN
          # If the player's left coord is less than the left boundary from above
              # .left: https://arcade.academy/arcade.html?highlight=.left#arcade.Sprite.left
              # Return the x coordinate of the left-side of the sprite’s hitbox
                # Any transparent “white-space” around an image counts as the "hitbox"
                # You can trim the space in a graphics editor OR specify a hitbox
          if self.player_sprite.left < left_boundary:
              # "-=" is called subtraction assignment: https://python-reference.readthedocs.io/en/latest/docs/operators/subtraction_assignment.html
                  # Subtracts a value from the variable and assigns the result to that variable.
              # In this case, first take the left_boundary from above and subtract the player's left coord
              # THEN, subtract that from view_left and reassign view_left with this new number
              # It makes sense that this value is negative, because we would be heading left, aka, in the negative direction on the x-axis
              self.view_left -= left_boundary - self.player_sprite.left
              # Finally, update "changed" to True
              changed = True

          # Scroll right
          # The right_boundary must include the screen width as a component
          right_boundary = self.view_left + SCREEN_WIDTH - RIGHT_VIEWPORT_MARGIN
          # If a players right coord attempts to exceed the right boundary
          if self.player_sprite.right > right_boundary:
              # Because this is on the right side of the screen, we want to use addition assignment
              # view_left is now a positive value because we are heading right, or in the positive direction on the x-axis
              self.view_left += self.player_sprite.right - right_boundary
              changed = True

          # Scroll up
          # Very similar to above if-block, bit takes in Height and the Top/Bottom viewport margins
          top_boundary = self.view_bottom + SCREEN_HEIGHT - TOP_VIEWPORT_MARGIN
          if self.player_sprite.top > top_boundary:
              self.view_bottom += self.player_sprite.top - top_boundary
              changed = True

          # Scroll down
          # This does not need height
          bottom_boundary = self.view_bottom + BOTTOM_VIEWPORT_MARGIN
          if self.player_sprite.bottom < bottom_boundary:
              self.view_bottom -= bottom_boundary - self.player_sprite.bottom
              changed = True

          # Here is where all the above if-blocks come into play
          # If changed is true, then this means our player is attempting to go past the margins near the edge
          if changed:
              # Only scroll to integers. Otherwise we end up with pixels that don't line up on the screen
              self.view_bottom = int(self.view_bottom)
              self.view_left = int(self.view_left)

              # Do the scrolling
              # .set_viewport: https://arcade.academy/arcade.html?highlight=.set_viewport#arcade.set_viewport
              # This sets what coordinates the window will cover.
              # By default, the lower left coordinate will be (0, 0) and the top y coordinate will be the height of the window in pixels, and the right x coordinate will be the width of the window in pixels.
              arcade.set_viewport(self.view_left,
                                  SCREEN_WIDTH + self.view_left,
                                  self.view_bottom,
                                  SCREEN_HEIGHT + self.view_bottom)

  def main():
      """ Main method """
      window = MyGame()
      window.setup()
      arcade.run()

  if __name__ == "__main__":
      main()
  ```
- Now let's play with our code:
  1. What happens when I change the viewport margins to something else?
    - If I change the viewport constants at the beginning to very _small_ values, my player doesn't make the world scroll until it gets to the very edge of the map
      - This doesn't seem like great gameplay because I can't see what is coming on the map.
      ```py
      LEFT_VIEWPORT_MARGIN = 5
      RIGHT_VIEWPORT_MARGIN = 5
      BOTTOM_VIEWPORT_MARGIN = 5
      TOP_VIEWPORT_MARGIN = 5
      ```
    - If I change the viewport constants at the beginning to very _large_ values, my player makes the world scroll "too much". If I jump, the entire world shift. My ground is off center now because my player is "approaching the bottom" edge. If I move right or left, the entire world moves.
      - This is bad gameplay because the world is moving too much and too quick. The user can't fully see what is happening on the map.
      ```py
      LEFT_VIEWPORT_MARGIN = 500
      RIGHT_VIEWPORT_MARGIN = 500
      BOTTOM_VIEWPORT_MARGIN = 300
      TOP_VIEWPORT_MARGIN = 300
      ```
  2. **LOOKING FOR MORE?**
    - Explore [viewport](https://arcade.academy/arcade.html?highlight=.set_viewport#arcade.set_viewport) thought the Arcade Class
- Awesome! We are beginning to have an interactive space for our player. But if a player can just move around a space, that doesn't make for a compelling game. Let's give our player some incentive in the next section.

#### Add Coins and Sounds
[Top](#priyas-practice)
- With this code players can collect coins AND we will add sounds that trigger when a coin is collected or the player jumps
- Playing with `06_coins_and_sounds`, I see that my player can now collect coins and trigger sounds
- But... I'm not happy with the user control, so first I update it to match better user keystrokes
- Like usual, to grasp the new code, let's annotate it:
  ```py
  """
  Platformer Game
  """
  import arcade

  SCREEN_WIDTH = 1000
  SCREEN_HEIGHT = 650
  SCREEN_TITLE = "Priya's 2D Funhouse"

  CHARACTER_SCALING = 1
  TILE_SCALING = 0.5
  # NEW CONSTANT FOR COIN SCALING
  COIN_SCALING = 0.5

  PLAYER_MOVEMENT_SPEED = 3
  GRAVITY = 0.8
  PLAYER_JUMP_SPEED = 15

  LEFT_VIEWPORT_MARGIN = 250
  RIGHT_VIEWPORT_MARGIN = 250
  BOTTOM_VIEWPORT_MARGIN = 50
  TOP_VIEWPORT_MARGIN = 100

  class MyGame(arcade.Window):
      """
      Main application class.
      """

      def __init__(self):

          super().__init__(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)
          # New Coin List Variable Setup
          self.coin_list = None
          self.wall_list = None
          self.player_list = None

          self.player_sprite = None

          self.physics_engine = None

          # MY USER CONTROL UPDATES
          self.left_pressed = False
          self.right_pressed = False
          self.up_pressed = False
          self.down_pressed = False

          self.view_bottom = 0
          self.view_left = 0

          # Creates a variable that holds our sound for coin collection
          # .load_sound: https://arcade.academy/arcade.html?highlight=.load_sound#arcade.load_sound
              # Loads a sound for use with .play_sound later
          self.collect_coin_sound = arcade.load_sound(":resources:sounds/coin1.wav")
          # Creates a variable that holds our sound for player jumping
          self.jump_sound = arcade.load_sound(":resources:sounds/jump1.wav")

          arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

      def setup(self):
          """ Set up the game here. Call this function to restart the game. """

          self.view_bottom = 0
          self.view_left = 0

          self.player_list = arcade.SpriteList()
          self.wall_list = arcade.SpriteList()
          # New Coin Sprite List
          self.coin_list = arcade.SpriteList()

          image_source = ":resources:images/animated_characters/female_adventurer/femaleAdventurer_idle.png"
          self.player_sprite = arcade.Sprite(image_source, CHARACTER_SCALING)
          self.player_sprite.center_x = 64
          self.player_sprite.center_y = 128
          self.player_list.append(self.player_sprite)

          for x in range(0, 1250, 64):
              image_source2 = ":resources:images/tiles/grassMid.png"
              wall = arcade.Sprite(image_source2, TILE_SCALING)
              wall.center_x = x
              wall.center_y = 32
              self.wall_list.append(wall)

          coordinate_list = [[256, 96],
                             [512, 96],
                             [768, 96]]

          for coordinate in coordinate_list:
              image_source3 = ":resources:images/tiles/boxCrate_double.png"
              wall = arcade.Sprite(image_source3, TILE_SCALING)
              wall.position = coordinate
              self.wall_list.append(wall)

          # Adds a new sprite: the coin
          for x in range(128, 1250, 256):
              image_source4 = ":resources:images/items/coinGold.png"
              coin = arcade.Sprite(image_source4, COIN_SCALING)
              coin.center_x = x
              # Makes the coin float a little off the ground
              coin.center_y = 96
              # Adds coin to coin list
              self.coin_list.append(coin)

          self.physics_engine = arcade.PhysicsEnginePlatformer(self.player_sprite,
                                                               self.wall_list,
                                                               GRAVITY)

      def on_draw(self):
          """ Render the screen. """
          arcade.start_render()

          self.wall_list.draw()
          self.coin_list.draw()
          self.player_list.draw()

      def on_key_press(self, key, modifiers):
          """Called whenever a key is pressed. """
          # MY USER CONTROL UPDATES
          if key == arcade.key.UP or key == arcade.key.W or key == arcade.key.SPACE:
              self.up_pressed = True
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = True
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = True
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = True

      def on_key_release(self, key, modifiers):
          """Called when the user releases a key. """
          # MY USER CONTROL UPDATES
          if key == arcade.key.UP or key == arcade.key.W:
              self.up_pressed = False
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = False
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = False
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = False

      def update(self, delta_time):
          """ Movement and game logic """
          # MY USER CONTROL UPDATES
          self.player_sprite.change_x = 0

          if self.up_pressed and not self.down_pressed:
              if self.physics_engine.can_jump():
                  self.player_sprite.change_y = PLAYER_JUMP_SPEED
                  # NEW INFO FROM SOUNDS
                  # This plays the sound from jump_sound which was set in __init__
                  arcade.play_sound(self.jump_sound)
          elif self.down_pressed and not self.up_pressed:
              self.player_sprite.change_y = -PLAYER_MOVEMENT_SPEED
          if self.left_pressed and not self.right_pressed:
              self.player_sprite.change_x = -PLAYER_MOVEMENT_SPEED
          elif self.right_pressed and not self.left_pressed:
              self.player_sprite.change_x = PLAYER_MOVEMENT_SPEED

          self.player_list.update()
          self.physics_engine.update()

          # The code for what happens when a player collides with a coin
          # Checks the coin sprite list for collisions AND saves to a new variable "coin_hit_list"
          # .check_for_collision_with_list: https://arcade.academy/arcade.html?highlight=check_for_collision_with_list#arcade.check_for_collision_with_list
              # Check for a collision between a sprite, and a list of sprites
              # 2 Parameters: (sprite_to_check, sprite_to_check_AGAINST)
          coin_hit_list = arcade.check_for_collision_with_list(self.player_sprite,
                                                               self.coin_list)

          # For every coin sprite in the coin HIT list
          for coin in coin_hit_list:
              # Remove the coin from any sprite list it belongs to
              coin.remove_from_sprite_lists()
              # Play the sound set in __init__
              arcade.play_sound(self.collect_coin_sound)

          # --- Manage Scrolling ---
          changed = False

          left_boundary = self.view_left + LEFT_VIEWPORT_MARGIN
          if self.player_sprite.left < left_boundary:
              self.view_left -= left_boundary - self.player_sprite.left
              changed = True

          right_boundary = self.view_left + SCREEN_WIDTH - RIGHT_VIEWPORT_MARGIN
          if self.player_sprite.right > right_boundary:
              self.view_left += self.player_sprite.right - right_boundary
              changed = True

          top_boundary = self.view_bottom + SCREEN_HEIGHT - TOP_VIEWPORT_MARGIN
          if self.player_sprite.top > top_boundary:
              self.view_bottom += self.player_sprite.top - top_boundary
              changed = True

          bottom_boundary = self.view_bottom + BOTTOM_VIEWPORT_MARGIN
          if self.player_sprite.bottom < bottom_boundary:
              self.view_bottom -= bottom_boundary - self.player_sprite.bottom
              changed = True

          if changed:
              self.view_bottom = int(self.view_bottom)
              self.view_left = int(self.view_left)

              arcade.set_viewport(self.view_left,
                                  SCREEN_WIDTH + self.view_left,
                                  self.view_bottom,
                                  SCREEN_HEIGHT + self.view_bottom)

  def main():
      """ Main method """
      window = MyGame()
      window.setup()
      arcade.run()

  if __name__ == "__main__":
      main()
  ```
- Updates you could make in this section:
  1. Update where you place the coins (How would you make them higher? How would you place them on top of crates? How would you place them for jumpable off crates?)
  2. Add other collectibles (Gems and keys are in the arcade resources. You can also internet research "sprite resources open source" )
  3. Make a subclass for the coin sprite and add an attribute for a score value. Make a subclass for your gem sprite. Then you could have coins worth one point, and gems worth 5, 10, and 15 points.
  4. **LOOKING FOR MORE?**
    - [Coins by mouse](https://arcade.academy/examples/sprite_collect_coins.html)
    - [Coins collected downward](https://arcade.academy/examples/sprite_collect_coins_move_down.html)
    - [Change Coins](https://arcade.academy/examples/sprite_change_coins.html)
    - [Random Placement with Safeguards](https://arcade.academy/examples/sprite_no_coins_on_walls.html)
    - [Level Coin Clearage](https://arcade.academy/examples/sprite_collect_coins_diff_levels.html_)
- So we can collect coins... but how does a player know their score? Let's see the section for [displaying the score](#display-the-score).

#### Halfway Demo
[Top](#priyas-practice)

![halfway demo](https://user-images.githubusercontent.com/49959312/109329417-c3d48d80-7817-11eb-95b4-941c3de613f1.gif)

#### Display the Score
[Top](#priyas-practice)
- As easy as it would be to draw a static box with a score inside, it isn't quite correct for our game dynamics:
  - Since our game scrolls at the edges, we must account for this when we setup our score box!
- I ran my `07_score.py` and see the same game as the previous section, but now, there is a Score board in the bottom left hand of my screen that scrolls with the users character as they move around
- I like to modify the code for more appropriate user input and annotate the code for understanding. Like usual, the changes are documented using comments:
  ```py
  """
  Platformer Game
  """
  import arcade

  SCREEN_WIDTH = 1000
  SCREEN_HEIGHT = 650
  SCREEN_TITLE = "Priya's 2D Funhouse"

  CHARACTER_SCALING = 1
  TILE_SCALING = 0.5
  COIN_SCALING = 0.5

  PLAYER_MOVEMENT_SPEED = 3
  GRAVITY = 0.8
  PLAYER_JUMP_SPEED = 13

  LEFT_VIEWPORT_MARGIN = 250
  RIGHT_VIEWPORT_MARGIN = 250
  BOTTOM_VIEWPORT_MARGIN = 50
  TOP_VIEWPORT_MARGIN = 100


  class MyGame(arcade.Window):
      """
      Main application class.
      """

      def __init__(self):

          super().__init__(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_TITLE)

          self.coin_list = None
          self.wall_list = None
          self.player_list = None

          self.player_sprite = None

          self.physics_engine = None

          # MY USER CONTROL UPDATES
          self.left_pressed = False
          self.right_pressed = False
          self.up_pressed = False
          self.down_pressed = False

          self.view_bottom = 0
          self.view_left = 0

          # SETS INITIAL VALUE OF SCORE TO ZERO AND HELPS US KEEP TRACK OF THE SCORE BY GIVING US ACCESS TO A self.score VARIABLE THAT WE CAN ADD/SUBTRACT POINTS TO/FROM
          self.score = 0

          self.collect_coin_sound = arcade.load_sound(":resources:sounds/coin1.wav")
          self.jump_sound = arcade.load_sound(":resources:sounds/jump1.wav")

          # I LIKE TO CHANGE MY BACKGROUND COLOR FOR MY PERSONAL PREFERENCE OF THIS PRETTY PINK COLOR
          arcade.set_background_color(arcade.csscolor.MEDIUM_VIOLET_RED)

      def setup(self):
          """ Set up the game here. Call this function to restart the game. """

          self.view_bottom = 0
          self.view_left = 0

          # FOR THE RESTART, THIS SETS SCORE TO 0
          self.score = 0

          self.player_list = arcade.SpriteList()
          self.wall_list = arcade.SpriteList()
          self.coin_list = arcade.SpriteList()

          image_source = ":resources:images/animated_characters/female_adventurer/femaleAdventurer_idle.png"
          self.player_sprite = arcade.Sprite(image_source, CHARACTER_SCALING)
          self.player_sprite.center_x = 64
          self.player_sprite.center_y = 96
          self.player_list.append(self.player_sprite)

          for x in range(0, 1250, 64):
              image_source2 = ":resources:images/tiles/grassMid.png"
              wall = arcade.Sprite(image_source2, TILE_SCALING)
              wall.center_x = x
              wall.center_y = 32
              self.wall_list.append(wall)

          coordinate_list = [[256, 96],
                             [512, 96],
                             [768, 96]]

          for coordinate in coordinate_list:
              image_source3 = ":resources:images/tiles/boxCrate_double.png"
              wall = arcade.Sprite(image_source3, TILE_SCALING)
              wall.position = coordinate
              self.wall_list.append(wall)

          for x in range(128, 1250, 256):
              image_source4 = ":resources:images/items/coinGold.png"
              coin = arcade.Sprite(image_source4, COIN_SCALING)
              coin.center_x = x
              coin.center_y = 96
              self.coin_list.append(coin)

          self.physics_engine = arcade.PhysicsEnginePlatformer(self.player_sprite,
                                                               self.wall_list,
                                                               GRAVITY)

      def on_draw(self):
          """ Render the screen. """

          arcade.start_render()

          self.wall_list.draw()
          self.coin_list.draw()
          self.player_list.draw()

          # DRAW THE SCORE ON THE SCREEN
          # HAS DYNAMIC CAPABILITIES - IT SCROLLS WITH YOUR PLAYER
          # score_text is a String with the self.score interpolated into the Score statement
          score_text = f"Score: {self.score}"
          # draw text is an arcade function that draws text to the screen
              # https://arcade.academy/arcade.html?highlight=draw_text#arcade.draw_text
          # The arguments are as follows:
              # .draw_text(TEXT, X-START, Y-START, COLOR, FONT-SIZE)
          # So this creates a text box drawn on the bottom left of the screen with the score printed from self.score in the color white at font size 18
          arcade.draw_text(score_text, 10 + self.view_left, 10 + self.view_bottom,
                           arcade.csscolor.WHITE, 18)

      def on_key_press(self, key, modifiers):
          """Called whenever a key is pressed. """

          # MY USER CONTROL UPDATES
          if key == arcade.key.UP or key == arcade.key.W or key == arcade.key.SPACE:
              self.up_pressed = True
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = True
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = True
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = True

      def on_key_release(self, key, modifiers):
          """Called when the user releases a key. """

          # MY USER CONTROL UPDATES
          if key == arcade.key.UP or key == arcade.key.W:
              self.up_pressed = False
          elif key == arcade.key.DOWN or key == arcade.key.S:
              self.down_pressed = False
          elif key == arcade.key.LEFT or key == arcade.key.A:
              self.left_pressed = False
          elif key == arcade.key.RIGHT or key == arcade.key.D:
              self.right_pressed = False

      def on_update(self, delta_time):
          """ Movement and game logic """

          # MY USER CONTROL UPDATES
          self.player_sprite.change_x = 0

          if self.up_pressed and not self.down_pressed:
              if self.physics_engine.can_jump():
                  self.player_sprite.change_y = PLAYER_JUMP_SPEED
                  arcade.play_sound(self.jump_sound)
          elif self.down_pressed and not self.up_pressed:
              self.player_sprite.change_y = -PLAYER_MOVEMENT_SPEED
          if self.left_pressed and not self.right_pressed:
              self.player_sprite.change_x = -PLAYER_MOVEMENT_SPEED
          elif self.right_pressed and not self.left_pressed:
              self.player_sprite.change_x = PLAYER_MOVEMENT_SPEED

          self.player_list.update()

          self.physics_engine.update()

          coin_hit_list = arcade.check_for_collision_with_list(self.player_sprite,
                                                               self.coin_list)

          for coin in coin_hit_list:
              coin.remove_from_sprite_lists()
              arcade.play_sound(self.collect_coin_sound)
              # EVERY TIME A PLAYER HITS A COIN, THIS INCREMENTS BY 1 FOR SCORE COLLECTION
              self.score += 1

          # --- Manage Scrolling ---
          changed = False

          left_boundary = self.view_left + LEFT_VIEWPORT_MARGIN
          if self.player_sprite.left < left_boundary:
              self.view_left -= left_boundary - self.player_sprite.left
              changed = True

          right_boundary = self.view_left + SCREEN_WIDTH - RIGHT_VIEWPORT_MARGIN
          if self.player_sprite.right > right_boundary:
              self.view_left += self.player_sprite.right - right_boundary
              changed = True

          top_boundary = self.view_bottom + SCREEN_HEIGHT - TOP_VIEWPORT_MARGIN
          if self.player_sprite.top > top_boundary:
              self.view_bottom += self.player_sprite.top - top_boundary
              changed = True

          bottom_boundary = self.view_bottom + BOTTOM_VIEWPORT_MARGIN
          if self.player_sprite.bottom < bottom_boundary:
              self.view_bottom -= bottom_boundary - self.player_sprite.bottom
              changed = True

          if changed:
              self.view_bottom = int(self.view_bottom)
              self.view_left = int(self.view_left)

              arcade.set_viewport(self.view_left,
                                  SCREEN_WIDTH + self.view_left,
                                  self.view_bottom,
                                  SCREEN_HEIGHT + self.view_bottom)


  def main():
      """ Main method """
      window = MyGame()
      window.setup()
      arcade.run()


  if __name__ == "__main__":
      main()
  ```
- Things you might consider adding for more dynamic games:
  - A count of how many coins are left to be collected.
  - Number of lives left.
  - A timer: [On-Screen Timer](https://arcade.academy/examples/timer.html#timer)
  - This example shows how to add an FPS timer: [Draw Moving Sprites Stress Test](https://arcade.academy/examples/stress_test_draw_moving.html#stress-test-draw-moving)
  - Practice creating your own layout with different tiles.
  - Add background images. See [Using a Background Image](https://arcade.academy/examples/sprite_collect_coins_background.html#sprite-collect-coins-background)
  - Add moving platforms. See [Moving Platforms](https://arcade.academy/examples/sprite_moving_platforms.html#sprite-moving-platforms)
  - Change the character image based on the direction she is facing. See [Sprite: Face Left or Right](https://arcade.academy/examples/sprite_face_left_or_right.html#sprite-face-left-or-right)
  - Add instruction and game over screens.
- With scores displayed, we are ready to create levels for our player!

#### Use a Map Editor
[Top](#priyas-practice)
- What is a Map Editor?
  - Don't forget to install from the Part 1 section: [What is a Tiled Map Editor](#What-is-a-Tiled-Map-Editor)
  - A map editor helps create the playable levels that a users character might access
  - Consider the Mario Series, every level had a distinct map with enemies, obstacles, power-ups, coins, etc
    - ![super mario bros level poster](https://i.pinimg.com/originals/04/8a/60/048a60099be2b7819b24100d15c2d638.jpg)
  - Want to learn [more](https://gamedevelopment.tutsplus.com/tutorials/introduction-to-tiled-map-editor-a-platform-agnostic-tool-for-level-maps--gamedev-2838)?
- So let's use TILED
  - I open the Application `Tiled`
  - Create a new file/map
  - ![new map](https://user-images.githubusercontent.com/49959312/109323346-9a643380-7810-11eb-9575-ac9a9967b5d5.png)
  - Fill out the options
  - ![options](https://user-images.githubusercontent.com/49959312/109323972-4c9bfb00-7811-11eb-8e72-731413c68042.png)
    ```
    Orientation: Orthogonal
    Tile layer format: Base65 (zlib compressed)
    Tile render order: Right Down
    Map size: Width: 25; Height: 20
    Tile Size: Width: 128; Height: 128
    ```
  - Details about options:
    - Orthogonal - This is a normal square-grid layout. It is the only version that Arcade supports very well at this time.
    - Tile layer format - This selects how the data is stored inside the file. Any option works, but Base64 zlib compressed is the smallest.
    - Tile render order - Any of these should work. It simply specifies what order the tiles are added. Right-down has tiles added left->right and top->down.
    - Map size - You can change this later, but this is your total grid size.
    - Tile size - the size, in pixels, of your tiles. Your tiles all need to be the same size. Also, rendering works better if the tile size is a power of 2, such as 16, 32, 64, 128, and 256.
  - Click `Save As...` and name your file. I chose `map.tmx` from the tutorial and I made sure it was in my project folder
  - This opened a blank file
  - ![blank map](https://user-images.githubusercontent.com/49959312/109324229-9edd1c00-7811-11eb-9a39-5acacffae887.png)
  - We need to change the layer name to "Platforms"
  - ![update layer name](https://user-images.githubusercontent.com/49959312/109324329-c207cb80-7811-11eb-85be-cd907e876413.png)
  - We may eventually have layers for:
    - Platforms that you run into (or you can think of them as walls)
    - Coins or objects to pick up
    - Background objects that you don’t interact with, but appear behind the player
    - Foreground objects that you don’t interact with, but appear in front of the player
    - Insta-death blocks (like lava)
    - Ladders
  - Create a tileset (click bottom right button `New Tileset...`)
  - ![new tileset](https://user-images.githubusercontent.com/49959312/109324508-ff6c5900-7811-11eb-861f-16ff36733ccf.png)
    ```
    name: my_tiles
    type: Collection of images
    embed in map: CHECKED
    ```
  - ![tileset info](https://user-images.githubusercontent.com/49959312/109324703-42c6c780-7812-11eb-8c41-ab857fe16b17.png)
  - when I hit `OK`, I now see a blank tileset in the bottom right of my screen
  - ![blank tileset](https://user-images.githubusercontent.com/49959312/109324879-7efa2800-7812-11eb-8b80-1bee7025c96a.png)
  - Now we need to add in our tilesets. In the Tilesets box, there are icons on the bottom. Find the one for "Edit" (has a wrench) which will open a new file (map.tmx#my_tiles => file_name#tile_name). At the top of this file, there will be a "Plus" icon. Clicking on this will get us to the point where we can "paint" our level.
  - ![tileset vid](https://user-images.githubusercontent.com/49959312/109329690-20d04380-7818-11eb-9a9e-01a962f85ff2.gif)
  - Create a level by adding whatever tiles you may want. Return to the main map.tsx file and use your mouse to add tiles wherever you would like on your map
  - ![level vid](https://user-images.githubusercontent.com/49959312/109330055-845a7100-7818-11eb-8ffe-499d00915c24.gif)
  - Finish a TEST LEVEL - this means don't spend forever on this level, make something quick (and maybe ugly), because we just want to confirm this works with our code before we spend time creating in-depth levels
  - ![test level](https://user-images.githubusercontent.com/49959312/109327279-65a6ab00-7815-11eb-8943-cf2811c4ac20.png)




- In fact, we have a starter file for ourselves called `0.py` that we can play around with
- When I run it, I see
- To fully understand this code, let's annotate it:
```py
```
- Now let's play with our code:
  1. Adjust the code and try putting sprites in new positions.
    - ADJUSTMENT NOTES
```py
```
- Now that we can

#### Multiple Levels and Other Layers
[Top](#priyas-practice)
- DEETS
- In fact, we have a starter file for ourselves called `0.py` that we can play around with
- When I run it, I see
- To fully understand this code, let's annotate it:
```py
```
- Now let's play with our code:
  1. Adjust the code and try putting sprites in new positions.
    - ADJUSTMENT NOTES
```py
```
- Now that we can

#### Add Ladders, Properties, and a Moving Platform
[Top](#priyas-practice)
- DEETS
- In fact, we have a starter file for ourselves called `0.py` that we can play around with
- When I run it, I see
- To fully understand this code, let's annotate it:
```py
```
- Now let's play with our code:
  1. Adjust the code and try putting sprites in new positions.
    - ADJUSTMENT NOTES
```py
```
- Now that we can

#### Add Character Animations and Better Keyboard Control
[Top](#priyas-practice)
- DEETS
- In fact, we have a starter file for ourselves called `0.py` that we can play around with
- When I run it, I see
- To fully understand this code, let's annotate it:
```py
```
- Now let's play with our code:
  1. Adjust the code and try putting sprites in new positions.
    - ADJUSTMENT NOTES
```py
```
- Now that we can

### Part 3
------
#### What is Pymunk
[Top](#priyas-practice)
- https://arcade.academy/tutorials/pymunk_platformer/index.html#

### Part 4
------
#### Final Code
[Top](#priyas-practice)
- Github repo]()
- Play game here]()

#### An Executable Program
[Top](#priyas-practice)
- BLARG___________________________________
