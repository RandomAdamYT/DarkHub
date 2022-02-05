local settings = {
    silent = false,
    boxesp = false,
    EnemyColor = Color3.fromRGB(196, 40, 28),
    TeamColor = Color3.fromRGB(75, 151, 75),
    DrawFOV = false,
    Acc = 100,
    FOV = 100
}

local Services = setmetatable({
LocalPlayer = game:GetService("Players").LocalPlayer,
Camera = workspace.CurrentCamera,
}, {
__index = function(self, idx)
return rawget(self, idx) or game:GetService(idx)
end
})

local Funcs = {}



function Funcs:IsAlive(player)
if player and player.Character and player.Character:FindFirstChild("Head") and workspace:FindFirstChild(player.Character.Name) and player ~= Services.LocalPlayer then
return true
end
end

function Funcs:DrawSquare()
local Box = Drawing.new("Square")
Box.Color = Color3.fromRGB(190, 190, 0)
Box.Thickness = 0.5
Box.Filled = false
Box.Transparency = 1
return Box
end

function Funcs:DrawQuad() -- Unused
local quad = Drawing.new("Quad")
quad.Color = Color3.fromRGB(190, 190, 0)
quad.Thickness = 0.5
quad.Filled = false
quad.Transparency = 1
return quad
end

function Funcs:DrawLine()
local line = Drawing.new("Line")
line.Color = Color3.new(190, 190, 0)
line.Thickness = 0.5
return line
end

function Funcs:DrawText()
local text = Drawing.new("Text")
text.Color = Color3.fromRGB(190, 190, 0)
text.Size = 20
text.Outline = true
text.Center = true
return text
end

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
Mainz = main:Tab('Combat')
Esp = main:Tab('Visuals')
GM = main:Tab('Gun Mods')

Mainz:Toggle("Silent-Aim", function(state)
settings.silent = state
end)
Mainz:Toggle("Draw FOV", function(state)
settings.DrawFOV = state
end)
Mainz:Slider('FOV', 0, 2500, function(num)
settings.FOV = num
end)
Mainz:Slider('Silent-Aim Accuracy', 0, 100, function(num)
settings.Acc = num
end)
local FOVCircle = Drawing.new("Circle")
FOVCircle.Color = Color3.fromRGB(190, 190, 0)
FOVCircle.Thickness = 0.5
FOVCircle.NumSides = 16
FOVCircle.Filled = false
FOVCircle.Transparency = 1

 -- // Mangled to fix :eyerolling:
local Players = game:GetService("Players")
local Mouse = game.Players.LocalPlayer:GetMouse()
function GetTarget()
    local Plr = nil
    local SD = math.huge
    for i,v in pairs(Players.GetPlayers(Players)) do
        if v ~= game.Players.LocalPlayer  and v.Character and v.Character.HumanoidRootPart.Nametag.Arrow.ImageColor3 ~= Color3.fromRGB(34, 255, 143) then -- DekuDimz for simple teamcheck 
                local Pos, Vis = workspace.CurrentCamera.WorldToScreenPoint(workspace.CurrentCamera, v.Character.HumanoidRootPart.Position)
                if Vis then
                    local mag = (Vector2.new(Pos.X, Pos.Y) - Vector2.new(Mouse.X, Mouse.Y)).magnitude
                    if mag < SD and mag <= settings.FOV then
                        Plr = v
                        SD = mag
                    end
                end
            end
    end
    return Plr
end
local OldNameCall
OldNameCall = hookmetamethod(game, "__namecall", function(self,...)
    local Args = {...}
    if getnamecallmethod() == "FindPartOnRayWithIgnoreList" and not checkcaller() and settings.silent and settings.Acc >= math.random(1,100) then
        local IRaysBed = GetTarget()
        if IRaysBed then
            Args[1] = Ray.new(workspace.CurrentCamera.CFrame.Position, (IRaysBed.Character.HumanoidRootPart.Position - workspace.CurrentCamera.CFrame.Position).Unit * 1000)
            return OldNameCall(self, unpack(Args))
        end
    end
    return OldNameCall(self, ...)
end)

Esp:Toggle("BoxEsp", function(state)
settings.boxesp = state
end)

Esp:Colorpicker("Enemy Color", Color3.fromRGB(225,0,0), function(Color)
settings.EnemyColor = Color
end)

Esp:Colorpicker("Team Color", Color3.fromRGB(0,225,0), function(Color)
settings.TeamColor = Color
end)

