--Open Source uwu ~ discord.gg/darkhub
--Credits to Bye...#0001 and Teax for esp
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()

CombatW = main:Tab('Combat')

Client = {
    Toggles = {
        SilentAim = false,
        Aimbot = false,
        AutoShoot = false,
        InfAmmo = false,
        NoRecoil = false
    },
    Values = {
        FOV = 200,
        Power = 0.8
    },
    Visuals = {
        Boxes = false,
        Tracers = false,
        TracersOrigin = 'Bottom'
    }
}

local Network;
repeat wait(.5)
    for i,v in pairs(getgc(true)) do
        if type(v) == 'table' and rawget(v,'send') then
            Network = v
        end
        if type(v) == 'function' and getfenv(v).script and getfenv(v).script.name == 'GunFramework' and table.find(debug.getconstants(v),'Neck') then
            u5 = v
        end
        if type(v) == 'table' and rawget(v,'ShootRecoil') then
            Recoil = v
        end
    end
until Network and u5 and Recoil

local OKUWU;
local FOVCircle = Drawing.new("Circle")
FOVCircle.Color = Color3.fromRGB(192, 57, 43)
FOVCircle.Thickness = 0.5
FOVCircle.NumSides = 460
FOVCircle.Filled = false
FOVCircle.Transparency = 0.7
FOVCircle.Visible = true

CombatW:Toggle('Silent Aim',function(state)
    Client.Toggles.SilentAim = state
end)
CombatW:Toggle('Aim Assist',function(state)
    Client.Toggles.Aimbot = state
end)
CombatW:Slider('Power',1,30,function(num)
    Client.Values.Power = num / 10
end)
CombatW:Slider('FOV',10,1000,function(val)
    Client.Values.FOV = val
end)
CombatW:Keybind('Autoclicker',Enum.KeyCode.T,function()
    Client.Toggles.AutoShoot = not Client.Toggles.AutoShoot
    pcall(function()
        if Client.Toggles.AutoShoot == true then
            OKUWU:SetText('Enabled')
            OKUWU:SetColor(Color3.new(0,1,0))
        else
            OKUWU:SetText('Diabled')
            OKUWU:SetColor(Color3.new(1,0,0))
        end
    end)
end)
CombatW:Toggle('Inf Ammo',function(state)
    Client.Toggles.InfAmmo = state
end)
CombatW:Toggle('No Recoil',function(state)
    Client.Toggles.NoRecoil = state
end)
pcall(function()
OldRecoil = Recoil.ShootRecoil
    Recoil.ShootRecoil = function(...)
        args = {...}
        if Client.Toggles.NoRecoil == true then
            return
        end
        return OldRecoil(unpack(args))
    end
end)

function inlos(p, ...)
    local cam = Workspace.CurrentCamera
    local lp = game.Players.LocalPlayer
    return #cam:GetPartsObscuringTarget({p}, {cam, lp.Character, ...}) == 0
end

mouse = game.Players.LocalPlayer:GetMouse()

MouseDown = false

spawn(function()
    while true do
        wait()
        if not dataTable or not dataTable.data then
            for i,v in pairs(getgc(true)) do
                if type(v) == 'table' and rawget(v,'data') then
                    if v.data.Ammo then
                        dataTable = v
                        print('Found datatable')
                        break
                    end
                end
            end
        end
        if Client.Toggles.AutoShoot == true and dataTable and dataTable.data and dataTable.data.FireRate then
            dataTable.data.FireRate = 0
            pcall(function()
                mouse1click()
                mouse1release()
            end)
        end
        if Client.Toggles.InfAmmo and dataTable.data and dataTable.data.Ammo then
            dataTable.data.Ammo = 1000
        end
    end
end)

function getClosestPlayerToCursor()
    local closestPlayer = nil
    local shortestDistance = math.huge
    for i, v in pairs(game:GetService("Players"):GetPlayers()) do
        if v.Name ~= game.Players.LocalPlayer.Name then
            if v.Character then
                if v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") and v.Character:FindFirstChild("Head") and not teamCheck then
                    local pos = game.workspace.CurrentCamera:WorldToViewportPoint(v.Character.HumanoidRootPart.Position)
                    local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(mouse.X, mouse.Y)).magnitude
                    if magnitude < shortestDistance and magnitude <= Client.Values.FOV then
                        closestPlayer = v
                        shortestDistance = magnitude
                    end
                end
            end
        end
    end
    return closestPlayer
end
OldSend = Network.send
Network.send = function(...)
    args = {...}
    argsnew = nil
    if args[2] == 'bullet' and Client.Toggles.SilentAim == true then
        if getClosestPlayerToCursor() ~= nil then
            pcall(function()
                if getClosestPlayerToCursor() and getClosestPlayerToCursor().Character.HumanoidRootPart and game.Players.LocalPlayer.Character:FindFirstChildOfClass('Tool').Name ~= 'Knife' then
                    CC = game.workspace.CurrentCamera
                    CurrentCameraCF = CC.CFrame
                    FakeCamera  = {
                        CFrame = CFrame.new(CurrentCameraCF.p,getClosestPlayerToCursor().Character.HumanoidRootPart.Position)
                    }
                    FakeLV = (FakeCamera).CFrame.lookVector
                    TTX,UUSI,SS = u5(FakeCamera.CFrame,FakeLV,1000,game.Players.LocalPlayer.Character:FindFirstChildOfClass('Tool').Name)
                    argsnew = {{},'bullet',TTX,UUSI,SS,CurrentCameraCF,FakeLV,1000,game.Players.LocalPlayer.Character:FindFirstChildOfClass('Tool').Name}
                end
            end)
            if argsnew then
                return OldSend(unpack(argsnew))
            else
                return OldSend(unpack(args))
            end
        end
    end
    return OldSend(unpack(args))
