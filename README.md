##### HalloweenFantasy

  #난이도
  def selectDifficulty():
      global gamePad
      font = pygame.font.Font('neodgm.ttf', 20) 
      
      while True:
          for event in pygame.event.get():
              if event.type == pygame.QUIT:
                  pygame.quit()
                  sys.exit()
              
              if event.type == pygame.KEYDOWN:
                  if event.key == pygame.K_n:  # 노말 모드 선택
                      return '노말'
                  elif event.key == pygame.K_h:  # 하드 모드 선택
                      return '하드'

=========================================================================================================================

  #시작화면
  def startMessage(text):
      global gamePad
      textfont = pygame.font.Font('neodgm.ttf', 35)                  # 폰트는 35px
      text = textfont.render(text, True, (255,255,255))                     # 게임 오버 시 나오는 텍스트 출력. 색은 흰색
      textpos = text.get_rect()
      textpos.center = (padWidth/2, 500)
      gamePad.blit(text, textpos)                                         # text와 textpos 변수 화면에 출력
      pygame.display.update()                                             # 그 후에 화면을 한번 업데이트 한다.
      pygame.mixer.music.stop()                                           # 배경음악 정지           



=========================================================================================================================

    # 안개 랜덤 생성
    fog = pygame.image.load(random.choice(fogImage))
    fogSize = fog.get_rect().size                                                        
    fogWidth = fogSize[0]
    fogHeight = fogSize[1]
    
    # 안개 랜덤 생성
    fog02 = pygame.image.load(random.choice(fog02Image))
    fog02Size = fog02.get_rect().size                                                        
    fog02Width = fog02Size[0]
    fog02Height02 = fog02Size[1]
    
    # 안개 랜덤 생성
    fog03 = pygame.image.load(random.choice(fog03Image))
    fog03Size = fog03.get_rect().size                                                        
    fog03Width = fog03Size[0]
    fog03Height = fog03Size[1]

=========================================================================================================================

    # 안개 초기 위치 설정
    fogX = random.randrange(0, padWidth - (fogWidth+80))
    fogY = 0
    fogSpeed = 4
    
    # 안개 초기 위치 설정
    fog02X = random.randrange(0, padWidth - (fog02Width-40))
    fog02Y = -30
    fog02Speed = 3
    
    # 안개 초기 위치 설정
    fog03X = random.randrange(0, padWidth - (fog03Width+50))
    fog03Y = -50
    fog03Speed = 4

=========================================================================================================================

    # 새로운 적(랜덤)
    enemy = pygame.image.load(random.choice(enemyImage))
    enemySize = enemy.get_rect().size # 적 크기
    enemyWidth = enemySize[0]
    enemyHeight = enemySize[1]
    enemyX = random.randrange(0, padWidth - enemyWidth)
    enemyY = 0
    destroySound = pygame.mixer.Sound(random.choice(explosionSound))  
    num_lives -= 1
    if num_lives == 0:
        gameOver()
    else:
        drawLives(num_lives)        #목숨 그림 감소
