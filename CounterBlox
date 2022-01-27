--[[
  ____    _    ____  _  __   _   _ _   _ ____  
 |  _ \  / \  |  _ \| |/ /  | | | | | | | __ ) 
 | | | |/ _ \ | |_) | ' /   | |_| | | | |  _ \ 
 | |_| / ___ \|  _ <| . \   |  _  | |_| | |_) |
 |____/_/   \_\_| \_\_|\_\  |_| |_|\___/|____/ 
                    ~ Thanks Cute Man DekuDimz
]]

-- Just the config
local Config = {
  Visuals = {
    BoxEsp = false,
    TracerEsp = false,
    TracersOrigin = "Top", -- "Top", "Middle", "Bottom", or "Mouse"
    NameEsp = false,
    DistanceEsp = false,
    SkeletonEsp = false,
    EnemyColor = Color3.fromRGB(190, 190, 0),
    TeamColor = Color3.fromRGB(0, 190, 0),
    Flash = false,
    BulletTracers = false,
    ImpactPoints = false,
    BulletTracersColor = Color3.fromRGB(100, 100, 255),
    ImpactPointsColor = Color3.fromRGB(255, 50, 50),
    THP = 0.5,
    WS = 16,
    WST = false,
    BHOP = false,
    THPT = false
  },
  Aimbot = {
    Aimbot = false,
    TriggerBot = false,
    Smoothness = 0.25,
    AimBone = "Head",
    MouseTwoDown = false, -- Dont Touch
    Silent = false,
    VisCheck = false,
    DrawFOV = false,
    FOV = 200,
    SnapLines = false,
    Delay = 0.66,
    Color = Color3.fromRGB(60, 60, 190),
    Silent2 = false,
  },
  GunMods = {
    Recoil = false,
    Spread = false,
    FireRate = false,
    FireRateAmmount = 0.1,
    InfAmmo = false,
    InfPenetration = false,
    InstaKill = false
  }
}

-- Some of the funcs
local Funcs = {}

function Funcs:IsAlive(player)
  if player and player.Character and player.Character:FindFirstChild("Head") and workspace:FindFirstChild(player.Character.Name) then
    return true
  end
end

function Funcs:Round(number)
  return math.floor(tonumber(number) + 0.5)
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

local Services = setmetatable({
  LocalPlayer = game:GetService("Players").LocalPlayer,
  Camera = workspace.CurrentCamera,
  Mouse = game:GetService("Players").LocalPlayer:GetMouse(),
}, {
  __index = function(self, idx)
    return rawget(self, idx) or game:GetService(idx)
  end
})
local things = Instance.new("Folder", Services.Workspace)
local Mouse = Services.LocalPlayer:GetMouse()
local UserInputService = game:GetService("UserInputService")
local target = false
local Client = getsenv(Services.Players.LocalPlayer.PlayerGui.Client)
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
local main = lib:Window()
Aimbot = main:Tab('Aimbot')
Esp = main:Tab('Visuals')
GunMods = main:Tab('Gun Mods')
things.Name = "teax was here"

Aimbot:Toggle('Aimbot',function(state)
  Config.Aimbot.Aimbot = state
end)

Aimbot:Toggle('Silent Aim',function(state)
  Config.Aimbot.Silent = state
end)

Aimbot:Toggle('Trigger Bot',function(state)
  Config.Aimbot.TriggerBot = state
end)

Aimbot:Dropdown(
  "Aim Bone", 
  {'Head','Torso','Left Arm','Right Arm','Left Leg','Right Leg'},
  function(selected)
    if selected == "Head" then
      Config.Aimbot.AimBone = "Head"
    elseif selected == "Torso" then
      Config.Aimbot.AimBone = "UpperTorso"
    elseif selected == "Left Arm" then
      Config.Aimbot.AimBone = "LeftLowerArm"
    elseif selected == "Right Arm" then
      Config.Aimbot.AimBone = "RightLowerArm"
    elseif selected == "Left Leg" then
      Config.Aimbot.AimBone = "LeftLowerLeg"
    elseif selected == "Right Leg" then
      Config.Aimbot.AimBone = "RightLowerLeg"
    end
  end
)

