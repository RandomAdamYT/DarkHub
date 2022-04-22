
--[[
	we 𐎠re tr𐏑v5 𐏃𐎢𐎲 𐎠nd 𐎭rk 𐏃𐎢𐎲
]] 

--[[Tabs and Uilib]]--
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
local main = lib:Window()
local FarmW = main:Tab("Auto Farm")
local BuyW = main:Tab("Auto Buy")
local TeleW = main:Tab("Teleports")
local PlayerW = main:Tab("LocalPlayer")
local MiscW = main:Tab("Misc")

--[[Config]]--

Config = {
    Farms = {
        StrengthFarm = false,
        EnduranceFarm = false,
        PsychicFarm = false,
        SpeedFarm = false,
        AutoMiniChests = false,
        AutoQuest = false
    },
    Multiplier = {
        MultiBuy = false,
        SelectedMulti = ""
    },
    ChestBuy = {
        ChestBuy = false,
        SelectedChests = ""
    },
    Teleports = {
        SelectedArea = ""
    },
}

local Multi = {
    "StrengthMultiplier",
    "EnduranceMultiplier",
    "PsychicMultiplier",
    "SpeedMultiplier"
}

local Chest = {
    "HolidayChest",
    "BasicChest",
    "VoidChest",
    "ElementalChest",
    "AlienChest",
    "HuntedChest",
    "LightDarkChest",
    "FestiveChest",
    "GalaxyChest",
    "AncientGodChest",
    "DarkPumpkinChest"
}

local Area = {
    "Desert",
    "LostSea",
    "Robot",
    "Ninja",
    "Sky",
}

spawn(function()
    while true do 
        task.wait()
    if Config.Farms.StrengthFarm == true then
            game:GetService("ReplicatedStorage").Events.Train:FireServer("Strength")
        end
    end
end)

spawn(function()
    while true do 
        task.wait()
    if Config.Farms.EnduranceFarm == true then
            task.wait()
            game:GetService("ReplicatedStorage").Events.Train:FireServer("Endurance")
        end
    end
end)

spawn(function()
    while true do 
        task.wait()
    if Config.Farms.PsychicFarm == true then
            task.wait()
            game:GetService("ReplicatedStorage").Events.Train:FireServer("Psychic")
        end
    end
end)

spawn(function()
    while true do 
        task.wait()
    if Config.Farms.AutoQuest == true then
            task.wait(1)
            game:GetService("ReplicatedStorage").Functions.Quest:InvokeServer("GamesReborn")

            game:GetService("ReplicatedStorage").Events.Quest:FireServer("DailyPsychic")

            game:GetService("ReplicatedStorage").Events.Quest:FireServer("DailyStrength")

            game:GetService("ReplicatedStorage").Events.Quest:FireServer("DailyEndurance")

            game:GetService("ReplicatedStorage").Events.Quest:FireServer("WeeklyStrength")

            game:GetService("ReplicatedStorage").Events.Quest:FireServer("WeeklyEndurance")

            game:GetService("ReplicatedStorage").Events.Quest:FireServer("WeeklyPsychic")
        end
    end
end)

spawn(function()
    while true do 
        task.wait()
            if Config.Farms.AutoMiniChests == true then
            task.wait()
                pcall(function()
                    for i, v in pairs(game:GetService("Workspace").MiniChests:GetChildren()) do
                        if v.ClassName == "Part" then
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
                        task.wait(1)
                    fireclickdetector(v.ClickDetector) -- This will just fire it
                end
            end
        end
    )
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

function BasePlate()
    local baseplate = Instance.new("Part")
    baseplate.Parent = workspace
    baseplate.Size = Vector3.new(10000,10,10000) -- change size
    baseplate.Anchored = true
    baseplate.Position = Vector3.new(0, 5000, 14.358478546142578) -- higher number for it to spawn higher
    task.wait(1)
end

spawn(function()
    BasePlate()
    while true do
        task.wait() 
    if Config.Farms.SpeedFarm == true then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 5000, 14.358478546142578)
                    task.wait(0.5)
                    local RunService = game:GetService('RunService')
                    game:GetService('VirtualInputManager'):SendKeyEvent(true,Enum.KeyCode.W,false,game)
                    task.wait(0.5)
        end
    end
end)

