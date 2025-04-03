local function otimizarGraficos()
    local lighting = game:GetService("Lighting")
    local terrain = workspace:FindFirstChildOfClass("Terrain")
    local player = game:GetService("Players").LocalPlayer
    local settings = settings() -- Configurações do jogo

    -- Ajusta as configurações de iluminação para reduzir efeitos pesados
    lighting.GlobalShadows = false -- Remove sombras globais
    lighting.FogEnd = 500 -- Reduz a distância do nevoeiro
    lighting.Brightness = 1 -- Mantém um brilho adequado

    -- Reduz a qualidade do terreno
    if terrain then
        terrain.WaterWaveSize = 0
        terrain.WaterWaveSpeed = 0
        terrain.WaterReflectance = 0
        terrain.WaterTransparency = 1 -- Deixa a água transparente para reduzir carga gráfica
    end

    -- Ajusta configurações gráficas do cliente
    if player then
        local success, err = pcall(function()
            settings.RenderSettings.QualityLevel = Enum.QualityLevel.Level1 -- Reduz a qualidade dos gráficos
        end)
        if not success then
            warn("Não foi possível ajustar a qualidade dos gráficos:", err)
        end
    end

    print("Configurações gráficas otimizadas para melhor desempenho!")
end

-- Executa a otimização
otimizarGraficos()
