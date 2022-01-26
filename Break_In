local Client = {
     toggles = {
        WST = false,
        JPT = false,
        Killbaddies = false
    }
}


local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
Mainz = main:Tab('Combat')
Character = main:Tab('Character')
Trolling = main:Tab('Troll')

Mainz:Toggle("Kill All Baddies", function(state)
Client.toggles.Killbaddies = state
end)


Character:Button("Commit Plan: No Father (Semi-God)", function(state)
game:GetService("ReplicatedStorage").RemoteEvents.MakeStealth:FireServer(9999999) -- should give godmode
end)

Trolling:Textbox("Drown Specific Player", true, function(Text)
    if game:GetService("Players")[Text] then
        game:GetService("ReplicatedStorage").RemoteEvents.ToxicDrown:FireServer(1, game:GetService("Players")[Text])
    end
end)

Trolling:Button("Commit the llorona (Drown All Players)", function(state)
for _,v in pairs(game.Players:GetPlayers()) do
    if v ~= game.Players.LocalPlayer then
        game:GetService("ReplicatedStorage").RemoteEvents.ToxicDrown:FireServer(1, v)
    end
end
end)

Character:Button("Commit Tax Fraud (Attempt To trigger all events)", function(state)
local Pos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
for _,v in pairs(game:GetService("ReplicatedStorage").RemoteEvents:GetChildren()) do -- could cause all player godmode / can break game
    v:FireServer(999999999, "Success!")
end
wait(2)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Pos)
end)

Character:Toggle("WalkSpeed Toggle", function(state)
Client.toggles.WST = state

end)

Character:Slider('WalkSpeed Value',16,150,function(num)
if Client.toggles.WST then
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = num
    end
end)

Character:Toggle("JumpPower Toggle", function(state)
Client.toggles.JPT = state
end)

Character:Slider('WalkSpeed Value',16,150,function(num)
if Client.toggles.JPT then
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = num
    end
end)


Trolling:Textbox("Play Audio (ID)", true, function(Text)
    print('yes')
local a = "rbxassetid://" .. tostring(Text) -- soundwwwwwwww
local b = false -- random shit idk
local c = 69 -- volume (really you can only do 1,10 but fuck u)
local d = "trolling57"

game:GetService("ReplicatedStorage").RemoteEvents.Sounds:FireServer(a, b, c, d)
end)


Trolling:Dropdown(
"Give Item",{'TeddyBloxpin','BloxyCola', "Plank", "Chips", "Cure", "MedKit", "Cookie", "Bat", "Pan", "Apple", "Pie"}, function(selected)
    game:GetService("ReplicatedStorage").RemoteEvents.GiveTool:FireServer(selected)
end)

spawn(function() 
    while task.wait(.45) do
if Client.toggles.Killbaddies then
    for _,v in pairs(workspace.BadGuys:GetChildren()) do
local ohInstance1 = v
local ohNumber2 = 10

game:GetService("ReplicatedStorage").RemoteEvents.HitBadguy:FireServer(ohInstance1, ohNumber2)
end
end
end
end)