function Funcs:AddEsp(player)
local Box = Funcs:DrawSquare()
local Tracer = Funcs:DrawLine()
local Name = Funcs:DrawText()
local Distance = Funcs:DrawText()
local SnapLines = Funcs:DrawLine()
local HeadLowerTorso = Funcs:DrawLine()
local NeckLeftUpper = Funcs:DrawLine()
local LeftUpperLeftLower = Funcs:DrawLine()
local NeckRightUpper = Funcs:DrawLine()
local RightUpperLeftLower = Funcs:DrawLine()
local LowerTorsoLeftUpper = Funcs:DrawLine()
local LeftLowerLeftUpper = Funcs:DrawLine()
local LowerTorsoRightUpper = Funcs:DrawLine()
local RightLowerRightUpper = Funcs:DrawLine()
local bottomrightone = Funcs:DrawLine()
local bottomleftone = Funcs:DrawLine()
local toprightone = Funcs:DrawLine()
local topleftone = Funcs:DrawLine()
local toplefttwo = Funcs:DrawLine()
local bottomlefttwo = Funcs:DrawLine()
local toprighttwo = Funcs:DrawLine()
local bottomrighttwo = Funcs:DrawLine()
Services.RunService.Stepped:Connect(function()
FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation();
FOVCircle.Radius = settings.FOV
if settings.DrawFOV then
FOVCircle.Visible = true
else
FOVCircle.Visible = false
end
    if player.Character.HumanoidRootPart.Nametag.Arrow.ImageColor3 == Color3.fromRGB(34, 255, 143) then
  Box.Color = settings.TeamColor
  Tracer.Color = settings.TeamColor
  HeadLowerTorso.Color = settings.TeamColor
  NeckLeftUpper.Color = settings.TeamColor
  LeftUpperLeftLower.Color = settings.TeamColor
  NeckRightUpper.Color = settings.TeamColor
  RightUpperLeftLower.Color = settings.TeamColor
  LowerTorsoLeftUpper.Color = settings.TeamColor
  LeftLowerLeftUpper.Color = settings.TeamColor
  LowerTorsoRightUpper.Color = settings.TeamColor
  RightLowerRightUpper.Color = settings.TeamColor
  bottomrightone.Color = settings.TeamColor
  bottomleftone.Color = settings.TeamColor
  toprightone.Color = settings.TeamColor
  topleftone.Color = settings.TeamColor
  toplefttwo.Color = settings.TeamColor
  bottomlefttwo.Color = settings.TeamColor
  toprighttwo.Color = settings.TeamColor
  bottomrighttwo.Color = settings.TeamColor
else
  Box.Color = settings.EnemyColor
  Tracer.Color = settings.EnemyColor
  HeadLowerTorso.Color = settings.EnemyColor
  NeckLeftUpper.Color = settings.EnemyColor
  LeftUpperLeftLower.Color = settings.EnemyColor
  NeckRightUpper.Color = settings.EnemyColor
  RightUpperLeftLower.Color = settings.EnemyColor
  LowerTorsoLeftUpper.Color = settings.EnemyColor
  LeftLowerLeftUpper.Color = settings.EnemyColor
  LowerTorsoRightUpper.Color = settings.EnemyColor
  RightLowerRightUpper.Color = settings.EnemyColor
  bottomrightone.Color = settings.EnemyColor
  bottomleftone.Color = settings.EnemyColor
  toprightone.Color = settings.EnemyColor
  topleftone.Color = settings.EnemyColor
  toplefttwo.Color = settings.EnemyColor
  bottomlefttwo.Color = settings.EnemyColor
  toprighttwo.Color = settings.EnemyColor
  bottomrighttwo.Color = settings.EnemyColor
end
if Funcs:IsAlive(player) and player.Character:FindFirstChild("HumanoidRootPart") then
  local RootPosition, OnScreen = Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position)
  local HeadPosition = Services.Camera:WorldToViewportPoint(player.Character.Head.Position + Vector3.new(0, 0, 0)) -- can creat an offset if u want
  local LegPosition = Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position - Vector3.new(0, 5, 0))
  local length = RootPosition.Y - ((HeadPosition.Y - LegPosition.Y) / 2)
  local lengthx = RootPosition.X - ((HeadPosition.Y - LegPosition.Y) / 2)
  local size = HeadPosition.Y - LegPosition.Y
  if settings.boxesp then
    Box.Visible = OnScreen
    Box.Size = Vector2.new(HeadPosition.Y - LegPosition.Y, HeadPosition.Y - LegPosition.Y)
    Box.Position = Vector2.new(RootPosition.X - ((HeadPosition.Y - LegPosition.Y) / 2), RootPosition.Y - ((HeadPosition.Y - LegPosition.Y) / 2))
  else
    Box.Visible = false
  end
else
  Box.Visible = false
end
end)
end

for i, v in pairs(game.Players:GetPlayers()) do
if v ~= Services.LocalPlayer then
Funcs:AddEsp(v)
end
end

game.Players.PlayerAdded:Connect(function(player)
if v ~= game.Players.LocalPlayer then
Funcs:AddEsp(player)
end
end)

GM:Button("No Spread", function()
for _,v in ipairs(game:GetService("ReplicatedStorage").Weapons.Guns:GetChildren()) do
    for _,v2 in pairs(v:GetChildren()) do
        if v2.ClassName == "Folder" then
            v2:SetAttribute("bloomFactor", 0)
        end
    end
end
end)


GM:Button("Fast Fire", function()
for _,v in ipairs(game:GetService("ReplicatedStorage").Weapons.Guns:GetChildren()) do
    for _,v2 in pairs(v:GetChildren()) do
        if v2.ClassName == "Folder" then
            v2:SetAttribute("Automatic", true)
            v2:SetAttribute("ProjectileVelocity", 5000)
            v:SetAttribute("Firerate", 50000)

        end
    end
end

end)


