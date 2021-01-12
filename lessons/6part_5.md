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
  1. [Display the Score](#Display-the-Score)
  1. [Use a Map Editor](#Use-a-Map-Editor)
  1. [Multiple Levels and Other Layers](#Multiple-Levels-and-Other-Layers)
  1. [Add Ladders, Properties, and a Moving Platform](#Add-Ladders-Properties-and-a-Moving-Platform)
  1. [Add Character Animations and Better Keyboard Control](#Add-Character Animations-and-Better-Keyboard-Control)
- [Part 3: Adding Physics using Pymunk](#part-3)
  1. [What is Pymunk](#What-is-Pymunk)
- [Part 4: ](#part-4)
  1. [Final Code](#Final-Code)

------
### Part 0
------
#### Arcade
[Top](#priyas-practice)
- BLARG___________________________________

#### Pycharm
[Top](#priyas-practice)
- BLARG___________________________________

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
- BLARG___________________________________
- https://www.mapeditor.org

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

#### Add Sprites
[Top](#priyas-practice)
-

#### Add User Control
[Top](#priyas-practice)
-

#### Add Gravity
[Top](#priyas-practice)
-

#### Add Scrolling
[Top](#priyas-practice)
-

#### Add Coins and Sounds
[Top](#priyas-practice)
-

#### Display the Score
[Top](#priyas-practice)
-

#### Use a Map Editor
[Top](#priyas-practice)
-

#### Multiple Levels and Other Layers
[Top](#priyas-practice)
-

#### Add Ladders, Properties, and a Moving Platform
[Top](#priyas-practice)
-

#### Add Character Animations and Better Keyboard Control
[Top](#priyas-practice)
-

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