Aimbot:Toggle('Visible Check',function(state)
  Config.Aimbot.VisCheck = state
end)

Aimbot:Toggle('Draw FOV',function(state)
  Config.Aimbot.DrawFOV = state
end)

Aimbot:Toggle('Draw SnapLines',function(state)
  Config.Aimbot.SnapLines = state
end)

Aimbot:Slider('Smoothness', 0, 10, function(number)
  Config.Aimbot.Smoothness = number / 10
end)

Aimbot:Slider('FOV', 0, 1000, function(number)
  Config.Aimbot.FOV = number
end)

-- Aimbot:Label('Backtrack')

-- Aimbot:Toggle('Backtrack',function(state)
--   Config.Aimbot.Backtrack = state
-- end)

-- Aimbot:Slider('Backtrack Delay', 0, 10, function(number)
--   Config.Aimbot.Delay = number / 10
-- end)

-- Aimbot:Colorpicker("Backtrack Color",Color3.fromRGB(60, 60, 190), function(color)
--   Config.Aimbot.Color = color
-- end)
Esp:Toggle('Camera Offset Changer',function(state)
 Config.Visuals.THPT = state
end)

Esp:Slider('Camera Offset', 0.5, 32, function(number)
 Config.Visuals.THP = number
end)

Esp:Toggle('BHOP (Just bounces you up and down)',function(state)
 Config.Visuals.BHOP = state
end)

spawn(function()
while wait(.86) do
   if game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") and Config.Visuals.BHOP then
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0,25, 0)
    else 
        repeat wait() until game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
    end
end
end)

Esp:Toggle('Faster Movement',function(state)
  Config.Visuals.WST = state
end)

Esp:Slider('Movement Multiplier', 16, 40, function(number)
 Config.Visuals.WS = number
end)

Esp:Toggle('Boxes',function(state)
  Config.Visuals.BoxEsp = state
end)

Esp:Toggle('Tracers',function(state)
  Config.Visuals.TracerEsp = state
end)

Esp:Dropdown(
  "Tracers Origin",
  {'Top','Middle','Bottom','Mouse'},
  function(selected)
    Config.Visuals.TracersOrigin = selected
  end
)

Esp:Toggle('Names',function(state)
  Config.Visuals.NameEsp = state
end)

Esp:Toggle('Distance',function(state)
  Config.Visuals.DistanceEsp = state
end)

Esp:Toggle('Skeleton',function(state)
  Config.Visuals.SkeletonEsp = state
end)

Esp:Colorpicker("Team Esp Color",Color3.fromRGB(0, 190, 0), function(color)
  Config.Visuals.TeamColor = color
end)

Esp:Colorpicker("Enemy Esp Color", Color3.fromRGB(190, 190, 0),function(color)
  Config.Visuals.EnemyColor = color
end)

Esp:Toggle('No Flash Bang',function(state)
  Config.Visuals.Flash = state
end)

Esp:Toggle('Bullet Tracers',function(state)
  Config.Visuals.BulletTracers = state
end)

Esp:Colorpicker("Bullet Tracers Color",Color3.fromRGB(100, 100, 255), function(color)
  Config.Visuals.BulletTracersColor = color
end)

Esp:Toggle('Impact Points',function(state)
  Config.Visuals.ImpactPoints = state
end)

Esp:Colorpicker("Impact Points Color",Color3.fromRGB(255, 50, 50), function(color)
  Config.Visuals.ImpactPointsColor = color
end)

GunMods:Toggle('No Recoil',function(state)
  Config.GunMods.Recoil = state
end)

GunMods:Toggle('No Spread',function(state)
  Config.GunMods.Spread = state
end)

GunMods:Toggle('Fire Rate',function(state)
  Config.GunMods.FireRate = state
end)

GunMods:Slider('Fire Rate Speed', 1, 5 ,function(number)
  Config.GunMods.FireRateAmmount = number / 10
end)

GunMods:Toggle('Infinite Ammo',function(state)
  Config.GunMods.InfAmmo = state
end)

