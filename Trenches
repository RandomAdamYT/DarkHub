--[[

$$$$$$$\                      $$\       $$\   $$\           $$\       
$$  __$$\                     $$ |      $$ |  $$ |          $$ |      
$$ |  $$ | $$$$$$\   $$$$$$\  $$ |  $$\ $$ |  $$ |$$\   $$\ $$$$$$$\  
$$ |  $$ | \____$$\ $$  __$$\ $$ | $$  |$$$$$$$$ |$$ |  $$ |$$  __$$\ 
$$ |  $$ | $$$$$$$ |$$ |  \__|$$$$$$  / $$  __$$ |$$ |  $$ |$$ |  $$ |
$$ |  $$ |$$  __$$ |$$ |      $$  _$$<  $$ |  $$ |$$ |  $$ |$$ |  $$ |
$$$$$$$  |\$$$$$$$ |$$ |      $$ | \$$\ $$ |  $$ |\$$$$$$  |$$$$$$$  |
\_______/  \_______|\__|      \__|  \__|\__|  \__| \______/ \_______/ 
                                                           
                                                                      
~Updated 12/18/2021

    ~ Merry Christmas from the DarkHub Development Team!
]]

DarkHub_Client = {SavedClient = false}
if isfolder and makefolder and not isfolder('DarkHub') then
    makefolder('DarkHub')
    DarkHub_Client.SaveClient = true
    if isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
        DarkHub_Client.SavedClient = true
        DarkHub_Client.GameClient = game:GetService('HttpService'):JSONDecode(readfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB'))
    end
elseif isfolder('DarkHub') then
    DarkHub_Client.SaveClient = true
    if isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
        DarkHub_Client.SavedClient = true
        DarkHub_Client.GameClient = game:GetService('HttpService'):JSONDecode(readfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB'))
    end
else
    DarkHub_Client.SaveClient = false
end


local OldNameCall 
OldNameCall = hookmetamethod(game, "__namecall", function(...) --namecall shit blah blah
    
    if getnamecallmethod() == "Kick" then --calling for a kick
        return--returning the kick nil 
    end

    return OldNameCall(...)
end)

	

local Services = setmetatable({
LocalPlayer = game:GetService("Players").LocalPlayer,
Camera = workspace.CurrentCamera,
}, {
__index = function(self, idx)
return rawget(self, idx) or game:GetService(idx)
end
})

local Funcs = {}

function Funcs:Round(number)
return math.floor(tonumber(number) + 0.5)
end


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


--Client Values that will save basicly
IsUpToDate = pcall(function()
    Client = {
       Toggles = {
            SilentAim = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.Silent or false,
            FOV = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.FOV or 100,
        DrawFOV = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.DrawFOV or false,
        Distance = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.Distance or math.huge,
        Accuracy = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.Accuracy or 100,
        Construct = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.Construct or false,
        CAuraSize = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.CAuraSize or 10,
        BoxEsp = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.BoxEsp or false,
        EnemyColor = Color3.fromRGB(196, 40, 28),
        TeamColor = Color3.fromRGB(75, 151, 75),
        WalkSpeed = 16,
        JumpPower = 50,
        Build = DarkHub_Client.SavedClient and DarkHub_Client.GameClient.Toggles.Build or false,
    }
}
 
end)

if not IsUpToDate and DarkHub_Client.SavedClient and isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
    delfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB')
    game.Players.LocalPlayer:Kick('DarkHub Client Out Of Date - Issue Fixed | Restart DarkHub to Continue')
end

 
local Services = setmetatable({
LocalPlayer = game:GetService("Players").LocalPlayer,
Camera = workspace.CurrentCamera,
}, {
__index = function(self, idx)
return rawget(self, idx) or game:GetService(idx)
end
})

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB",true))()
main = lib:Window()
Aimbot = main:Tab('Combat')
LPTab = main:Tab('Character')
Esp = main:Tab('Visuals')
Extra = main:Tab('Extra')

LPTab:Slider('WalkSpeed', 16, 100, function(num)
Client.Toggles.WalkSpeed = num
end)
LPTab:Slider('JumpPower', 50, 100, function(num)
Client.Toggles.JumpPower = num
end)

Esp:Toggle('BoxEsp',function(state)
Client.Toggles.BoxEsp = state
end,Client.Toggles.BoxEsp)

Esp:Colorpicker("Enemy Color", Color3.fromRGB(225,0,0), function(Color)
Client.Toggles.EnemyColor = Color
end)

Esp:Colorpicker("Team Color", Color3.fromRGB(0,225,0), function(Color)
Client.Toggles.TeamColor = Color
end)

  
Extra:Toggle('Instant Build',function(state)
Client.Toggles.Build = state
end,Client.Toggles.Build)

Extra:Toggle('Construct Aura',function(state)
Client.Toggles.Construct = state
end,Client.Toggles.Construct)

Extra:Slider('Construct Aura Size', 0, 20, function(num)
Client.Toggles.CAuraSize = num
end,Client.Toggles.CAuraSize)


Aimbot:Toggle('Silent',function(state)
Client.Toggles.Silent = state
end,Client.Toggles.Silent)


Aimbot:Slider('Silent-Aim Accuracy', 0, 100, function(num)
Client.Toggles.Distance = num
end,Client.Toggles.Distance)

Aimbot:Slider('Max Target Distance', 0,100000, function(num)
Client.Toggles.Distance = num
end,Client.Toggles.Distance)

Aimbot:Slider('FOV', 0,2500, function(num)
Client.Toggles.FOV = num
end,Client.Toggles.FOV)

Aimbot:Toggle('Draw FOV',function(state)
Client.Toggles.DrawFOV = state
end,Client.Toggles.DrawFOV)


local FOVCircle = Drawing.new("Circle")
FOVCircle.Color = Color3.fromRGB(190, 190, 0)
FOVCircle.Thickness = 0.5
FOVCircle.NumSides = 16
FOVCircle.Filled = false
FOVCircle.Transparency = 1
local Pos = nil
local Item = nil
local db = true
   game:GetService("RunService").RenderStepped:Connect(function()
for _,v in ipairs(workspace.Camera:GetChildren()) do -- This will get the test Model
    for _,v2 in ipairs(game:GetService("ReplicatedStorage").Structures:GetChildren()) do-- This will sort from the Structures it can pick
        if v.ClassName == "Model" and v.Name == v2.Name then -- We can follow down a path to X out the incorrect ones
            Item = v.Name -- This sets it to the Correct path
            Pos = v.Root.Position -- This is Holograms Position
        end
    end
end
if game.Players.LocalPlayer.Character:FindFirstChild("Build") then -- Test for the stinky tool
    if game.Players.LocalPlayer.Character.Build.BuildMain.Variables.MouseDown.Value == true then -- make sure you clicked
        if db then -- quick cooldown
            db= false -- Stops you from spamming
game.Players.LocalPlayer.Character.Build.Build:FireServer(CFrame.new(Pos), game:GetService("ReplicatedStorage").Structures[Item])  --Places
wait(.50) -- Waits half a second
db = true -- lets you build again
        end
    end
end

if game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
game.Players.LocalPlayer.Character.Humanoid.JumpPower = Client.Toggles.JumpPower
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Client.Toggles.WalkSpeed
game.Players.LocalPlayer.Character.Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Client.Toggles.WalkSpeed
    end)
end
if Client.Toggles.Construct then
    for _,v in pairs(game:GetService("Workspace").Structures:GetChildren()) do
    if v:IsA("Model") then
        if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v:FindFirstChild("Root").Position).Magnitude < Client.Toggles.CAuraSize then
if game.Players.LocalPlayer.Character:FindFirstChild("Build") then
game.Players.LocalPlayer.Character.Build.Work:FireServer(v)
end
end
end
end
end
FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation();
FOVCircle.Radius = Client.Toggles.FOV
if Client.Toggles.DrawFOV then
FOVCircle.Visible = true
else
FOVCircle.Visible = false
end
end)

