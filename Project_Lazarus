local Settings = {
    Aimbot = false,
    Silent = false,
    Vis = false,
    HeadShot = false,
    FovUsed = false,
    Fov = 100,
    Boxes = false,
    Walkspeed = 1,
    Instakill = false,
    InstaReload = false,
    Recoil = false,
    Wallbang = false,
    Firerate = false,
    InfAmmo = false,
    Spread = false
}
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local Camera = game:GetService("Workspace").CurrentCamera
local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local Mouse = Player:GetMouse()
local Zombies = game:GetService("Workspace").Baddies
local Map = game:GetService("Workspace").Map
local Interact = game:GetService("Workspace").Interact
local Ignore = game:GetService("Workspace").Ignore
local SendData = game:GetService("ReplicatedStorage").ClientRemotes.SendData
local Metatable = getrawmetatable(game)
local Index = Metatable.__index
local Namecall = Metatable.__namecall
local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
local Window = Lib:Window()
local Main = Window:Tab('Main')
local Gun = Window:Tab('Gun')
local TargetPos = false
local Circle = Drawing.new("Circle")
Circle.Color = Color3.new(1, 1, 1)
Circle.Thickness = 1
Circle.Radius = Settings.Fov
Circle.Visible = Settings.FovUsed
Circle.NumSides = 1000
Circle.Filled = false
Circle.Transparency = 1

Main:Toggle('Aimbot', function(Bool)
    Settings.Aimbot = Bool
end)

Main:Toggle('Silent Aim', function(Bool)
    Settings.Silent = Bool
end)

Main:Toggle('Visable Check', function(Bool)
    Settings.Vis = Bool
end)

Main:Toggle('Head Shots', function(Bool)
    Settings.HeadShot = Bool
end)

Main:Toggle('Use Fov', function(Bool)
    Settings.FovUsed = Bool
    Circle.Visible = Bool
end)

Main:Slider('Fov', 1, 1000, function(Number)
    Settings.Fov = Number
    Circle.Radius = Number
end)

Main:Toggle('Box Esp', function(Bool)
    Settings.Boxes = Bool
end)

Main:Slider('Walkspeed', 1, 20, function(Number)
    Settings.Walkspeed = Number
    for i, v in pairs(Player.Backpack:GetChildren()) do
        if v.Name == "Weapon1" or v.Name == "Weapon2" or v.Name == "Weapon3" then
            local Data = require(v)
            Data.MoveSpeed = Number
            Data.AimMoveSpeed = Number
        end
    end
end)

Main:Label("cum")

Gun:Toggle('Wallbang', function(Bool)
    Settings.Wallbang = Bool
    for i, v in pairs(Player.Backpack:GetChildren()) do
        if v.Name == "Weapon1" or v.Name == "Weapon2" or v.Name == "Weapon3" then
            local Data = require(v)
            Data.BulletPenetration = 420
        end
    end
end)

Gun:Toggle('No Recoil', function(Bool)
    Settings.Recoil = Bool
    for i, v in pairs(Player.Backpack:GetChildren()) do
        if v.Name == "Weapon1" or v.Name == "Weapon2" or v.Name == "Weapon3" then
            local Data = require(v)
            Data.GunKick = 0
            Data.ViewKick.Pitch.Min = 0
            Data.ViewKick.Pitch.Max = 0
            Data.ViewKick.Yaw.Min = 0
            Data.ViewKick.Yaw.Max = 0
        end
    end
end)

Gun:Toggle('No Spread', function(Bool)
    Settings.Spread = Bool
    for i, v in pairs(Player.Backpack:GetChildren()) do
        if v.Name == "Weapon1" or v.Name == "Weapon2" or v.Name == "Weapon3" then
            local Data = require(v)
            Data.Spread.Min = 0
            Data.Spread.Max = 0
        end
    end
end)

Gun:Toggle('Insta Kill', function(Bool)
    Settings.Instakill = Bool
end)

