# Initialisation de Pygame
pygame.init()

# Définition des couleurs
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)

# Définition de la taille de l'écran
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Pixel Quest")

# Chargement des images (remplacez ces fichiers par vos propres sprites)
player_image = pygame.Surface((50, 50))
player_image.fill(WHITE)
player_rect = player_image.get_rect()

# Définition de la vitesse du joueur
player_speed = 5

# Boucle principale du jeu
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Déplacement du joueur
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        player_rect.x -= player_speed
    if keys[pygame.K_RIGHT]:
        player_rect.x += player_speed
    if keys[pygame.K_UP]:
        player_rect.y -= player_speed
    if keys[pygame.K_DOWN]:
        player_rect.y += player_speed

    # Limitation de la position du joueur à l'écran
    player_rect.x = max(0, min(WIDTH - player_rect.width, player_rect.x))
    player_rect.y = max(0, min(HEIGHT - player_rect.height, player_rect.y))

    # Dessin de l'écran
    screen.fill(BLACK)
    screen.blit(player_image, player_rect)

    # Mise à jour de l'écran
    pygame.display.flip()
