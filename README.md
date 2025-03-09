import pygame

# Inicializa o Pygame
pygame.init()

# Configurações da tela
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Aventura do Herói")

# Cores
WHITE = (255, 255, 255)
BLUE = (0, 0, 255)
GREEN = (0, 255, 0)
RED = (255, 0, 0)

# Configuração do personagem
player_size = 40
player_x, player_y = 50, HEIGHT // 2
player_speed = 5

# Configuração do objetivo
goal_size = 40
goal_x, goal_y = WIDTH - 80, HEIGHT // 2

# Configuração do obstáculo
obstacle_x, obstacle_y = WIDTH // 2, HEIGHT // 2
obstacle_width, obstacle_height = 100, 100

# Loop principal
going = True
while going:
    pygame.time.delay(30)
    
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            going = False
    
    # Movimentação
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        player_x -= player_speed
    if keys[pygame.K_RIGHT]:
        player_x += player_speed
    if keys[pygame.K_UP]:
        player_y -= player_speed
    if keys[pygame.K_DOWN]:
        player_y += player_speed
    
    # Checa colisão com o objetivo
    if (player_x < goal_x + goal_size and player_x + player_size > goal_x and
        player_y < goal_y + goal_size and player_y + player_size > goal_y):
        print("Você venceu!")
        going = False
    
    # Checa colisão com obstáculo
    if (player_x < obstacle_x + obstacle_width and player_x + player_size > obstacle_x and
        player_y < obstacle_y + obstacle_height and player_y + player_size > obstacle_y):
        print("Você bateu em um obstáculo!")
        player_x, player_y = 50, HEIGHT // 2  # Reinicia posição
    
    # Limpa a tela e desenha os elementos
    screen.fill(WHITE)
    pygame.draw.rect(screen, BLUE, (player_x, player_y, player_size, player_size))  # Personagem
    pygame.draw.rect(screen, GREEN, (goal_x, goal_y, goal_size, goal_size))  # Objetivo
    pygame.draw.rect(screen, RED, (obstacle_x, obstacle_y, obstacle_width, obstacle_height))  # Obstáculo
    pygame.display.update()

pygame.quit()