Gun:Toggle('Insta Reload', function(Bool)
    Settings.InstaReload = Bool
    for i, v in pairs(Player.Backpack:GetChildren()) do
        if v.Name == "Weapon1" or v.Name == "Weapon2" or v.Name == "Weapon3" then
            local Data = require(v)
            for o, b in pairs(Data.ReloadSequence) do
                getfenv(b).wait = function(time)
                    if Settings.InstaReload then
                        return
                    else
                        return wait(time)
                    end
                end
            end
        end
    end
end)

Gun:Toggle('Inf Ammo', function(Bool)
    Settings.InfAmmo = Bool
    for i, v in pairs(Player.Backpack:GetChildren()) do
        if v.Name == "Weapon1" or v.Name == "Weapon2" or v.Name == "Weapon3" then
            local Data = require(v)
        	Data.MagSize = math.huge
        	Data.StoredAmmo = math.huge
        	Data.MaxAmmo = math.huge
        end
    end
end)

Gun:Toggle('Firerate', function(Bool)
    Settings.Firerate = Bool
    for i, v in pairs(Player.Backpack:GetChildren()) do
        if v.Name == "Weapon1" or v.Name == "Weapon2" or v.Name == "Weapon3" then
            local Data = require(v)
            Data.Semi = false
            Data.FireTime = 0
        end
    end
end)

function DrawSquare()
    local Box = Drawing.new("Square")
    Box.Color = Color3.fromRGB(190, 190, 0)
    Box.Thickness = 0.5
    Box.Filled = false
    Box.Transparency = 1
    return Box
end

function GetOffset(part, pos)
    local FarPosition = Camera:WorldToViewportPoint(Vector3.new(part.Position.X, part.Position.Y + (part.Size.Y / 2), part.Position.Z))
    return FarPosition.Y - pos.Y
end

function GetCorners(Char)
    local TopY = math.huge
    local BottomY = -math.huge
    local RightX = -math.huge
    local LeftX = math.huge
    local Offsets
    local Positions = {}
    for i, v in next, Char:GetChildren() do
        if v.ClassName == "Part" and v.Name ~= "HumanoidRootPart" then
            local Position, OnScreen = Camera:WorldToViewportPoint(v.Position)
            Positions[v.Name] = Position
            Offsets = GetOffset(v, Position)
            if OnScreen then
                if Position.Y < TopY then
                    TopY = Position.Y
                end
                if Position.Y > BottomY then
                    BottomY = Position.Y
                end
                if Position.X < LeftX then
                    LeftX = Position.X
                end
                if Position.X > RightX then
                    RightX = Position.X
                end
            end
        end
    end
    return {TopLeft = Vector2.new(LeftX + Offsets, TopY + Offsets), TopRight = Vector2.new(RightX - Offsets, TopY + Offsets), BottomLeft = Vector2.new(LeftX + Offsets, BottomY - Offsets), BottomRight = Vector2.new(RightX - Offsets, BottomY - Offsets), Positions = Positions}
end

function VisCheck(Pos)
  	local Parts = Camera:GetPartsObscuringTarget({Player.Character.Head.Position, Pos}, {Ignore, Zombies})
  	if #Parts == 0 then
    	return true
  	end
end

function GetClosest()
    local Closest = nil
    local Pos = nil
    local Magnitude = math.huge
    for i, v in next, Zombies:GetChildren() do 
        if Player.Character and Player.Character:FindFirstChild("Head") and v:FindFirstChild("Head") and v:FindFirstChild("Torso") then
            if Settings.Vis and VisCheck(v.Head.Position) or not Settings.Vis then
	            local Position, Visible = Camera:WorldToViewportPoint(v.Head.Position) 
	            if Visible then
	                local Mouse = Player:GetMouse()
	                local Distance = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(Position.X, Position.Y)).Magnitude 
	                if not Settings.FovUsed and Distance < Magnitude or Settings.FovUsed and Distance < Magnitude and Distance < Settings.Fov then 
	                    Closest = v 
	                    Magnitude = Distance
	                    Pos = Position
	                end
	            end
        	end
        end
    end
    return Closest, Pos
end

setreadonly(Metatable, false)

Metatable.__index = newcclosure(function(self, Property)
    if Settings.Silent and TargetPos then
        if self == Mouse and Property == "Hit" or tostring(self) == "AimPart" and Property == "CFrame" then
            return CFrame.new(TargetPos)
        end
    end
    return Index(self, Property)
end)

