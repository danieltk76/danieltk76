# Import the pygame module
import pygame

# import pygame.locals for easier access to key coordinates
# updated to conform to flake8 and black standards
from pygame.locals import (
    K_UP,
    K_DOWN,
    K_RIGHT,
    K_ESCAPE,
    K_LEFT,
    KEYDOWN,
    QUIT,
)

# initialize pygame
pygame.init()

# define a player object by extending pygame.sprite.Sprite
# the surface drawn on the screen is now an attribute of the 'player'
class Player(pygame.sprite.Sprite):
    def _init_(self):
        super(Player, self).__init__()
        self.surf = pygame.Surface((75, 25))
        self.surf.fill((255, 255, 255))
        self.rect = self.surf.get_rect()



# define constants for the screen width and height
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600


# create the screen object
# the size is determined by the constant SCREEN_WIDTH and SCREEN_HEIGHT
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

# variable to keep the main loop running
running = True

# Main loop
while running:
    for event in pygame.event.get():
        if event.type == KEYDOWN:
            if event.key == K_ESCAPE:
                running = False

        elif event.type == QUIT:
            running = False

# fill the screen with white
screen.fill((255, 255, 255))

# create a surface and pass in a tuple containing its length and width
surf = pygame.Surface((50, 50))

# give the surface a color to separate it from the background
surf.fill((0, 0, 0))
rect = surf.get_rect()

# this line says "Draw surf onto the screen at the center"
screen.blit(surf, (SCREEN_WIDTH/2, SCREEN_HEIGHT/2))
pygame.display.flip()

# put the center of the surf at the center of the display
surf_center = (
    (SCREEN_WIDTH-surf.get_width())/2,
    (SCREEN_HEIGHT-surf.get_height())/2
)
# draw surf at the new coordinates
screen.blit(surf, surf_center)
pygame.display.flip()

