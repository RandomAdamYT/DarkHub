local Settings = {
    Godmode = false,
    KillAura = false,
    Range = 10
}

local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
local Window = Lib:Window()
local Main = Window:Tab('Main')
local Char = Window:Tab('Character')

Main:Toggle('Slap-Aura', function(state)
    Settings.KillAura = state
end)

Main:Slider('Custom Range', 10, 30, function(num)
    Settings.Range = num
end)


local function getNPlayer()
    local TargetDistance = math.huge
    local Target
    for i, v in ipairs(game.Players:GetPlayers()) do
        if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("entered") then -- This will detect if the player is in lobby or has godmode and then will not target
            local Mag = (game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position - v.Character:FindFirstChild("HumanoidRootPart").Position).Magnitude
            if Mag < TargetDistance then
                TargetDistance = Mag
                Target = v
            end
        end
    end
    return Target
end;
spawn(function()
    while task.wait(.23) do
        pcall(function()
            for _,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                if Settings.KillAura then
                    if string.find(v.Name, game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name) and v.Name ~= "Defualt" and (game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position - getNPlayer().Character:FindFirstChild("HumanoidRootPart").Position).Magnitude <= Settings.Range then
                        game:GetService("ReplicatedStorage")[v.Name]:FireServer(getNPlayer().Character.HumanoidRootPart)
                            else
                        game:GetService("ReplicatedStorage").b:FireServer(getNPlayer().Character.HumanoidRootPart)
                    end
                end
            end
        end)
    end
end)

Char:Toggle('Semi-God', function(state)
    Settings.Godmode = state
end)
spawn(function()
while task.wait() do
    if Settings.Godmode then
    repeat wait() until game.Players.LocalPlayer.Character:FindFirstChild("entered")
        for _,v in ipairs(game.Players.LocalPlayer.Character:GetChildren()) do
            if v.ClassName == "BoolValue" and v.Name ~= "Ragdolled" then
                v:Destroy()
            end
        end
    end
end    
end)


Char:Slider('Custom WalkSpeed', 16, 100, function(num)
if game:GetService("Players").LocalPlayer.PlayerScripts:FindFirstChild("WSC") then
    game:GetService("Players").LocalPlayer.PlayerScripts:FindFirstChild("WSC").Disabled = true
end
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = num
end)

Char:Slider('Custom JumpPower', 50, 100, function(num)
if game:GetService("Players").LocalPlayer.PlayerScripts:FindFirstChild("WSC") then
    game:GetService("Players").LocalPlayer.PlayerScripts:FindFirstChild("WSC").Disabled = true
end
game.Players.LocalPlayer.Character.Humanoid.JumpPower = num
end)
