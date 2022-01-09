local settings = {
    Comp = false,
    Buy = false,
    Delay = 5
    
}
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
Mainz = main:Tab('Main')


Mainz:Toggle('Auto-Buy',function(state)
settings.Buy = state
end)

  Mainz:Slider('Auto-Complete Delay (seconds)',0,5,function(num)
    settings.Delay = num
  end)
    
Mainz:Toggle('Auto-Complete',function(state)
settings.Comp = state
end)


spawn(function()
while task.wait(settings.Delay) do
    if settings.Comp then
     if game:GetService("Workspace").Gifts:FindFirstChild("Gift") then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Gifts.Gift.Position)
end
    if game:GetService("Players").LocalPlayer.leaderstats.Stage.Value == 181 then
game:GetService("ReplicatedStorage").Remotes.Rebirth:InvokeServer(5)
    end
end
end
end)

spawn(function()
   while task.wait() do
       if settings.Buy then
           game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Visible = false
for _,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Sections.Tags.Grid:GetChildren()) do
    game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Visible = false
    game:GetService("ReplicatedStorage").Remotes.BuyTag:InvokeServer(v.Name)
end
for _,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Sections.Trails.Grid:GetChildren()) do
    game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Visible = false
    game:GetService("ReplicatedStorage").Remotes.BuyTrail:InvokeServer(v.Name)
end
for _,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Sections.Halos.Grid:GetChildren()) do
    game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Visible = false
    game:GetService("ReplicatedStorage").Remotes.BuyHalo:InvokeServer(v.Name)
end
for _,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Sections.Pets.Grid:GetChildren()) do
    game:GetService("Players").LocalPlayer.PlayerGui.MainGUI.Shop.Visible = false
    game:GetService("ReplicatedStorage").Remotes.BuyPet:InvokeServer(v.Name)
end
end
end
    
end)

Mainz:Button('+ 1 Skip',function()
    if game:GetService("Workspace").Gifts:FindFirstChild("Gift") then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Gifts.Gift.Position)
else
    game.Players.LocalPlayer:Kick('It seems the script may be patched or you are already max stage')
end
end)

Mainz:Button('+ 5 Skip',function()
local Goal = game:GetService("Players").LocalPlayer.leaderstats.Stage.Value + 5
repeat
    if game:GetService("Workspace").Gifts:FindFirstChild("Gift") then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Gifts.Gift.Position)
else
    game.Players.LocalPlayer:Kick('It seems the script may be patched or you are already max stage')
end wait()
until game:GetService("Players").LocalPlayer.leaderstats.Stage.Value == Goal

end)
