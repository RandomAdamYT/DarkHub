
local settings = {
    AutoFarm = false,
    God = false,
    NoDmg = false,
    WS = false,
    AutoAtck = false,
    FarmArea = "Primis Field 1"

}



local function getNearestEnemy() -- // Legit says it troll
    local TargetDistance = math.huge
    local Target
    for i, v in ipairs(game:GetService("Workspace").Enemies[settings.FarmArea]:GetChildren()) do
        for _,v2 in ipairs(v:GetChildren()) do
            if v2.ClassName == "Part" and v2.Name == "EnemyLocation" and v2.Parent.InCombat.Value ~= true and not game.Players.LocalPlayer.Character:FindFirstChild("Combat Border") then
                 local Mag = (game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position - v2.Position).Magnitude
                if Mag < TargetDistance then
                    TargetDistance = Mag
                    Target = v
                end
            end
        end
    end
    return Target
end;
spawn(function()
    while task.wait() do
        pcall(function()
            for _,v in ipairs(game:GetService("Workspace"):FindFirstChild("CombatFolder"):GetChildren()) do -- Get our stinky folder shit method but oh well
                 if v.ClassName == "Folder" then
                    if v.Name == game.Players.LocalPlayer.Name then
                        PlayerFolder = v
                    end
                end
            end
        end)
    end
end)

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
Mainz = main:Tab('Main')
Combat = main:Tab('Combat')
LP = main:Tab('LocalPlayer')


        Mainz:Toggle('Toggle WalkSpeed', function(state)
            settings.WS = state
        end)
        
        Mainz:Slider('WalkSpeed Value',30,150,function(num)
            if settings.WS then
                if game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = num
                end
            end
        end)
        
        LP:Button('Open All Chests', function()
for _,v in pairs(game:GetService("Workspace").Chests:GetChildren()) do
    if v.ClassName == "Model" then
        firetouchinterest(v.Giver, game.Players.LocalPlayer.Character.HumanoidRootPart,0)
        wait()
        firetouchinterest(v.Giver, game.Players.LocalPlayer.Character.HumanoidRootPart,1)
    end
end
        
        end)
        
        LP:Toggle('Godmode', function(state)
           settings.God = state
        end)
        
            local wow2 = {} -- table that will be used later
    
    for _,v in pairs(game:GetService("Workspace").Statues:GetChildren()) do -- Smack all the areas into a table
    table.insert(wow2,v.Name)
    end
    

    LP:Dropdown('Teleport 2 Statue',wow2,function(Sele)
       game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Statues[Sele].Orb.Position)
    end)
    
               local wow3 = {} -- table that will be used later
    
    for _,v in pairs(game:GetService("Workspace").Spawns:GetChildren()) do -- Smack all the areas into a table
    table.insert(wow3,v.Name)
    end
    

    LP:Dropdown('Teleport 2 Spawns',wow3,function(Sele)
       game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Spawns[Sele].Position)
    end)
        


        local OldNameCall 
    OldNameCall = hookmetamethod(game, "__namecall", function(self,...) 
        local args = {...}
        if tostring(self) == "Damage" and getnamecallmethod() == "FireServer" and settings.God then -- Check for Damage and that it gets called with FireServer showing that its a RemoteEvent
            if args[3] == "Enemy" then -- Are we taking damage from the NPC?
                return wait() -- Stop for a second I need to do something
            end
        end
    
        return OldNameCall(self,...)
    end)
    
    local wow = {} -- table that will be used later
    
    for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do -- Smack all the areas into a table
    table.insert(wow,v.Name)
    end
    

    Combat:Dropdown('Area ( What Island Do You wanna Farm? )',wow,function(Sele)
        settings.FarmArea = Sele
    end)

    Combat:Toggle('Auto-Sword ( Auto-Attack Enemy ) ', function(state)
        settings.AutoAtck = state
    end)
        
spawn(function()
    while task.wait(.45) do
        pcall(function()
            for _,v in pairs(PlayerFolder:GetChildren()) do
                for _,v2 in pairs(v:GetChildren()) do
                     if v2.Name == "Base" and settings.AutoAtck then -- sort for base
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v2.Position) -- teleport to bases
                     end
                end
            end
        end)
    end
end)

    Combat:Toggle('Auto-Farm', function(state)
         settings.AutoFarm = state
    end)
    spawn(function()
        while task.wait() do
            pcall(function()
                if settings.AutoFarm and not game.Players.LocalPlayer.Character:FindFirstChild("Combat Border") then -- are we fighting and what not?
                    wait(.11)
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getNearestEnemy().EnemyLocation.Position)
                    wait(.11)
                        game.Players.LocalPlayer.Character.Humanoid.Jump = true
                end
            end)
        end
    end)

print('loaded')
