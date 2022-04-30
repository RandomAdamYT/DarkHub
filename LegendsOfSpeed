
--[[
	we 𐎠re tr𐏑v5 𐏃𐎢𐎲 𐎠nd 𐎭rk 𐏃𐎢𐎲
]] 

--[[Tabs and Uilib]]--
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
local main = lib:Window()
local AutoW = main:Tab("AutoFarm")
local AutoBuyW = main:Tab("AutoBuy")
local PlayerW = main:Tab("LocalPlayer")
local MiscW = main:Tab("Misc")

--[[Config]]--
Config = {
    AutoFarm = {
        AutoOrbFarm = false,
        AutoXpFarm = false,
        AutoHoopFarm = false,
        AutoGemFarm = false,
        AutoRebirth = false
    },
    AutoBuy = {
        SelectedCrystal = "",
        AutoBuyCrystal = false
    },
    Player = {
        InfJump = false
    },
}

--[[Functions And Controls]]--
task.spawn(function()
    while true do
        task.wait()
            if Config.AutoFarm.AutoOrbFarm == true then
                game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer("collectOrb", "Red Orb", "City")
                game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer("collectOrb", "Blue Orb", "City")
                game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer("collectOrb", "Orange Orb", "City")
        end
    end
end)

task.spawn(function()
    while true do
        task.wait()
            if Config.AutoFarm.AutoHoopFarm == true then
                for i, v in pairs(workspace.Hoops:GetChildren()) do -- Bye...#0001 Is Hot
                    if v.Name == "Hoop" then
                        v.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
                    end
                end
            task.wait(0.5)
            for i, v in pairs(workspace.Hoops:GetChildren()) do
                if v.Name == "Hoop" then
                    v.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0,100,0)
                end
            end
        end
    end
end)

game:GetService("UserInputService").JumpRequest:connect(function()
    if Config.Player.InfJump then
        game:GetService"Players".LocalPlayer.Character:FindFirstChildOfClass'Humanoid':ChangeState("Jumping")
    end
end)


task.spawn(function()
    while true do
        task.wait()
            if Config.AutoFarm.AutoXpFarm == true then
                game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer("collectOrb", "Yellow Orb", "City")
        end
    end
end)

task.spawn(function()
    while true do
        task.wait()
            if Config.AutoFarm.AutoGemFarm == true then
                game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer("collectOrb", "Gem", "City")
        end
    end
end)

task.spawn(function()
    while true do
        task.wait()
            if Config.AutoFarm.AutoRebirth == true then
                game:GetService("ReplicatedStorage").rEvents.rebirthEvent:FireServer("rebirthRequest")
        end
    end
end)

local Crystal = {
    "Red Crystal",
    "Blue Crystal",
    "purple Crystal",
    "Lightning Crystal",
    "Snow Crystal",
    "Inferno Crystal",
    "Lava Crystal",
    "Electro Legends Crystal"
} -- FrontMan#9917 Is Hotter the Sun UwU


task.spawn(function()
    while true do
        task.wait()
            if Config.AutoBuy.AutoBuyCrystal == true then
                game:GetService("ReplicatedStorage").rEvents.openCrystalRemote:InvokeServer("openCrystal", Config.AutoBuy.SelectedCrystal)
        end
    end
end)

