-- Script básico para coletar informações de personagens em Blox Fruits
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Exibir informações básicas
print("Nome do Jogador: " .. player.Name)
print("Nível: " .. player.Data.Level.Value)
print("Beli: " .. player.Data.Beli.Value)

-- Função para verificar status do personagem
local function checkStatus()
    if character:FindFirstChild("Health") then
        print("Vida: " .. character.Health)
    else
        print("Vida: Indisponível")
    end
end

-- Chamar a função checkStatus
checkStatus()

-- Adiciona uma função ao evento CharacterAdded para monitorar alterações no status do personagem
player.CharacterAdded:Connect(function(newCharacter)
    character = newCharacter
    checkStatus()
end)
