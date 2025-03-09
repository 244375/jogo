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

# Configuração do personagem
player_size = 40
player_x, player_y = WIDTH // 2, HEIGHT // 2
player_speed = 5

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
    
    # Limpa a tela e desenha o personagem
    screen.fill(WHITE)
    pygame.draw.rect(screen, BLUE, (player_x, player_y, player_size, player_size))
    pygame.display.update()

pygame.quit()
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

# Configuração do personagem
player_size = 40
player_x, player_y = WIDTH // 2, HEIGHT // 2
player_speed = 5

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
    
    # Limpa a tela e desenha o personagem
    screen.fill(WHITE)
    pygame.draw.rect(screen, BLUE, (player_x, player_y, player_size, player_size))
    pygame.display.update()

pygame.quit()

