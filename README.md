-- Voidqzxy Hub Auto Farm Script para Dragon Blox Ultimate

-- Configuração inicial
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Criar GUI
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local AutoFarmButton = Instance.new("TextButton")

ScreenGui.Name = "VoidqzxyHub"
ScreenGui.Parent = game.CoreGui

Frame.Size = UDim2.new(0, 200, 0, 300)
Frame.Position = UDim2.new(0.5, -100, 0.5, -150)
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Parent = ScreenGui

AutoFarmButton.Size = UDim2.new(0, 180, 0, 50)
AutoFarmButton.Position = UDim2.new(0, 10, 0, 10)
AutoFarmButton.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
AutoFarmButton.Text = "Auto Farm"
AutoFarmButton.Parent = Frame

local farming = false

-- Função de Auto Farm
function autoFarm()
    while farming do
        -- Adicione aqui a lógica para derrotar inimigos ou coletar recursos
        local enemies = game.Workspace:FindFirstChild("Enemies")
        if enemies then
            for _, enemy in pairs(enemies:GetChildren()) do
                if enemy:IsA("Model") and enemy:FindFirstChild("Humanoid") then
                    character.Humanoid:MoveTo(enemy.HumanoidRootPart.Position)
                    wait(1) -- Espera 1 segundo antes de continuar o ataque
                    -- Código para atacar o inimigo
                end
            end
        end
        wait(5) -- Espera 5 segundos antes de repetir a ação
    end
end

-- Conectar botão Auto Farm
AutoFarmButton.MouseButton1Click:Connect(function()
    farming = not farming
    if farming then
        AutoFarmButton.Text = "Parar Auto Farm"
        autoFarm()
    else
        AutoFarmButton.Text = "Auto Farm"
    end
end)
