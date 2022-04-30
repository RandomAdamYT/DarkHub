local OldCCC;
OldCCC = hookfunction(getrenv().xpcall,function()
    return    
end)

DarkHub_Client = {SavedSettings = false}
if isfolder and makefolder and not isfolder('DarkHub') then
    makefolder('DarkHub')
    DarkHub_Client.SaveSettings = true
    if isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
        DarkHub_Client.SavedSettings = true
        DarkHub_Client.GameSettings = game:GetService('HttpService'):JSONDecode(readfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB'))
    end
elseif isfolder('DarkHub') then
    DarkHub_Client.SaveSettings = true
    if isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
        DarkHub_Client.SavedSettings = true
        DarkHub_Client.GameSettings = game:GetService('HttpService'):JSONDecode(readfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB'))
    end
else
    DarkHub_Client.SaveSettings = false
end


local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB",true))()
main = lib:Window()
MainWindow = main:Tab('Bad Business')
Aimbotz = main:Tab('Aimbot')
Esp = main:Tab('Esp')

IsUpToDate = pcall(function()
    Client = {
        Toggles = {
            SilentAim = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.SilentAim or false,
            FOV = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.FOV or false,
            NoRecoil = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoRecoil or false,
            Fly = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Fly or false,
            BHOP = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.BHOP or false,
            BoxEsp = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.BoxEsp or false,
            TracerEsp = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.TracerEsp or false,
            ShowTeam = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.ShowTeam or false,
            Rainbow =  DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Rainbow or false,
            Rainbow2 = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Rainbow2 or false,
            Wallbang = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Wallbang or false,
            RapidFire = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.RapidFire or false,
            NoSpread = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoSpread or false
        },
        Visuals = {
            BoxEsp = false,
            TracerEsp = false,
            Names = false,
            TeamCheck = true,
            EnemyColor = Color3.fromRGB(255,0,0),
            TeamColor = Color3.fromRGB(0,255,0),
            ShowTeam = false,
            Rainbow = false,
            Rainbow2 = false
        },
        Values = {
            AimPart = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.AimPart or "Head",
            FOV = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.FOV or 100,
            ChatMsg = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.ChatMsg or "Dark HUB Winning! darkhub.xyz",
            ChatDelay = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.ChatDelay or 1,
            Speed = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.Speed or 2
        }
    }
end)
if not IsUpToDate and DarkHub_Client.SavedSettings and isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
    delfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB')
    game.Players.LocalPlayer:Kick('DarkHub Settings Out Of Date - Issue Fixed | Restart DarkHub to Continue')
end


MainWindow:Toggle("Fly", function(state)
    Client.Toggles.Fly = state
end,Client.Toggles.Fly)


local TS = require(game:GetService("ReplicatedStorage"):WaitForChild("TS"));
local Timer = TS.Timer
local Control = getupvalue(Timer.BindToHeartbeat,1)['Control']

MainWindow:Slider("Speed", 2, 10, function(num)
    Client.Values.Speed = num
    setconstant(Control,tonumber(table.find(getconstants(Control),'Stand'))+1,num)
end,Client.Values.Speed)




MainWindow:Toggle("No Recoil", function(state)
    Client.Toggles.NoRecoil = state
end,Client.Toggles.NoRecoil)
MainWindow:Toggle("No Spread", function(state)
    Client.Toggles.NoSpread = state
end,Client.Toggles.NoSpread)
MainWindow:Toggle("Rapid Fire", function(state)
    Client.Toggles.RapidFire = state
end,Client.Toggles.RapidFire)


MainWindow:Toggle("Wallbang(20m Close Range)", function(state)
    Client.Toggles.Wallbang = state
    local Raycast = require(game:GetService("ReplicatedStorage").TS).Raycast
    if state == true then
        debug.setupvalue(Raycast.CastGeometryAndEnemies, 1, nil)
        debug.setupvalue(Raycast.CastGeometryAndEnemies, 2, nil)
    else
        debug.setupvalue(Raycast.CastGeometryAndEnemies, 1, game:GetService('Workspace').Geometry)
        debug.setupvalue(Raycast.CastGeometryAndEnemies, 2, game:GetService('Workspace').Terrain)
    end
end,Client.Toggles.Wallbang)

MainWindow:Toggle('Chat Spam',function(state)
    Client.Toggles.SpamChat = state
end,Client.Toggles.SpamChat)

MainWindow:Textbox(
	"Chat Message",
	true,
	function(Text)
		Client.Values.ChatMsg = tostring(Text)
	end
)


spawn(function()
    while true do
        wait(Client.Values.ChatDelay)
        if Client.Toggles.SpamChat == true then
            game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(Client.Values.ChatMsg, "ALL")
            wait(.1)
        end
    end
end)

MainWindow:Slider("Chat Delay", 0, 10, function(num)
    Client.Values.ChatDelay = num
end)

game:GetService('UserInputService').InputBegan:connect(function(key, gpe)
    if key.KeyCode == Enum.KeyCode.LeftShift then
        Temp_Up = true
    end
    if key.KeyCode == Enum.KeyCode.LeftControl then
        Temp_Down = true
    end
end)
game:GetService('UserInputService').InputEnded:connect(function(key, gpe)
    if key.KeyCode == Enum.KeyCode.LeftShift then
        Temp_Up = false
    end
    if key.KeyCode == Enum.KeyCode.LeftControl then
        Temp_Down = false
    end
end)
Main = require(game:GetService("ReplicatedStorage"):WaitForChild("TS"));
spawn(function()
    while true do
        wait()
        pcall(function()
            if Client.Toggles.KillAura then
                for i,v in pairs(GetCharacters()) do
                    local Me = Main.Characters:GetCharacter(game.Players.LocalPlayer)
                    if Me and v.Hitbox and (v.Hitbox.Chest.Position - game.Workspace.CurrentCamera.CFrame.p).Magnitude < 20 then
                       if Me.Backpack.Equipped ~= Me:FindFirstChild('Stab',true).Parent.Parent then
                            for _,v in pairs(game:GetService("ReplicatedStorage"):FindFirstChild('Item',true).Parent:GetChildren()) do
                                if v.Name == "Item" and v.ClassName == "RemoteEvent" then
                                    v:FireServer("Equip", Me:FindFirstChild('Stab',true).Parent.Parent)   
                                end
                            end
                        end
                        local v1 = "Stab"
                        local v2 = Me:FindFirstChild('Stab',true).Parent.Parent
                        local v3 = v.Hitbox.Chest
                        local v4 = Vector3.new()
                        local v5 = Vector3.new()
                        local event = game:GetService("ReplicatedStorage"):FindFirstChild('Item_Melee',true)
                        
                        event:FireServer(v1, v2, v3, v4, v5)
                    end
                end
            end
            if Client.Toggles.Fly == true then
                game:GetService("Workspace").Gravity = 0
                Me = Main.Characters:GetCharacter(game.Players.LocalPlayer)
                if Temp_Up == true then
                    Me.Root.Velocity = Vector3.new(0,40,0)
                end
                if Temp_Down == true then
                    Me.Root.Velocity = Vector3.new(0,-40,0)
                end
                if Temp_Down == false and Temp_Up == false then
                    if Me.Root.Velocity.Y ~= 0 then
                        Me.Root.Velocity = Vector3.new(0,0,0)
                    end
                end
            else
                game:GetService("Workspace").Gravity = 110
            end
        end)
    end
end)


Aimbotz:Toggle("Silent-Aim", function(state)
    Client.Toggles.SilentAim = state
end,Client.Toggles.SilentAim)
Aimbotz:Toggle('Kill Aura',function(state)
    Client.Toggles.KillAura = state
end,Client.Toggles.KillAura)

Aimbotz:Toggle('FOV Visible',function(state)
    Client.Toggles.FOV = state
end,Client.Toggles.FOV)

Aimbotz:Slider("FOV", 15, 1000, function(num)
    Client.Values.FOV = num
end,Client.Values.FOV)

Aimbotz:Dropdown('BodyPart',{'Chest','Head','Random'},function(Sele)
    Client.Values.AimPart = Sele
end)
function GetAimPart()
    if Client.Values.AimPart == 'Random' then
        if math.random(1,3) == 1 then
            return 'Head'
        else
            return 'Chest'
        end
    else
        return Client.Values.AimPart
    end
end

--Visuals Below
--FOV
local FOVCircle = Drawing.new("Circle")
FOVCircle.Thickness = 2
FOVCircle.NumSides = 460
FOVCircle.Filled = false
FOVCircle.Transparency = 0.6
FOVCircle.Radius = Client.Values.FOV
FOVCircle.Color = Color3.new(0,255,0)

--Framework
local localPlayer = game:GetService("Players").LocalPlayer
local currentCamera = game:GetService("Workspace").CurrentCamera
local Mouse = localPlayer:GetMouse()
Main = require(game:GetService("ReplicatedStorage"):WaitForChild("TS"));
function GetCharacters()
    temptable = {}
        for i,v in pairs(game:GetService('Players'):GetPlayers()) do
            if v.Name ~= game:GetService('Players').LocalPlayer.Name and Main.Teams:GetPlayerTeam(v) ~= Main.Teams:GetPlayerTeam(game:GetService('Players').LocalPlayer) then
                temp2 = Main.Characters:GetCharacter(v)
                table.insert(temptable,temp2)
            end
        end
    return temptable
end
function getClosestPlayerToCursor() 
    local closestPlayer = nil
    local shortestDistance = math.huge
        for i, v in pairs(GetCharacters()) do
            if v:FindFirstChild('Body') and v.Body:FindFirstChild('Head') then
                local pos = currentCamera:WorldToViewportPoint(v.Body.Head.Position)
                local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(Mouse.X, Mouse.Y)).magnitude
                if magnitude < shortestDistance and magnitude <= Client.Values.FOV then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end  
    return closestPlayer
end
game:GetService("RunService").Stepped:Connect(function()
    FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation()
    FOVCircle.Radius = Client.Values.FOV
    if Client.Toggles.FOV == true then
        FOVCircle.Visible = true
    else
        FOVCircle.Visible = false
    end
end)

Main = require(game:GetService("ReplicatedStorage"):WaitForChild("TS"));
Camera =  game.Workspace.CurrentCamera
local getcallingfunction = function(stack)
    return debug.getinfo(stack + 1).func
end
Camera = game:GetService('Workspace').CurrentCamera
OldIndex = hookfunction(getrawmetatable(game).__index,function(...)
	local Self,Key = ...
	if tostring(Self) == 'Camera' and tostring(Key) == 'CFrame' and tostring(getfenv(2).script) == 'ItemControlScript' then
	    if Client.Toggles.SilentAim and getClosestPlayerToCursor() and tostring(debug.getinfo(getcallingfunction(3)).name) == 'LookVector' then
		    local target = getClosestPlayerToCursor()
            if target then
                Camera = game:GetService('Workspace').CurrentCamera
                if target:FindFirstChild('Body') then
                    local HP = target.Body:FindFirstChild(GetAimPart())
                    if HP then
                        Camera = {
                            CFrame = CFrame.new(Camera.CFrame.p,HP.Position or Vector3.new(0,0,0))
                        }
                    end
                end
                return (Camera.CFrame)
            end
		end
	end
	return OldIndex(...)
end)

local OldRANDOM;
OldRANDOM = hookfunction(getrenv().math.random,function(...)
    local Args = {...}
    if Args[1] == 7 then
        return wait(9e9)
    end
    if tostring(getfenv(2).script) == 'ItemControlScript' and Client.Toggles.NoSpread then
        if math.abs(Args[1]) == Args[2] then
            Args[1] = -0.1
            Args[2] = 0.1
            return OldRANDOM(unpack(Args))
        end
    end
    return OldRANDOM(...)
end)

OldRecoil = hookfunction(Main.Camera.Recoil.Update,function(p6, p7)
    if Client.Toggles.NoRecoil == true then
        return p6.Value - p6.LastValue;
    end
    return OldRecoil(p6,p7)
end)

Main = require(game:GetService("ReplicatedStorage"):WaitForChild("TS"));
Old = Main.Timer.Wait
Main.Timer.Wait = function(...)
    Args = {...}
    if tostring(getcallingscript()) == 'ItemControlScript' then
        if Client.Toggles.RapidFire then
            Args[2] = 0.01
        end
    end
    return Old(unpack(Args))
end

--ESP 

Esp:Toggle('Boxes',function(state)
    Client.Toggles.BoxEsp = state
end,Client.Toggles.BoxEsp)

Esp:Toggle("Tracers", function(state)
    Client.Toggles.TracerEsp = state
end,Client.Toggles.TracerEsp)

Esp:Toggle("NameEsp", function(state)
    Client.Toggles.NameEsp = state
end,Client.Toggles.NameEsp)

Esp:Toggle("TeamEsp", function(state)
    Client.Toggles.ShowTeam = state
end,Client.Toggles.ShowTeam)

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

function DrawText()
    local text = Drawing.new("Text")
    text.Color = Color3.fromRGB(190, 190, 0)
    text.Size = 20
    text.Outline = true
    text.Center = true
    return text
end

--Esp Loader

function AddEsp(player)
    local Box = DrawSquare()
    local Tracer = DrawLine()
    local Name = DrawText()
    game:GetService('RunService').Stepped:Connect(function()
        pcall(function()
            if Main.Characters:GetCharacter(player) == nil or Main.Characters:GetCharacter(player).Health.Value == 0 then
                Box.Visible = false
                Tracer.Visible = false
                Name.Visible = false
            else
                if Client.Toggles.ShowTeam then
                    if Client.Visuals.TeamCheck and Main.Teams:GetPlayerTeam(player) == Main.Teams:GetPlayerTeam(game.Players.LocalPlayer) then
                        Box.Color = Client.Visuals.TeamColor
                        Tracer.Color = Client.Visuals.TeamColor
                        Name.Color = Client.Visuals.TeamColor
                    else
                        Box.Color = Client.Visuals.EnemyColor
                        Tracer.Color = Client.Visuals.EnemyColor
                        Name.Color = Client.Visuals.EnemyColor
                    end
                    if Main.Characters:GetCharacter(player).Body:FindFirstChild("Chest") and player.InMenu.Value == false then
                        local RootPosition, OnScreen = game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Chest.Position)
                        local HeadPosition = game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Head.Position + Vector3.new(0, 0.5, 0))
                        local LegPosition = game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Chest.Position - Vector3.new(0, 4, 0))
                        if Client.Toggles.BoxEsp then
                            Box.Visible = OnScreen
                            Box.Size = Vector2.new((2350 / RootPosition.Z) + 2.5, HeadPosition.Y - LegPosition.Y)
                            Box.Position = Vector2.new((RootPosition.X - Box.Size.X / 2) - 1, RootPosition.Y - Box.Size.Y / 2)
                        else
                            Box.Visible = false
                        end
                        if Client.Toggles.TracerEsp then
                            Tracer.Visible = OnScreen
                            Tracer.To = Vector2.new(game.Workspace.CurrentCamera.ViewportSize.X / 2, 1000)
                            Tracer.From = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Chest.Position).X - 1, RootPosition.Y - (HeadPosition.Y - LegPosition.Y) / 2)
                        else
                            Tracer.Visible = false
                        end
                        if Client.Toggles.NameEsp then
                            Name.Visible = OnScreen
                            Name.Position = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Head.Position).X, game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Head.Position).Y - 40)
                            Name.Text = player.Name
                        else
                            Name.Visible = false
                        end
                    else
                        Box.Visible = false
                        Tracer.Visible = false
                        Name.Visible = false
                    end
                    if not player then
                        Box.Visible = false
                        Tracer.Visible = false
                        Name.Visible = false
                    end
                else
                    if Main.Teams:GetPlayerTeam(player) == Main.Teams:GetPlayerTeam(game.Players.LocalPlayer) then
                        Box.Visible = false
                        Tracer.Visible = false
                        Name.Visible = false
                    end
                    if Client.Visuals.TeamCheck and Main.Teams:GetPlayerTeam(player) ~= Main.Teams:GetPlayerTeam(game.Players.LocalPlayer) then
                        Box.Color = Client.Visuals.EnemyColor
                        Tracer.Color = Client.Visuals.EnemyColor
                        Name.Color = Client.Visuals.EnemyColor
                        if Main.Characters:GetCharacter(player).Body:FindFirstChild("Chest") and player.InMenu.Value == false then
                        local RootPosition, OnScreen = game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Chest.Position)
                        local HeadPosition = game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Head.Position + Vector3.new(0, 0.5, 0))
                        local LegPosition = game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Chest.Position - Vector3.new(0, 4, 0))
                        if Client.Toggles.BoxEsp then
                            Box.Visible = OnScreen
                            Box.Size = Vector2.new((2350 / RootPosition.Z) + 2.5, HeadPosition.Y - LegPosition.Y)
                            Box.Position = Vector2.new((RootPosition.X - Box.Size.X / 2) - 1, RootPosition.Y - Box.Size.Y / 2)
                        else
                            Box.Visible = false
                        end
                        if Client.Toggles.TracerEsp then
                            Tracer.Visible = OnScreen
                            Tracer.To = Vector2.new(game.Workspace.CurrentCamera.ViewportSize.X / 2, 1000)
                            Tracer.From = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Chest.Position).X - 1, RootPosition.Y - (HeadPosition.Y - LegPosition.Y) / 2)
                        else
                            Tracer.Visible = false
                        end
                        if Client.Toggles.NameEsp then
                            Name.Visible = OnScreen
                            Name.Position = Vector2.new(game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Head.Position).X, game.Workspace.CurrentCamera:WorldToViewportPoint(Main.Characters:GetCharacter(player).Body.Head.Position).Y - 40)
                            Name.Text = player.Name
                        else
                            Name.Visible = false
                        end
                    else
                        Box.Visible = false
                        Tracer.Visible = false
                        Name.Visible = false
                    end
                        if not player then
                            Box.Visible = false
                            Tracer.Visible = false
                            Name.Visible = false
                        end
                    end
                end
            end
        end)
    end)
end
  
for i, v in pairs(game:GetService('Players'):GetPlayers()) do
    if v ~= game:GetService('Players').LocalPlayer then
        AddEsp(v)
    end
end
  
game:GetService('Players').PlayerAdded:Connect(function(player)
    if v ~= game:GetService('Players').LocalPlayer then
        AddEsp(player)
    end
end)


while true do wait(5)
    if DarkHub_Client.SaveSettings then
        writefile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB',game:GetService('HttpService'):JSONEncode({['Toggles'] = Client.Toggles,['Values'] = Client.Values}))    
    end
end
