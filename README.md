-- Configurações do autorob
getgenv().FlySpeed = 260
getgenv().Team = "Prisoners"
getgenv().TimeToLoad = 2

-- Carrega o autorob a partir da URL
loadstring(game:HttpGet("https://raw.githubusercontent.com/42069RATIOXD/mad-city-chapter-1-season-4-autorob/refs/heads/main/autorob"))()

-- Script de noclip automático
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Garante que o personagem foi totalmente carregado
character:WaitForChild("HumanoidRootPart")

local noclipEnabled = true  -- Noclip ativado por padrão

-- Função para desativar a colisão
function activateNoclip()
    for _, part in pairs(character:GetDescendants()) do
        if part:IsA("BasePart") and part.CanCollide then
            part.CanCollide = false
        end
    end
end

-- Atualiza o estado do noclip a cada tick
game:GetService("RunService").Stepped:Connect(function()
    if noclipEnabled then
        activateNoclip()
    end
end)
