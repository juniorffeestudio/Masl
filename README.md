local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

local function toggleAllDoors()
    for _, door in ipairs(workspace:GetChildren()) do
        if door:IsA("Model") and door:FindFirstChild("HingeConstraint") then
            local hinge = door:FindFirstChild("HingeConstraint")
            if hinge then
                hinge.TargetAngle = hinge.TargetAngle == 0 and 90 or 0
            end
        end
    end
end

-- Criar a interface gráfica usando a Orion Library
local Window = OrionLib:MakeWindow({Name = "Whitexhub", HidePremium = false, SaveConfig = true, ConfigFolder = "WhitexhubConfig"})

local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

MainTab:AddButton({
    Name = "Abrir/Fechar Todas as Portas",
    Callback = function()
        toggleAllDoors()
    end
})

OrionLib:Init()