GunMods:Toggle('Infinite Penetration',function(state)
  Config.GunMods.InfPenetration = state
end)

GunMods:Toggle('Insta Kill',function(state)
  Config.GunMods.InstaKill = state
end)

-- Aimbot
function Funcs:GetTarget()
  local nearestmagnitude = math.huge
  local nearestenemy = nil
  local vector = nil
  for i,v in next, Services.Players:GetChildren() do
    if v.Team ~= Services.LocalPlayer.Team then
      if v.Character and  v.Character:FindFirstChild("HumanoidRootPart") and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health > 0 then
        local vector, onScreen = Services.Camera:WorldToScreenPoint(v.Character["HumanoidRootPart"].Position)
        if onScreen then
          local ray = Ray.new(
            Services.Camera.CFrame.p,
            (v.Character["Head"].Position-Services.Camera.CFrame.p).unit*500
          )
          local ignore = {
            Services.LocalPlayer.Character,
          }
          local hit,position,normal=workspace:FindPartOnRayWithIgnoreList(ray,ignore)
          if Config.Aimbot.VisCheck == true and hit and hit:FindFirstAncestorOfClass("Model") and Services.Players:FindFirstChild(hit:FindFirstAncestorOfClass("Model").Name)then
            local magnitude = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(vector.X, vector.Y)).magnitude
            if magnitude < nearestmagnitude and magnitude <= Config.Aimbot["FOV"] then
              nearestenemy = v
              nearestmagnitude = magnitude
            end
          elseif Config.Aimbot.VisCheck == false then
            local magnitude = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(vector.X, vector.Y)).magnitude
            if magnitude < nearestmagnitude and magnitude <= Config.Aimbot["FOV"] then
              nearestenemy = v
              nearestmagnitude = magnitude
            end
          end
        end
      end
    end
  end
  return nearestenemy
end

function Funcs:Trace(firstpos, secondpos)
  --local colorSequence = ColorSequence.new({ColorSequenceKeypoint.new(0, Color3.new(Config.Visuals.BulletTracersColor.R, Config.Visuals.BulletTracersColor.G, Config.Visuals.BulletTracersColor.B)), ColorSequenceKeypoint.new(1, Color3.new(Config.Visuals.BulletTracersColor.R, Config.Visuals.BulletTracersColor.G, Config.Visuals.BulletTracersColor.B))})
  local colorSequence = ColorSequence.new(Config.Visuals.BulletTracersColor, Config.Visuals.BulletTracersColor)
  local start = Instance.new("Part", things)
  local endd = Instance.new("Part", things)
  local Attachment = Instance.new("Attachment", start)
  local Attachment2 = Instance.new("Attachment", endd)
  local laser = Instance.new("Beam", start)
  start.Size = Vector3.new(0, 0, 0)
  start.Transparency = 1
  start.CanCollide = false
  start.CFrame = CFrame.new(firstpos)
  start.Anchored = true
  endd.Size = Vector3.new(0, 0, 0)
  endd.Transparency = 1
  endd.CanCollide = false
  endd.CFrame = CFrame.new(secondpos)
  endd.Anchored = true
  laser.FaceCamera = false
  laser.Color = colorSequence
  laser.LightEmission = 0
  laser.LightInfluence = 0
  laser.Width0 = 0.1
  laser.Width1 = 0.1
  laser.Attachment0 = Attachment
  laser.Attachment1 = Attachment2
  delay(1.6, function()
    for i = 0.5, 1.3, 0.2 do
      wait()
      laser.Transparency = NumberSequence.new(i)
    end
    start:Destroy()
    endd:Destroy()
  end)
end

function Funcs:Highlight(pos)
  local highlight = Instance.new("Part", things)
  highlight.Size = Vector3.new(0.4, 0.4, 0.4)
  highlight.Transparency = 0.5
  highlight.CanCollide = false
  highlight.Position = pos
  highlight.Anchored = true
  highlight.Color = Config.Visuals.ImpactPointsColor
  delay(2, function()
    for i = 1, 10 do
      wait()
      highlight.Transparency = highlight.Transparency + 0.05
    end
    highlight:Destroy()
  end)
