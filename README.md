pip install pygame
import pygame
import random

# Initialize pygame
pygame.init()

# Screen dimensions
WIDTH, HEIGHT = 500, 500
BLOCK_SIZE = 20

# Colors
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
RED = (255, 0, 0)
BLACK = (0, 0, 0)

# Create screen
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Snake Game")

# Snake and food initial positions
snake = [(100, 100), (80, 100), (60, 100)]
snake_dir = (BLOCK_SIZE, 0)
food = (random.randint(0, (WIDTH//BLOCK_SIZE)-1) * BLOCK_SIZE, 
        random.randint(0, (HEIGHT//BLOCK_SIZE)-1) * BLOCK_SIZE)

# Game variables
running = True
clock = pygame.time.Clock()

while running:
    screen.fill(BLACK)

  # Handle events
  for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP and snake_dir != (0, BLOCK_SIZE):
                snake_dir = (0, -BLOCK_SIZE)
            elif event.key == pygame.K_DOWN and snake_dir != (0, -BLOCK_SIZE):
                snake_dir = (0, BLOCK_SIZE)
            elif event.key == pygame.K_LEFT and snake_dir != (BLOCK_SIZE, 0):
                snake_dir = (-BLOCK_SIZE, 0)
            elif event.key == pygame.K_RIGHT and snake_dir != (-BLOCK_SIZE, 0):
                snake_dir = (BLOCK_SIZE, 0)

 # Move the snake
snake.insert(0, new_head)
# Check if snake eats food
if new_head == food:
        food = (random.randint(0, (WIDTH//BLOCK_SIZE)-1) * BLOCK_SIZE, 
                random.randint(0, (HEIGHT//BLOCK_SIZE)-1) * BLOCK_SIZE)
    else:
        snake.pop()
# Draw snake and food
 for block in snake:
        pygame.draw.rect(screen, GREEN, (block[0], block[1], BLOCK_SIZE, BLOCK_SIZE))
    pygame.draw.rect(screen, RED, (food[0], food[1], BLOCK_SIZE, BLOCK_SIZE))
    pygame.display.update()
    clock.tick(7)  # **Slows down the game**

# Show Game Over Message
font = pygame.font.Font(None, 36)
text = font.render("Game Over! Press any key to exit.", True, WHITE)
screen.blit(text, (WIDTH//6, HEIGHT//2))
pygame.display.update()

# Wait for user to press a key before closing
pygame.time.delay(2000)  # Wait for 2 seconds
pygame.quit()
