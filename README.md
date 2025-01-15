while wait(0.1) do
    -- Envia repetidamente o evento remoto para tentar adicionar créditos
    game:GetService("ReplicatedStorage").RemoteEvent:FireServer(16, "credit")

    -- Tenta iterar sobre todos os jogadores no servidor
    for _, player in ipairs(game.Players:GetPlayers()) do
        if player ~= game.Players.LocalPlayer then
            -- Envia o evento remoto para interagir com outros jogadores (simulação de ação no jogo)
            game:GetService("ReplicatedStorage").RemoteEvent:FireServer(30, player)
        end
    end

    -- Adiciona outra tentativa de manipulação diretamente no LocalPlayer
    game:GetService("ReplicatedStorage").RemoteEvent:FireServer(16, "add")
    game:GetService("ReplicatedStorage").RemoteEvent:FireServer(16, "win")
    game:GetService("ReplicatedStorage").RemoteEvent:FireServer(16, "bonus")
end
