--Give credits if u use anything :3
--this code is messy :rolling_eyes:

repeat pcall(function()
    wait()
    BulletClient = getconnections(game:GetService("ReplicatedStorage")["RS_Package"].Assets.Remotes.Bullet.OnClientEvent)[1].Function
    FuncNew = getupvalue(BulletClient,3).new
    RemoteKey = getupvalue(FuncNew,18)
end) until BulletClient
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()

Client = {
    Toggles = {
        KillAllPolice = false,
        InfStamina = false,
        InfAmmo = false
    }
}

MainW = main:Tab('Main')
MainW:Toggle('Kill All Police',function(state)
    Client.Toggles.KillAllPolice = state
end)
MainW:Toggle('Inf Stamina',function(state)
    Client.Toggles.InfStamina = state
end)
MainW:Toggle('Inf Ammo',function(state)
    Client.Toggles.InfAmmo = state
end)
MainW:Button('Destroy All Cameras',function()
    for i,v in pairs(game:GetService("Workspace").Cameras:GetChildren()) do
        local v1 = RemoteKey
        local v2 = v:FindFirstChildOfClass('MeshPart')
        local v3 = false
        local v4 = nil
        local v5 = nil
        local v6 = Vector3.new(3.02631664, 2.68741488, 3.29028654)
        game:GetService("ReplicatedStorage")["RS_Package"].Assets.Remotes.HitObject:FireServer(v1, v2, v3, v4, v5, v6)
    end
    game:GetService("Players").LocalPlayer.PlayerGui["SG_Package"].MainGui.Events.CasingError:Fire(' [ DARK HUB ] - Cameras Destroyed')
end)
MainW:Button('God Mode',function()
    local v1 = "Damage"
    local v2 = RemoteKey
    local v3 = game:GetService("Players").LocalPlayer.Character.Humanoid
    local v4 = -9000000000
    local v5 = game:GetService("Players").LocalPlayer.Character.Head
    local v6 = "Knife"
    local v7 = Vector3.new(-4.93716431, -0.482243985, -0.680375397)
    local event = game:GetService("ReplicatedStorage")["RS_Package"].Assets.Remotes.Damage
    event:FireServer(v1, v2, v3, v4, v5, v6, v7)
    game:GetService("Players").LocalPlayer.PlayerGui["SG_Package"].MainGui.Events.CasingError:Fire(' [ DARK HUB ] - Godded LocalPlayer')
end)
--[[
MainW:Button('Grab Lootables',function()
    for i = 1,10 do
        wait(.3)
        game:GetService("Players").LocalPlayer.PlayerGui["SG_Package"].MainGui.Events.CasingError:Fire(' [ DARK HUB ] - GRABBING LOOTABLES')
        for i,v in pairs(game:GetService("Workspace").Lootables:GetChildren()) do
            if v:FindFirstChildOfClass('Part') then
                game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(v:FindFirstChildOfClass('Part').Position))
                game:GetService("ReplicatedStorage")["RS_Package"].Remotes.StartInteraction:FireServer(v)
                game:GetService("ReplicatedStorage")["RS_Package"].Remotes.CompleteInteraction:FireServer(v)
            end
            if v:FindFirstChildOfClass('Model') and string.match(v:FindFirstChildOfClass('Model').Name,'Jewels') then
                game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(v:FindFirstChildOfClass('Model'):FindFirstChildOfClass('Part').Position))
                game:GetService("ReplicatedStorage")["RS_Package"].Remotes.StartInteraction:FireServer(v:FindFirstChildOfClass('Model'))
                game:GetService("ReplicatedStorage")["RS_Package"].Remotes.CompleteInteraction:FireServer(v:FindFirstChildOfClass('Model'))
            end
        end
    end
    game:GetService("Players").LocalPlayer.PlayerGui["SG_Package"].MainGui.Events.CasingError:Fire(' [ DARK HUB ] - COMPLETE')
end)
]]
--[[
MainW:Button('Put Bags In Van',function()
    game:GetService("Players").LocalPlayer.PlayerGui["SG_Package"].MainGui.Events.CasingError:Fire(' [ DARK HUB ] - Transporting Bags... Please dont move until complete')
    game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(game:GetService("Workspace").BagSecuredArea.PrimaryPart.Position + Vector3.new(0,6,0)))
    wait(1)
    local v1 = CFrame.new(game.Workspace.CurrentCamera.CFrame.p,game:GetService("Workspace").BagSecuredArea.PrimaryPart.Position).lookVector
    local event = game:GetService("ReplicatedStorage")["RS_Package"].Remotes.ThrowBag
    event:FireServer(v1)
    game:GetService("Players").LocalPlayer.PlayerGui["SG_Package"].MainGui.Events.CasingError:Fire(' [ DARK HUB ] - Transporting Bags Complete')
end)
]]
spawn(function()
    while true do wait()
        pcall(function()
            if Client.Toggles.KillAllPolice then
                for i,v in pairs(game:GetService("Workspace").Police:GetChildren()) do
                    if v:FindFirstChild('HumanoidRootPart') and v:FindFirstChild('Humanoid') then
                        local v1 = "Damage"
                        local v2 = RemoteKey
                        local v3 = v.Humanoid
                        local v4 = 110
                        local v5 = v.HumanoidRootPart
                        local v6 = "M16"
                        local v7 = Vector3.new(-4.93716431, -0.482243985, -0.680375397)
                        game:GetService("ReplicatedStorage")["RS_Package"].Assets.Remotes.Damage:FireServer(v1, v2, v3, v4, v5, v6, v7)
                    end
                end
            end
            if Client.Toggles.InfStamina then
                if game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild('Stamina') and game.Players.LocalPlayer.Character:FindFirstChild('MaxStamina') then
                    game.Players.LocalPlayer.Character.Stamina.Value = game.Players.LocalPlayer.Character.MaxStamina.Value
                end
            end
        end)
    end
end)

GameMT = getrawmetatable(game)
setreadonly(GameMT,false)
OldNC = GameMT.__namecall
GameMT.__namecall = function(self,...)
    if getnamecallmethod() == 'FireServer' and tostring(self) == 'Bullet' and Client.Toggles.InfAmmo then
        Args = {...}
        if Args[1] and Args[1]['UseAmmo'] then
            Args[1]['UseAmmo'] = false
        end
        return OldNC(self,unpack(Args))
    end
    return OldNC(self,...) 
end

game:GetService("Players").LocalPlayer.PlayerGui["SG_Package"].MainGui.Events.CasingError:Fire('~ DARKHUB LOADED ~')