Metatable.__namecall = function(self, ...)
    local Meth = getnamecallmethod()
    local Args = {...}
    if Settings.Instakill and Meth == "FireServer" and tostring(self) == "Damage" then
	    Args[1].Damage = 9999
        return Namecall(self, unpack(Args))
    end
    if Settings.Wallbang and Meth == "FindPartOnRayWithIgnoreList" then
        table.insert(Args[2], Map)
        table.insert(Args[2], Interact)
        return Namecall(self, unpack(Args))
    end
    if Meth == "FireServer" and self == SendData then -- anti cheat bypass btw
    	return
    end
    return Namecall(self, ...)
end

setreadonly(Metatable, true)

Player.Backpack.ChildAdded:Connect(function(Module)
    if Module.Name == "Weapon1" or Module.Name == "Weapon2" or Module.Name == "Weapon3" then
        local Data = require(Module)
        if Settings.Walkspeed ~= 1 then
            Data.MoveSpeed = Settings.Walkspeed
            Data.AimMoveSpeed = Settings.Walkspeed
        end
        if Settings.InstaReload then
            for o, b in pairs(Data.ReloadSequence) do
                getfenv(b).wait = function(time)
                    if Settings.InstaReload then
                        return
                    else
                        return wait(time)
                    end
                end
            end
        end
        if Settings.Wallbang then
            Data.BulletPenetration = 420
        end
        if Settings.Firerate then
            Data.Semi = false
            Data.FireTime = 0
        end
        if Settings.Recoil then
            Data.GunKick = 0
            Data.ViewKick.Pitch.Min = 0
            Data.ViewKick.Pitch.Max = 0
            Data.ViewKick.Yaw.Min = 0
            Data.ViewKick.Yaw.Max = 0
        end
        if Settings.Spread then
            Data.Spread.Min = 0
            Data.Spread.Max = 0
        end
        if Settings.InfAmmo then
        	Data.MagSize = math.huge
        	Data.StoredAmmo = math.huge
        	Data.MaxAmmo = math.huge
        end
        if Settings.Firerate then
            Data.Semi = false
            Data.FireTime = 0
        end
    end
end)

function AddEsp(Zombie)
    local Random = tostring(math.random(0, 9999999))
    local Box = DrawSquare()
    RunService:BindToRenderStep(Random, 1, function()
        local Exist = Zombie:IsDescendantOf(Zombies)
        if Exist and Zombie:FindFirstChild("HumanoidRootPart") then
            local Corners = GetCorners(Zombie)
            local Positions = Corners.Positions
            local xDist = Corners.BottomRight.X - Corners.TopLeft.X
            local yDist = Corners.BottomRight.Y - Corners.TopLeft.Y
            local RootPosition, OnScreen = Camera:WorldToViewportPoint(Zombie.HumanoidRootPart.Position)
            if Settings.Boxes then
                Box.Visible = OnScreen
                Box.Size = Vector2.new(xDist, yDist)
                Box.Position = Corners.TopLeft
            end
        else
            Box.Visible = false
            Box:Remove()
            RunService:UnbindFromRenderStep(Random)
        end
    end)
end

for i, v in pairs(Zombies:GetChildren()) do
    AddEsp(v)
end

Zombies.ChildAdded:Connect(function(Zombie)
    AddEsp(Zombie)
end)

RunService.RenderStepped:Connect(function()
    local Mouse = UserInputService:GetMouseLocation()
    Circle.Position = Vector2.new(Mouse.X, Mouse.Y)
end)

while wait() do
    local Target, Pos = GetClosest()
    local TargetP = Target and Settings.HeadShot and Target.Head.Position or Target and not Settings.HeadShot and Target.Torso.Position or false
    TargetPos = Target and TargetP or false
    if Settings.Aimbot and Target and UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton2) then
        local Mouse = UserInputService:GetMouseLocation()
        mousemoverel((Pos.X - Mouse.X) / 6, (Pos.Y - Mouse.Y) / 6)
    end
end