end

local game_mt = getrawmetatable(game);
local namecall = game_mt.__namecall
setreadonly(game_mt, false)
game_mt.__namecall = newcclosure(function(...)
  local method = getnamecallmethod()
  local args = {...}
  if Config.Visuals.BulletTracers and tostring(method) == "FireServer" and tostring(args[1]) == "HitPart" and Services.LocalPlayer.Character and Services.LocalPlayer.Character.Gun then
    Funcs:Trace(Services.LocalPlayer.Character.Gun.Position, args[3])
  end
  if Config.Visuals.ImpactPoints and tostring(method) == "FireServer" and tostring(args[1]) == "HitPart" then
    Funcs:Highlight(args[3])
  end
  if Config.Aimbot.Backtrack and tostring(method) == "FireServer" and tostring(args[1]) == "HitPart"  and Services.Players[mtarget.Parent.Name] and Services.Players[mtarget.Parent.Name].Character and Services.LocalPlayer.Character then
    local aimbone
    local mtarget = Services.Mouse.Target
    if mtarget and mtarget.Name == "backtrackpart" then
      if mtarget.Size == Vector3.new(0.9, 0.9, 0.9) then
        aimbone = "HeadHB"
      else
        aimbone = "LowerTorso"
      end
      args[2] = Services.Players[mtarget.Parent.Name].Character[aimbone]
      args[3] = Services.Players[mtarget.Parent.Name].Character[aimbone].Position
      return args[1].FireServer(unpack(args))
    end
  end
  if Config.Aimbot.Silent and tostring(method) == "FireServer" and tostring(args[1]) == "HitPart" and Funcs:GetTarget() and Funcs:GetTarget().Character then
    args[2] = Funcs:GetTarget().Character[Config.Aimbot.AimBone]
    args[3] = Funcs:GetTarget().Character[Config.Aimbot.AimBone].Position
    return args[1].FireServer(unpack(args))
  end
  return namecall(unpack(args))
end)
setreadonly(game_mt, true)

spawn(function()
  while wait() do
    pcall(function()
        
        if Config.Visuals.WST then
           if game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Config.Visuals.WS
            end
        end
        if Config.Visuals.THPT then
        game.Players.LocalPlayer.CameraMinZoomDistance = Config.Visuals.THP
        game.Players.LocalPlayer.CameraMaxZoomDistance = Config.Visuals.THP
        end
      TargetPlayer = Funcs:GetTarget()
      if TargetPlayer and Config.Aimbot.MouseTwoDown and Config.Aimbot.Aimbot then
        local niggasbone = workspace.CurrentCamera:WorldToScreenPoint(TargetPlayer.Character[Config.Aimbot.AimBone].Position)
        local moveto = Vector2.new((niggasbone.X-Mouse.X)*Config.Aimbot.Smoothness,(niggasbone.Y-Mouse.Y)*Config.Aimbot.Smoothness)
        mousemoverel(moveto.X,moveto.Y)
      end
      if Config.Aimbot.TriggerBot == true then
        local Target = Mouse.Target
        if Target then
          local TargetPlayer = LocalPlayer.Parent:FindFirstChild(Target.Parent.Name)
          if Target.Parent and TargetPlayer ~= nil and TargetPlayer.Team ~= LocalPlayer.Team and LocalPlayer.Character.Head or Target.Name == "backtrackpart" then
            mouse1press() wait() mouse1release()
          end
        end
      end
      Services.RunService.Heartbeat:wait()
    end)
  end
end)

