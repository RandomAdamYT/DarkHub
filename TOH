y = game:GetService("Players").LocalPlayer.PlayerScripts.LocalScript
getsenv(y).kick = function() return nil end
getsenv(y).kick()

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
local MainWindow = main:Tab('Main')
TimeAlive = 0

MainWindow:Button('Instant Top',function()
    if game.Players.LocalPlayer.Character:FindFirstChild('ForceField') or TimeAlive < 1 then
        return    
    end
    local temp_table = {}
    for i,v in pairs(game:GetService("Workspace").tower:GetDescendants()) do
        if v:IsA('Part') and v.CanCollide == true then
            table.insert(temp_table,v)
            v.CanCollide = false
        end
    end
    Me = game.Players.LocalPlayer.Character
    Old = Me.KillScript.Disabled
    Me.Humanoid.Jump = true
    for i = 1,300 do
        wait()
        Me.KillScript.Disabled = true
        Me.HumanoidRootPart.Velocity = Vector3.new(0,4000,0)
        o = game:GetService("Workspace").tower.sections.finish.exit.ParticleBrick.Position.Y
        e = game.Players.LocalPlayer.Character.HumanoidRootPart.Position.Y
        x = o - e
        if x < 5 then
            Me.HumanoidRootPart.Velocity = Vector3.new(0,0,0)
            Me.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").tower.sections.finish.exit.carpet.CFrame.X,game:GetService("Workspace").tower.sections.finish.exit.carpet.CFrame.Y + 3,game:GetService("Workspace").tower.sections.finish.exit.carpet.CFrame.Z)
            break
        end
    end
    for i,v in pairs(temp_table) do
        v.CanCollide = true
    end
    Me.KillScript.Disabled = Old
end)

MainWindow:Toggle('Godmode',function(state)
    if state == true then
        require(game:GetService("ReplicatedStorage").Mutators.invincibility).mutate()
    else
        require(game:GetService("ReplicatedStorage").Mutators.invincibility).revert()
    end
end)
MainWindow:Toggle('Double Jump',function(state)
    if state == true then
        require(game:GetService("ReplicatedStorage").Mutators["double jump"]).mutate()
    else
        require(game:GetService("ReplicatedStorage").Mutators["double jump"]).revert()
    end
end)
MainWindow:Button('Get All Items',function()
    for i,v in pairs(game:GetService("ReplicatedStorage").Gear:GetChildren()) do
        New = v:Clone()
        New.Parent = game.Players.LocalPlayer.Backpack
    end
end)

MainWindow:Slider('Speed',1,91,function(val)
    game:GetService("ReplicatedStorage").globalSpeed.Value = val
end)

MainWindow:Toggle('Gravity',function(state)
    if state == true then
        require(game:GetService("ReplicatedStorage").Mutators.gravity).mutate()
    else
        require(game:GetService("ReplicatedStorage").Mutators.gravity).revert()
    end
end)

workspace.ChildAdded:Connect(function(child)
    if child.Name == game.Players.LocalPlayer.Character.Name then
        TimeAlive = 0
    end
end)

spawn(function()
    pcall(function()
        while true do
            wait(1)
            TimeAlive = TimeAlive + 1
        end
    end)
end)