end
local UserInputService = game:GetService("UserInputService")
UserInputService.InputBegan:Connect(function(inputObject)
        if inputObject.UserInputType == Enum.UserInputType.MouseButton2 then
                MouseTwoDown = true
        end
end)

UserInputService.InputEnded:Connect(function(inputObject)
        if inputObject.UserInputType == Enum.UserInputType.MouseButton2 then
                MouseTwoDown = false
        end
end)

game:GetService('RunService').RenderStepped:Connect(function()
    FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation();
    FOVCircle.Radius = Client.Values.FOV
    if Client.Toggles.Aimbot == true then
        pcall(function()
            if MouseTwoDown == true then
                TargetPlayer = getClosestPlayerToCursor()
                bone = game:GetService("Workspace").CurrentCamera:WorldToScreenPoint(TargetPlayer.Character.Head.Position)
                moveto = Vector2.new((bone.X-mouse.X)*(Client.Values.Power / 10),(bone.Y-mouse.Y)*(Client.Values.Power / 10))
                mousemoverel(moveto.X,moveto.Y)
            end
        end)
    end
end)

local ESPW = main:Tab('Esp')

ESPW:Toggle('Boxes',function(state)
    Client.Visuals.Boxes = state
end)
ESPW:Toggle('Tracers',function(state)
    Client.Visuals.Tracers = state
end)


--Esp

function DrawSquare()
    local Box = Drawing.new("Square")
    Box.Color = Color3.fromRGB(190, 190, 0)
    Box.Thickness = 0.5
    Box.Filled = false
    Box.Transparency = 1
    return Box
end

function DrawLine()
    local line = Drawing.new("Line")
    line.Color = Color3.new(190, 190, 0)
    line.Thickness = 0.5
    return line
end

function AddEsp(player)
    local Box = DrawSquare()
    local Tracer = DrawLine()
    game:GetService('RunService').Stepped:Connect(function()
        if player == nil then
            Box.Visible = false
            Tracer.Visible = false
        else
            if player then
                Box.Color = Color3.new(255,0,0)
                Tracer.Color =  Color3.new(255,0,0)
                if player ~= nil and player.Character and player.Character:FindFirstChild('HumanoidRootPart') ~= nil and Box and Tracer then
                    local RootPosition, OnScreen = game.Workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position)
                    local HeadPosition = game.Workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position + Vector3.new(0, 0.5, 0))
                    local LegPosition = game.Workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position - Vector3.new(0, 4, 0))
                    if Client.Visuals.Boxes then
                        Box.Visible = OnScreen
                        Box.Size = Vector2.new((2350 / RootPosition.Z) + 2.5, HeadPosition.Y - LegPosition.Y)
                        Box.Position = Vector2.new((RootPosition.X - Box.Size.X / 2) - 1, RootPosition.Y - Box.Size.Y / 2)
                    else
                        Box.Visible = false
                    end
                    if Client.Visuals.Tracers then
                        Tracer.Visible = OnScreen
                        if Client.Visuals.TracersOrigin == "Top" then
                            Tracer.To = Vector2.new(game.Workspace.CurrentCamera.ViewportSize.X / 2, 0)
                            Tracer.From = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, RootPosition.Y + (HeadPosition.Y - LegPosition.Y) / 2)
                        elseif Client.Visuals.TracersOrigin == "Middle" then
                            Tracer.To = Vector2.new(game.Workspace.CurrentCamera.ViewportSize.X / 2, game.Workspace.CurrentCamera.ViewportSize.Y / 2)
                            Tracer.From = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, (RootPosition.Y + (HeadPosition.Y - LegPosition.Y) / 2) - ((HeadPosition.Y - LegPosition.Y) / 2))
                        elseif Client.Visuals.TracersOrigin == "Bottom" then
                            Tracer.To = Vector2.new(game.Workspace.CurrentCamera.ViewportSize.X / 2, 1000)
                            Tracer.From = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, RootPosition.Y - (HeadPosition.Y - LegPosition.Y) / 2)
                        elseif Client.Visuals.TracersOrigin == "Mouse" then
                            Tracer.To = game:GetService('UserInputService'):GetMouseLocation();
                            Tracer.From = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position).X - 1, (RootPosition.Y + (HeadPosition.Y - LegPosition.Y) / 2) - ((HeadPosition.Y - LegPosition.Y) / 2))
                        end
                    else
                        Tracer.Visible = false
                    end
                else
                    Box.Visible = false
                    Tracer.Visible = false
                end
            end
        end
    end)
end


for i, v in pairs(game.Players:GetPlayers()) do
    if v ~= game.Players.LocalPlayer then
        AddEsp(v)
    end
end

game.Players.PlayerAdded:Connect(function(player)
    if v ~= game.Players.LocalPlayer then
        AddEsp(player)
    end
end)