-- spawn(function()
--   while wait() do
--     if Services.LocalPlayer.Character and Config.Aimbot.Backtrack then
--       for i, v in pairs(Services.Players:GetPlayers()) do
--         if v.TeamColor ~= Services.LocalPlayer.TeamColor and Funcs:IsAlive(v) and v.Character:FindFirstChild("UpperTorso") and v.Character:FindFirstChild("Head") then
--           --for o, b in pairs(v.Character:GetChildren()) do
--             --if b.ClassName == "MeshPart" or b.Name == "Head" then
--               local backtrackpart = Instance.new("Part", things[v.Name])
--               backtrackpart.Transparency = 0.85
--               backtrackpart.Size = v.Character.Head.Size
--               backtrackpart.CFrame = v.Character.Head.CFrame
--               backtrackpart.Position = v.Character.Head.Position
--               backtrackpart.CanCollide = false
--               backtrackpart.Anchored = true
--               backtrackpart.Color = Config.Aimbot.Color
--               backtrackpart.Parent = things[v.Name]
--               backtrackpart.TopSurface = "Smooth"
--               backtrackpart.Name = "backtrackpart"
--               local backtrackpart2 = Instance.new("Part", things[v.Name])
--               backtrackpart2.Transparency = 0.85
--               backtrackpart2.Size = v.Character.UpperTorso.Size
--               backtrackpart2.CFrame = v.Character.UpperTorso.CFrame
--               backtrackpart2.Position = v.Character.UpperTorso.Position
--               backtrackpart2.CanCollide = false
--               backtrackpart2.Anchored = true
--               backtrackpart2.Color = Config.Aimbot.Color
--               backtrackpart2.Parent = things[v.Name]
--               backtrackpart2.TopSurface = "Smooth"
--               backtrackpart2.Name = "backtrackpart"
--               delay(Config.Aimbot.Delay, function()
--                 for i = 1, 10 do
--                   wait()
--                   backtrackpart.Transparency = backtrackpart.Transparency + 0.015
--                   backtrackpart2.Transparency = backtrackpart.Transparency + 0.015
--                 end
--                 backtrackpart:Destroy()
--                 backtrackpart2:Destroy()
--               end)
--             --end
--           --end
--         end
--       end
--     end
--   end
-- end)

Mouse.Button2Down:Connect(function()
  Config.Aimbot.MouseTwoDown = true
end)

