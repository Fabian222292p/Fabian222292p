
import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up display
width, height = 800, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("2D Adventure Game")

# Set up player
player_size = 50
player_x, player_y = width // 2, height // 2
player_speed = 5

# Main game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Get keys pressed
    keys = pygame.key.get_pressed()

    # Update player position based on keys pressed
    if keys[pygame.K_LEFT] and player_x > 0:
        player_x -= player_speed
    if keys[pygame.K_RIGHT] and player_x < width - player_size:
        player_x += player_speed
    if keys[pygame.K_UP] and player_y > 0:
        player_y -= player_speed
    if keys[pygame.K_DOWN] and player_y < height - player_size:
        player_y += player_speed

    # Clear the screen
    screen.fill((255, 255, 255))

    # Draw player
    pygame.draw.rect(screen, (0, 0, 255), (player_x, player_y, player_size, player_size))

    # Update display
    pygame.display.flip()

    # Control the frame rate
    pygame.time.Clock().tick(60)
