-- Cria um leaderboard para acompanhar as moedas coletadas
game.Players.PlayerAdded:Connect(function(player)
    local leaderstats = Instance.new("Folder")
    leaderstats.Name = "leaderstats"
    leaderstats.Parent = player
    
    local coins = Instance.new("IntValue")
    coins.Name = "Coins"
    coins.Value = 0
    coins.Parent = leaderstats
end)

-- Função para dar moedas quando o jogador toca na moeda
local function onTouched(part)
    local character = part.Parent
    local player = game.Players:GetPlayerFromCharacter(character)
    
    if player then
        local leaderstats = player:FindFirstChild("leaderstats")
        if leaderstats then
            local coins = leaderstats:FindFirstChild("Coins")
            if coins then
                coins.Value = coins.Value + 1
                part:Destroy() -- Remove a moeda após coleta
            end
        end
    end
end

-- Criar moedas no mapa
task.wait(2) -- Espera um pouco antes de criar as moedas
for i = 1, 10 do
    local coin = Instance.new("Part")
    coin.Size = Vector3.new(2, 2, 2)
    coin.Shape = Enum.PartType.Ball
    coin.BrickColor = BrickColor.new("Bright yellow")
    coin.Position = Vector3.new(math.random(-50, 50), 5, math.random(-50, 50))
    coin.Anchored = false
    coin.Parent = game.Workspace
    
    coin.Touched:Connect(onTouched)
end