Mouse.Button2Up:Connect(function()
  Config.Aimbot.MouseTwoDown = false
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
  Services.RunService.Stepped:Connect(function()
    if player.Team ~= Services.LocalPlayer.Team then
      Box.Color = Config.Visuals.EnemyColor
      Tracer.Color = Config.Visuals.EnemyColor
      Name.Color = Config.Visuals.EnemyColor
      Distance.Color = Config.Visuals.EnemyColor
      HeadLowerTorso.Color = Config.Visuals.EnemyColor
      NeckLeftUpper.Color = Config.Visuals.EnemyColor
      LeftUpperLeftLower.Color = Config.Visuals.EnemyColor
      NeckRightUpper.Color = Config.Visuals.EnemyColor
      RightUpperLeftLower.Color = Config.Visuals.EnemyColor
      LowerTorsoLeftUpper.Color = Config.Visuals.EnemyColor
      LeftLowerLeftUpper.Color = Config.Visuals.EnemyColor
      LowerTorsoRightUpper.Color = Config.Visuals.EnemyColor
      RightLowerRightUpper.Color = Config.Visuals.EnemyColor
    else
      Box.Color = Config.Visuals.TeamColor
      Tracer.Color = Config.Visuals.TeamColor
      Name.Color = Config.Visuals.TeamColor
      Distance.Color = Config.Visuals.TeamColor
      HeadLowerTorso.Color = Config.Visuals.TeamColor
      NeckLeftUpper.Color = Config.Visuals.TeamColor
      LeftUpperLeftLower.Color = Config.Visuals.TeamColor
      NeckRightUpper.Color = Config.Visuals.TeamColor
      RightUpperLeftLower.Color = Config.Visuals.TeamColor
      LowerTorsoLeftUpper.Color = Config.Visuals.TeamColor
      LeftLowerLeftUpper.Color = Config.Visuals.TeamColor
      LowerTorsoRightUpper.Color = Config.Visuals.TeamColor
      RightLowerRightUpper.Color = Config.Visuals.TeamColor
    end
    if Funcs:IsAlive(player) and player.Character:FindFirstChild("HumanoidRootPart") then
      local RootPosition, OnScreen = Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position)
      local HeadPosition = Services.Camera:WorldToViewportPoint(player.Character.Head.Position + Vector3.new(0, 0.5, 0))
      local LegPosition = Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position - Vector3.new(0, 4, 0))
      if Config.Visuals.BoxEsp then
        Box.Visible = OnScreen
        Box.Size = Vector2.new((2350 / RootPosition.Z) + 2.5, HeadPosition.Y - LegPosition.Y)
        Box.Position = Vector2.new((RootPosition.X - Box.Size.X / 2) - 1, RootPosition.Y - Box.Size.Y / 2)
      else
        Box.Visible = false
      end
      if Config.Visuals.TracerEsp then
        Tracer.Visible = OnScreen
        --Tracer.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X, Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).Y)
        if Config.Visuals.TracersOrigin == "Top" then
          Tracer.To = Vector2.new(Services.Camera.ViewportSize.X / 2, 0)
          Tracer.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, RootPosition.Y + (HeadPosition.Y - LegPosition.Y) / 2)
        elseif Config.Visuals.TracersOrigin == "Middle" then
          Tracer.To = Vector2.new(Services.Camera.ViewportSize.X / 2, Services.Camera.ViewportSize.Y / 2)
          Tracer.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, (RootPosition.Y + (HeadPosition.Y - LegPosition.Y) / 2) - ((HeadPosition.Y - LegPosition.Y) / 2))
        elseif Config.Visuals.TracersOrigin == "Bottom" then
          Tracer.To = Vector2.new(Services.Camera.ViewportSize.X / 2, 1000)
          Tracer.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, RootPosition.Y - (HeadPosition.Y - LegPosition.Y) / 2)
        elseif Config.Visuals.TracersOrigin == "Mouse" then
          Tracer.To = game:GetService('UserInputService'):GetMouseLocation();
          Tracer.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, (RootPosition.Y + (HeadPosition.Y - LegPosition.Y) / 2) - ((HeadPosition.Y - LegPosition.Y) / 2))
        end
      else
        Tracer.Visible = false
      end
      if Config.Visuals.NameEsp then
        Name.Visible = OnScreen
        Name.Position = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.Head.Position).X, Services.Camera:WorldToViewportPoint(player.Character.Head.Position).Y - 40)
        Name.Text = "[ " .. player.Name .. " ]"
      else
        Name.Visible = false
      end
      if Config.Visuals.DistanceEsp and player.Character:FindFirstChild("Head") then
        Distance.Visible = OnScreen
        Distance.Position = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.Head.Position).X, Services.Camera:WorldToViewportPoint(player.Character.Head.Position).Y - 25)
        Distance.Text = "[ " .. Funcs:Round((game:GetService('Players').LocalPlayer.Character.Head.Position - player.Character.Head.Position).Magnitude) .. " Studs ]"
      else
        Distance.Visible = false
      end
      if Config.Aimbot.SnapLines and player == Funcs:GetTarget() then
        SnapLines.Visible = OnScreen
        SnapLines.Color = Color3.fromRGB(255, 255, 255)
        SnapLines.To = game:GetService('UserInputService'):GetMouseLocation();
        SnapLines.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character[Config.Aimbot.AimBone].Position).X, Services.Camera:WorldToViewportPoint(player.Character[Config.Aimbot.AimBone].Position).Y)
      else
        SnapLines.Visible = false
      end
      if Config.Visuals.SkeletonEsp then
        HeadLowerTorso.Visible = OnScreen
        HeadLowerTorso.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.Head.Position).X, Services.Camera:WorldToViewportPoint(player.Character.Head.Position).Y)
        HeadLowerTorso.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LowerTorso.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LowerTorso.Position).Y)
        NeckLeftUpper.Visible = OnScreen
        NeckLeftUpper.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.Head.Position).X, Services.Camera:WorldToViewportPoint(player.Character.Head.Position).Y + ((Services.Camera:WorldToViewportPoint(player.Character.UpperTorso.Position).Y - Services.Camera:WorldToViewportPoint(player.Character.Head.Position).Y) / 3))
        NeckLeftUpper.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LeftUpperArm.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LeftUpperArm.Position).Y)
        LeftUpperLeftLower.Visible = OnScreen
        LeftUpperLeftLower.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LeftLowerArm.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LeftLowerArm.Position).Y)
        LeftUpperLeftLower.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LeftUpperArm.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LeftUpperArm.Position).Y)
        NeckRightUpper.Visible = OnScreen
        NeckRightUpper.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.Head.Position).X, Services.Camera:WorldToViewportPoint(player.Character.Head.Position).Y + ((Services.Camera:WorldToViewportPoint(player.Character.UpperTorso.Position).Y - Services.Camera:WorldToViewportPoint(player.Character.Head.Position).Y) / 3))
        NeckRightUpper.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.RightUpperArm.Position).X, Services.Camera:WorldToViewportPoint(player.Character.RightUpperArm.Position).Y)
        RightUpperLeftLower.Visible = OnScreen
        RightUpperLeftLower.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.RightLowerArm.Position).X, Services.Camera:WorldToViewportPoint(player.Character.RightLowerArm.Position).Y)
        RightUpperLeftLower.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.RightUpperArm.Position).X, Services.Camera:WorldToViewportPoint(player.Character.RightUpperArm.Position).Y)
        LowerTorsoLeftUpper.Visible = OnScreen
        LowerTorsoLeftUpper.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LowerTorso.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LowerTorso.Position).Y)
        LowerTorsoLeftUpper.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LeftUpperLeg.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LeftUpperLeg.Position).Y)
        LeftLowerLeftUpper.Visible = OnScreen
        LeftLowerLeftUpper.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LeftLowerLeg.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LeftLowerLeg.Position).Y)
        LeftLowerLeftUpper.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LeftUpperLeg.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LeftUpperLeg.Position).Y)
        LowerTorsoRightUpper.Visible = OnScreen
        LowerTorsoRightUpper.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.RightLowerLeg.Position).X, Services.Camera:WorldToViewportPoint(player.Character.RightLowerLeg.Position).Y)
        LowerTorsoRightUpper.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.RightUpperLeg.Position).X, Services.Camera:WorldToViewportPoint(player.Character.RightUpperLeg.Position).Y)
        RightLowerRightUpper.Visible = OnScreen
        RightLowerRightUpper.From = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.LowerTorso.Position).X, Services.Camera:WorldToViewportPoint(player.Character.LowerTorso.Position).Y)
        RightLowerRightUpper.To = Vector2.new(Services.Camera:WorldToViewportPoint(player.Character.RightUpperLeg.Position).X, Services.Camera:WorldToViewportPoint(player.Character.RightUpperLeg.Position).Y)
      else
        HeadLowerTorso.Visible = false
        NeckLeftUpper.Visible = false
        LeftUpperLeftLower.Visible = false
        NeckRightUpper.Visible = false
        RightUpperLeftLower.Visible = false
        LowerTorsoLeftUpper.Visible = false
        LeftLowerLeftUpper.Visible = false
        LowerTorsoRightUpper.Visible = false
        RightLowerRightUpper.Visible = false
      end
    else
      Box.Visible = false
      Tracer.Visible = false
      Name.Visible = false
      Distance.Visible = false
      HeadLowerTorso.Visible = false
      NeckLeftUpper.Visible = false
      LeftUpperLeftLower.Visible = false
      NeckRightUpper.Visible = false
      RightUpperLeftLower.Visible = false
      LowerTorsoLeftUpper.Visible = false
      LeftLowerLeftUpper.Visible = false
      LowerTorsoRightUpper.Visible = false
      RightLowerRightUpper.Visible = false
    end
  end)
