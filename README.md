function love.load()
    -- Define as dimensões da janela
    love.window.setMode(800, 600)
    
    -- Configuração do botão flutuante
    button = {
        x = 700,  -- Posição X do botão
        y = 500,  -- Posição Y do botão
        width = 80,  -- Largura do botão
        height = 40, -- Altura do botão
        color = {0.2, 0.6, 1}, -- Cor Azul
        targetX = 400,  -- Coordenada X onde o clique será simulado
        targetY = 300   -- Coordenada Y onde o clique será simulado
    }
    
    -- Mensagem de clique
    clickMessage = ""
end

function love.draw()
    -- Desenha o botão
    love.graphics.setColor(button.color)
    love.graphics.rectangle("fill", button.x, button.y, button.width, button.height)
    
    -- Desenha o texto no botão
    love.graphics.setColor(1, 1, 1)
    love.graphics.print("Clique Aqui", button.x + 10, button.y + 12)
    
    -- Exibe mensagem do clique
    love.graphics.setColor(1, 1, 1)
    love.graphics.print(clickMessage, 10, 10)
end

function love.mousepressed(x, y, buttonPressed, istouch, presses)
    if buttonPressed == 1 then  -- Verifica se o botão esquerdo foi pressionado
        
        -- Verifica se o clique foi no botão
        if x >= button.x and x <= button.x + button.width and
           y >= button.y and y <= button.y + button.height then
            
            -- Simula um clique nas coordenadas especificadas
            clickMessage = "Clique simulado em: (" .. button.targetX .. ", " .. button.targetY .. ")"
        end
    end
end
