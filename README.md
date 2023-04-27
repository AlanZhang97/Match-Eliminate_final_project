# Match-Eliminate_final_project

Introduction:

This code implements a game that involves matching blocks of the same kind gem. It features a GUI built using the tkinter library ands implements a puzzle game where the objective is to connect two given points on a board by drawing straight lines. The board is represented as a two-dimensional array, where the cells can be either empty or blocked. The solution is found by building a path between the two points that only goes through empty cells.

How to Run:

To run the code, you need to have Python 3 installed. You also need to have the tkinter and winsound libraries installed. You can then run the main.py file in a Python environment such as IDLE or Visual Studio Code.

How to play:

The game consists of a grid of blocks of different colors. The objective is to match blocks of the same color by selecting two adjacent blocks with the mouse. If the blocks can be matched by drawing a line that connects them with no more than two turns, they will be eliminated from the grid, and the player will score points. The game ends when there are no more blocks that can be matched. To select a block, click on it with the left mouse button. To deselect a block, click on it again. To attempt to match two selected blocks, click on the second block. If the match is valid, the blocks will be eliminated, and the player will score points. If the match is not valid, the blocks will be deselected, and the player can try again.

Code structure:

Point:
a class that represents a point in 2D space, with x and y attributes.

draw_checkerboard:
a function that draws a checkerboard pattern on the canvas using cv.create_line.

print_map: 
a function that outputs the map dictionary, creates images from the corresponding values in the images list, and places them on the canvas using cv.create_image at the appropriate coordinates based on the x and y values of the Point objects. The id of each image is stored in the image_map dictionary for later reference.

call_back: 
a function that handles the logic of selecting two blocks and checking if they can be eliminated

clear_two_blocks:
a function that is called when two blocks are successfully eliminated.

line_check: 
a function checks if there is a straight line between two given points on the board. It first checks if the points are on the same row or column, and if so, checks if there are any blocked cells between them. If there are no blocked cells, it returns True, indicating that the two points can be connected with a straight line. Otherwise, it returns False.

one_corner_connection: 
a function attempts to connect two given points with a right-angle bend. It first checks if there is an empty cell on the same row as the first point and the same column as the second point, or on the same column as the first point and the same row as the second point. If there is, it checks if it is possible to build a straight line from the first point to the empty cell, and from the empty cell to the second point, without going through any blocked cells. If so, it adds the empty cell to a stack of line points and returns True. Otherwise, it returns False.

two_corner_connection: 
a function attempts to connect two given points with two right-angle bends. It first iterates through the four directions around the first point, looking for an empty cell called check_point. It then calls the one_corner_connection function with check_point and the second point as parameters, to determine if it is possible to connect the two points with a right-angle bend at check_point. If it is, it adds check_point to the stack of line points and returns True. If not, it continues iterating until all directions have been checked. If no valid check_point is found, it returns False.

generate_map(): 
a function defines a game where the player has to connect matching blocks with lines. The game board is represented as a grid of blocks, where each block is assigned a random type

hint(): 
a function is called when the player requests a hint. It iterates over all possible pairs of blocks on the game board and checks whether they can be linked with a straight line. If a valid pair is found, the function draws two green rectangles around the selected blocks to indicate to the player which blocks to connect. A timer is started to delay the removal of the hint after a few seconds.

draw_connection_line: 
a function is called when the player clicks on two blocks that can be linked. It draws a yellow line between the two blocks and checks if the line forms a connection between existing lines on the game board. If the line connects two existing lines, the function draws new lines to connect the remaining endpoints.

delete_connection_line: 
a function is called when the player clicks on an existing line to delete it. It removes the line from the game board.

Tgame_menu: 
creates a simple graphical user interface using the tkinter library in Python.