--[[Auto Farm Tab]]--


FarmW:Toggle("Strength Farm",function(state)
    Config.Farms.StrengthFarm = state
end)

FarmW:Toggle("Endurance Farm",function(state)
    Config.Farms.EnduranceFarm = state
end)

FarmW:Toggle("Psychic Farm",function(state)
    Config.Farms.PsychicFarm = state
end)

FarmW:Toggle("Speed Farm",function(state)
    Config.Farms.SpeedFarm = state
end)

FarmW:Toggle("Auto Mini Chests",function(state)
    Config.Farms.AutoMiniChests = state
end)

FarmW:Toggle("Auto Quest",function(state)
    Config.Farms.AutoQuest = state
end)

--[[AutoBuy Tab]]--

BuyW:Dropdown("Select Multiplier",Multi,function(Selected)
    Config.Multiplier.SelectedMulti = Selected
end)

BuyW:Toggle("Auto Upgrade Multiplier",function(state)
    Config.Multiplier.MultiBuy = state
    spawn(function()
        while Config.Multiplier.MultiBuy == true do
            task.wait()
            game:GetService("ReplicatedStorage").Functions.Multiplier:InvokeServer(Config.Multiplier.SelectedMulti)
        end
    end)
end)

BuyW:Dropdown("Select Chest",Chest,function(Selected)
    Config.ChestBuy.SelectedChests = Selected
end)

BuyW:Toggle("Auto Chest Buy",function(state)
    Config.ChestBuy.ChestBuy = state
    spawn(function()
        while Config.ChestBuy.ChestBuy == true do
            task.wait()
            game:GetService("ReplicatedStorage").Events.PurchaseItem:FireServer(Config.ChestBuy.SelectedChests)
        end
    end)
end)

--[[Teleport Tab]]--


TeleW:Dropdown("Teleport Area",Area,function(Selected)
    Config.Teleports.SelectedArea = Selected
end)

TeleW:Button("Teleport", function()
if Config.Teleports.SelectedArea == "Desert" then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1643.88623046875, 65.32308959960938, -1895.0677490234375)
elseif Config.Teleports.SelectedArea == "LostSea" then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(996.2438354492188, 60.90877914428711, 679.8507080078125)
elseif Config.Teleports.SelectedArea == "Robot" then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1445.35400390625, 73.44744110107422, 846.1901245117188)
elseif Config.Teleports.SelectedArea == "Ninja" then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1047.5760498046875, 56.825130462646484, -2011.4100341796875)
elseif Config.Teleports.SelectedArea == "Sky" then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-252.15782165527344, 2832.602783203125, -662.334716796875)
end
end)

--[[LocalPlayer Tab]]--


PlayerW:Slider('Gravity',0,196.2,function(num)
    game.Workspace.Gravity = num
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

MiscW:Button("Remove Barriers", function() 
    pcall(function() 
        game:GetService("Workspace")["Map Sand / Barrier"]["Desert Barrier"]:Destroy() 
        game:GetService("Workspace")["Map Sand / Barrier"]["Ninja Barrier"]:Destroy() 
        game:GetService("Workspace")["Map Sand / Barrier"]["LostSea Barrier"]:Destroy() 
        game:GetService("Workspace")["Map Sand / Barrier"]["Prison Barrier"]:Destroy() 
    end)
end)

MiscW:Button("Collect All Chests", function()
for i, v in pairs(game:GetService("Workspace").Chests:GetChildren()) do
    if v.ClassName == "MeshPart" and v.Name == "TouchPart" then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame= v.CFrame
        task.wait(1)
    end
end
end)