Aimbot:Colorpicker("FOV Color", Color3.new(225,225,225), function(Color)
FOVCircle.Color = Color
end)


local Mouse = game:GetService('Players').LocalPlayer:GetMouse()
function GetTarget()
   local Plr = nil
   local SD = math.huge
       for i, v in pairs(game:GetService('Players'):GetPlayers()) do
           if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild('Head') and v.Character:FindFirstChild('Humanoid') then
               if v.Team ~= game:GetService('Players').LocalPlayer.Team then
                   local pos = game:GetService('Workspace').CurrentCamera:WorldToViewportPoint(v.Character:FindFirstChild('HumanoidRootPart').Position)
                   local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(Mouse.X, Mouse.Y)).magnitude
                   if magnitude < SD and magnitude <= Client.Toggles.FOV then
                       Plr = v
                       SD = magnitude
                   end
               end
           end
       end  
   return Plr
end

local OldNamecall
OldNamecall = hookmetamethod(game, "__namecall", function(self, ...)
       local args = {...}
       local method = getnamecallmethod()

       if tostring(self) == "ShootEvent" and method == "FireServer" and Client.Toggles.Silent and Client.Toggles.Accuracy >= math.random(1,100) then
           args[5] = GetTarget().Character.Head
           args[6] = GetTarget().Character.Head.Position

           return self.FireServer(self, unpack(args))
end
return OldNamecall(self, ...)
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
    if player.Team == Services.LocalPlayer.Team then
  Box.Color = Client.Toggles.TeamColor
  Tracer.Color = Client.Toggles.TeamColor
  HeadLowerTorso.Color = Client.Toggles.TeamColor
  NeckLeftUpper.Color = Client.Toggles.TeamColor
  LeftUpperLeftLower.Color = Client.Toggles.TeamColor
  NeckRightUpper.Color = Client.Toggles.TeamColor
  RightUpperLeftLower.Color = Client.Toggles.TeamColor
  LowerTorsoLeftUpper.Color = Client.Toggles.TeamColor
  LeftLowerLeftUpper.Color = Client.Toggles.TeamColor
  LowerTorsoRightUpper.Color = Client.Toggles.TeamColor
  RightLowerRightUpper.Color = Client.Toggles.TeamColor
  bottomrightone.Color = Client.Toggles.TeamColor
  bottomleftone.Color = Client.Toggles.TeamColor
  toprightone.Color = Client.Toggles.TeamColor
  topleftone.Color = Client.Toggles.TeamColor
  toplefttwo.Color = Client.Toggles.TeamColor
  bottomlefttwo.Color = Client.Toggles.TeamColor
  toprighttwo.Color = Client.Toggles.TeamColor
  bottomrighttwo.Color = Client.Toggles.TeamColor
else
  Box.Color = Client.Toggles.EnemyColor
  Tracer.Color = Client.Toggles.EnemyColor
  HeadLowerTorso.Color = Client.Toggles.EnemyColor
  NeckLeftUpper.Color = Client.Toggles.EnemyColor
  LeftUpperLeftLower.Color = Client.Toggles.EnemyColor
  NeckRightUpper.Color = Client.Toggles.EnemyColor
  RightUpperLeftLower.Color = Client.Toggles.EnemyColor
  LowerTorsoLeftUpper.Color = Client.Toggles.EnemyColor
  LeftLowerLeftUpper.Color = Client.Toggles.EnemyColor
  LowerTorsoRightUpper.Color = Client.Toggles.EnemyColor
  RightLowerRightUpper.Color = Client.Toggles.EnemyColor
  bottomrightone.Color = Client.Toggles.EnemyColor
  bottomleftone.Color = Client.Toggles.EnemyColor
  toprightone.Color = Client.Toggles.EnemyColor
  topleftone.Color = Client.Toggles.EnemyColor
  toplefttwo.Color = Client.Toggles.EnemyColor
  bottomlefttwo.Color = Client.Toggles.EnemyColor
  toprighttwo.Color = Client.Toggles.EnemyColor
  bottomrighttwo.Color = Client.Toggles.EnemyColor
end
if Funcs:IsAlive(player) and player.Character:FindFirstChild("HumanoidRootPart") then
  local RootPosition, OnScreen = Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position)
  local HeadPosition = Services.Camera:WorldToViewportPoint(player.Character.Head.Position + Vector3.new(0, 0, 0)) -- can creat an offset if u want
  local LegPosition = Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position - Vector3.new(0, 5, 0))
  local length = RootPosition.Y - ((HeadPosition.Y - LegPosition.Y) / 2)
  local lengthx = RootPosition.X - ((HeadPosition.Y - LegPosition.Y) / 2)
  local size = HeadPosition.Y - LegPosition.Y
  if Client.Toggles.BoxEsp then
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

--Goes under all framework
spawn(function()
    while true do wait(5)
        if DarkHub_Client.SaveClient then
            writefile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB',game:GetService('HttpService'):JSONEncode({['Toggles'] = Client.Toggles}))    
        end
    end
end)