--// Fly script From Fat IY

 function getRoot(char)
    local rootPart = char:FindFirstChild('HumanoidRootPart') or char:FindFirstChild('Torso') or char:FindFirstChild('UpperTorso')
    return rootPart
    end
    local Players = game:GetService("Players")
     local IYMouse = game:GetService("Players").LocalPlayer:GetMouse()
     FLYING = false
        QEfly = true
        iyflyspeed = 1
        vehicleflyspeed = 1
        function sFLY(vfly)
        repeat wait() until Players.LocalPlayer and Players.LocalPlayer.Character and getRoot(Players.LocalPlayer.Character) and Players.LocalPlayer.Character:FindFirstChild('Humanoid')
        repeat wait() until IYMouse
        if flyKeyDown or flyKeyUp then flyKeyDown:Disconnect() flyKeyUp:Disconnect() end
    
        local T = getRoot(Players.LocalPlayer.Character)
        local CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
        local lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
        local SPEED = 0
    
        local function FLY()
            FLYING = true
            local BG = Instance.new('BodyGyro')
            local BV = Instance.new('BodyVelocity')
            BG.P = 9e3
            BG.Parent = T
            BV.Parent = T
            BG.maxTorque = Vector3.new(9e4, 9e4, 9e4)
            BG.cframe = T.CFrame
            BV.velocity = Vector3.new(0, 0, 0)
            BV.maxForce = Vector3.new(9e4, 9e4, 9e4)
            task.spawn(function()
                repeat wait()
                    if not vfly and Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
                        Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = true
                    end
                    if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0 then
                        SPEED = 50
                    elseif not (CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0) and SPEED ~= 0 then
                        SPEED = 0
                    end
                    if (CONTROL.L + CONTROL.R) ~= 0 or (CONTROL.F + CONTROL.B) ~= 0 or (CONTROL.Q + CONTROL.E) ~= 0 then
                        BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (CONTROL.F + CONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
                        lCONTROL = {F = CONTROL.F, B = CONTROL.B, L = CONTROL.L, R = CONTROL.R}
                    elseif (CONTROL.L + CONTROL.R) == 0 and (CONTROL.F + CONTROL.B) == 0 and (CONTROL.Q + CONTROL.E) == 0 and SPEED ~= 0 then
                        BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (lCONTROL.F + lCONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(lCONTROL.L + lCONTROL.R, (lCONTROL.F + lCONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
                    else
                        BV.velocity = Vector3.new(0, 0, 0)
                    end
                    BG.cframe = workspace.CurrentCamera.CoordinateFrame
                until not FLYING
                CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
                lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
                SPEED = 0
                BG:Destroy()
                BV:Destroy()
                if Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
                    Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = false
                end
            end)
        end
        flyKeyDown = IYMouse.KeyDown:Connect(function(KEY)
            if KEY:lower() == 'w' then
                CONTROL.F = (vfly and vehicleflyspeed or iyflyspeed)
            elseif KEY:lower() == 's' then
                CONTROL.B = - (vfly and vehicleflyspeed or iyflyspeed)
            elseif KEY:lower() == 'a' then
                CONTROL.L = - (vfly and vehicleflyspeed or iyflyspeed)
            elseif KEY:lower() == 'd' then 
                CONTROL.R = (vfly and vehicleflyspeed or iyflyspeed)
            elseif QEfly and KEY:lower() == 'e' then
                CONTROL.Q = (vfly and vehicleflyspeed or iyflyspeed)*2
            elseif QEfly and KEY:lower() == 'q' then
                CONTROL.E = -(vfly and vehicleflyspeed or iyflyspeed)*2
            end
            pcall(function() workspace.CurrentCamera.CameraType = Enum.CameraType.Track end)
        end)
        flyKeyUp = IYMouse.KeyUp:Connect(function(KEY)
            if KEY:lower() == 'w' then
                CONTROL.F = 0
            elseif KEY:lower() == 's' then
                CONTROL.B = 0
            elseif KEY:lower() == 'a' then
                CONTROL.L = 0
            elseif KEY:lower() == 'd' then
                CONTROL.R = 0
            elseif KEY:lower() == 'e' then
                CONTROL.Q = 0
            elseif KEY:lower() == 'q' then
                CONTROL.E = 0
            end
        end)
        FLY()
     end
    
     function NOFLY()
        FLYING = false
        if flyKeyDown or flyKeyUp then flyKeyDown:Disconnect() flyKeyUp:Disconnect() end
        if Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
            Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = false
        end
        pcall(function() workspace.CurrentCamera.CameraType = Enum.CameraType.Custom end)
 end


--[[AutoFarm Tab]]--
AutoW:Toggle('AutoFarm Orbs',function(state)
    Config.AutoFarm.AutoOrbFarm = state
end)

AutoW:Toggle('AutoFarm Xp',function(state)
    Config.AutoFarm.AutoXpFarm = state
end)

AutoW:Toggle('Auto Hoops',function(state)
    Config.AutoFarm.AutoHoopFarm = state
end)

AutoW:Toggle('AutoFarm Gem',function(state)
    Config.AutoFarm.AutoGemFarm = state
end)

AutoW:Toggle('Auto Rebirth',function(state)
    Config.AutoFarm.AutoRebirth = state
end)

--[[AutoBuy Tab]]--

AutoBuyW:Dropdown('Select Crystal',Crystal,function(Selected)
    Config.AutoBuy.SelectedCrystal = Selected
end)

AutoBuyW:Toggle('Auto Buy Crystal',function(state)
    Config.AutoBuy.AutoBuyCrystal = state
end)

--[[LocalPlayer Tab]]--


PlayerW:Slider('Gravity',0,196.2,function(num)
    game.Workspace.Gravity = num
end)

PlayerW:Toggle('Inf Jump ',function(state)
    Config.Player.InfJump = state
end)

PlayerW:Slider('WalkSpeed Config',16,100000000,function(num)
    game:GetService('Players').LocalPlayer.Character.Humanoid.WalkSpeed = num
end)

PlayerW:Slider('JumpPower Config',50,10000,function(num)
    game:GetService('Players').LocalPlayer.Character.Humanoid.JumpPower = num
end)

PlayerW:Toggle('Fly',function(state)
    if state then 
        sFLY()
    else
        NOFLY()
    end
end)

PlayerW:Slider('Fly Config',1,15,function(Value)
    iyflyspeed = Value
end)

--[[Misc Tab]]--

MiscW:Button('Collect All cheats',function()
	for i,v in pairs(workspace.rewardChests:GetChildren()) do
        for i = 1,10 do
            local v1 = v
            game:GetService("ReplicatedStorage").rEvents.collectCourseChestRemote:InvokeServer(v1)
        end
    end
end)



