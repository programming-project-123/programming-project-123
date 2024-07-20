import pygame 

pygame.init() 
screen = pygame.display.set_mode((1200, 500))
clock =  pygame.time.Clock()
running = True
dt = 0

player_pos = pygame.Vector2(screen.get_width() / 2, screen.get_height() / 2) 
circle_position=[]

while running:
    for event in pygame.event.get():    
        if event.type == pygame.QUIT:
            running = False
        
        

    screen.fill("black")

    pygame.draw.circle(screen, "red", player_pos, 40)

    keys = pygame.key.get_pressed()
    if  keys[pygame.K_w]:
        player_pos.y -= 300 * dt
    if  keys[pygame.K_s]:
        player_pos.y += 300 * dt
    if  keys[pygame.K_a]:
        player_pos.x -= 300 * dt
    if  keys[pygame.K_d]:
        player_pos.x += 300  * dt
    if  keys[pygame.K_SPACE ]:
            circle_position.append(player_pos.copy())

    for pos in circle_position:
         pygame.draw.circle(screen,"red", pos, 40)
    
    pygame.display.flip()


    dt = clock.tick(60)/1000

pygame.quit()