end

for i, v in pairs(Services.Players:GetPlayers()) do
  if v ~= Services.LocalPlayer then
    Funcs:AddEsp(v)
    local plrfolder = Instance.new("Folder", things)
    plrfolder.Name = v.Name
    plrfolder.Parent = things
  end
end

Services.Players.PlayerAdded:Connect(function(player)
  if v ~= Services.LocalPlayer then
    Funcs:AddEsp(player)
    local plrfolder = Instance.new("Folder", things)
    plrfolder.Name = player.Name
    plrfolder.Parent = things
  end
end)

game:GetService("Players").LocalPlayer.PlayerGui.Blnd.Blind.Changed:connect(function()
  if Config.Visuals.Flash == true then
    game:GetService("Players").LocalPlayer.PlayerGui.Blnd.Enabled = false
  end
end)

local FOVCircle = Drawing.new("Circle")
FOVCircle.Color = Color3.fromRGB(190, 190, 0)
FOVCircle.Thickness = 0.5
FOVCircle.NumSides = 16
FOVCircle.Filled = false
FOVCircle.Transparency = 1

local oldgunmodules = {}
for i, v in pairs(game.ReplicatedStorage.Weapons:GetChildren()) do
  oldgunmodules[v] = {}
  if v:FindFirstChild("Ammo") and v:FindFirstChild("Recoil") and v:FindFirstChild("Spread") then
    oldgunmodules[v]["Spread"] = v.Spread.Value
    for i,d in pairs(v.Spread:GetChildren()) do
      if d.Name == "RecoveryTime" then
        oldgunmodules[v]["RecoveryTime"] = d.Value
        oldgunmodules[v]["Crouched"] = d.Crouched.Value
      else
        oldgunmodules[v][d.Name] = d.Value
      end
    end
    oldgunmodules[v]["FireRate"] = v.FireRate.Value
    oldgunmodules[v]["Auto"] = v.Auto.Value
    oldgunmodules[v]["Penetration"] = v.Penetration.Value
    oldgunmodules[v]["Bullets"] = v.Bullets.Value
  end
end

Services.RunService.Stepped:Connect(function()
  FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation();
  FOVCircle.Radius = Config.Aimbot.FOV
  if Config.Aimbot.DrawFOV then
    FOVCircle.Visible = true
  else
    FOVCircle.Visible = false
  end
  if Config.GunMods.Recoil then
    Client.RecoilX = 0
    Client.RecoilY = 0
  end
  if Config.GunMods.Spread then
    Client.resetaccuracy()
  end
  if Config.GunMods.InfAmmo then
    Client.ammocount = math.huge
    Client.ammocount2 = math.huge
    Client.ammocount3 = math.huge
    Client.ammocount4 = math.huge
  end
  for i, v in pairs(game.ReplicatedStorage.Weapons:GetChildren()) do
    if v:FindFirstChild("Ammo") and v:FindFirstChild("Recoil") and v:FindFirstChild("Spread") then
        for i,d in pairs(v.Spread:GetChildren()) do
          if Config.GunMods.Spread then
            v.Spread.Value = 0
            if d.Name == "RecoveryTime" then
              d.Value = 0
              d.Crouched.Value = 0
            else
              d.Value = 0
            end
          elseif not Config.GunMods.Spread and v.Spread.Value ~= oldgunmodules[v]["Spread"] then
            v.Spread.Value = oldgunmodules[v]["Spread"]
            if d.Name == "RecoveryTime" then
              d.Value = oldgunmodules[v]["RecoveryTime"]
              d.Crouched.Value = oldgunmodules[v]["Crouched"]
            else
              d.Value = oldgunmodules[v][d.Name]
            end
          end
        end
      if Config.GunMods.FireRate then
        v.FireRate.Value = Config.GunMods.FireRateAmmount
        v.Auto.Value = true
      elseif not Config.GunMods.FireRate and v.FireRate.Value ~= oldgunmodules[v]["FireRate"] then
        v.FireRate.Value = oldgunmodules[v]["FireRate"]
        v.Auto.Value = oldgunmodules[v]["Auto"]
      end
      if Config.GunMods.InfPenetration then
        v.Penetration.Value = 99999
      elseif not Config.GunMods.InfPenetration and v.Penetration.Value ~= oldgunmodules[v]["Penetration"] then
        v.Penetration.Value = oldgunmodules[v]["Penetration"]
      end
      if Config.GunMods.InstaKill then
        v.Bullets.Value = 10
      elseif not Config.GunMods.InstaKill and v.Bullets.Value ~= oldgunmodules[v]["Bullets"] then
        v.Bullets.Value = oldgunmodules[v]["Bullets"]
      end
    end
  end
end)

