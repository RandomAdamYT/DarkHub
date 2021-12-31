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
local main = lib:Window()
local Aimbotz = main:Tab('Aimbot')
local LP_TAB = main:Tab('LocalPlayer')
local Teleport = main:Tab('Teleports')

local Client;

IsUpToDate = pcall(function()
    Client = {
        Toggles = {
            SilentAim = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.SilentAim or false,
            FOV = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.FOV or false,
            NoClip = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoClip or false,
            Stamina = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Stamina or false,
            WalkSpeed = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.WalkSpeed or false
        },
        Values = {
            AimPart = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.AimPart or "Head",
            FOV = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.FOV or 200,
            Speed = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.Speed or 13
        }
    }
end)
if not IsUpToDate and DarkHub_Client.SavedSettings and isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
    delfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB')
    return game.Players.LocalPlayer:Kick('DarkHub Settings Out Of Date - Issue Fixed | Restart DarkHub to Continue')
end

local CS = game:GetService('CollectionService')
local currentCamera = game.Workspace.CurrentCamera
local Mouse = game.Players.LocalPlayer:GetMouse()
function getClosestPlayerToCursor()
    local closestPlayer = nil
    local shortestDistance = math.huge
        for i, v in pairs(CS:GetTagged("Characters")) do
            if v:FindFirstChild('HumanoidRootPart') and v:FindFirstChild('Head') and v.Name ~= game.Players.LocalPlayer.Name then
                local pos = currentCamera:WorldToViewportPoint(v.Head.Position)
                local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(Mouse.X, Mouse.Y)).magnitude
                if magnitude < shortestDistance and magnitude <= Client.Values.FOV then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end  
    return closestPlayer
end

Old = hookfunction(Instance.new,function(...)
    if tostring(getcallingscript()) == 'InteractionSystem' then
        return wait(9e9)
    end
    return Old(...)    
end)
OldIndex = hookfunction(getrawmetatable(game).__index,function(self,Key)
    if tostring(self) == 'HumanoidRootPart' and tostring(Key) == 'CFrame' and tostring(getfenv(2).script) == 'GunHandlerLocal' then
        return CFrame.new(0,0,0)
    end
    if tostring(Key) == 'Hit' and tostring(getcallingscript()) == 'MainGunScript' and Client.Toggles.SilentAim and getClosestPlayerToCursor() then
        return getClosestPlayerToCursor().Head.CFrame
    end
    return OldIndex(self,Key) 
end)

local FOVCircle = Drawing.new("Circle")
FOVCircle.Thickness = 2
FOVCircle.NumSides = 460
FOVCircle.Filled = false
FOVCircle.Transparency = 0.6
FOVCircle.Radius = Client.Values.FOV
FOVCircle.Color = Color3.new(0,255,0)

game:GetService("RunService").Stepped:Connect(function()
    FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation()
    FOVCircle.Radius = Client.Values.FOV
    if Client.Toggles.FOV then
        FOVCircle.Visible = true
    else
        FOVCircle.Visible = false
    end
    if Client.Toggles.NoClip then
        for i,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
            if v:IsA('BasePart') then
                v.CanCollide = false
            end
        end
    end
    if Client.Toggles.WalkSpeed and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild('Humanoid') then
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Client.Values.Speed
    end
end)

Aimbotz:Toggle('Silent Aim', function(state)
    Client.Toggles.SilentAim = state
end,Client.Toggles.SilentAim)
Aimbotz:Toggle('Show FOV', function(state)
    Client.Toggles.FOV = state
end,Client.Toggles.FOV)
Aimbotz:Slider('FOV', 15, 1000, function(num)
    Client.Values.FOV = num
end,Client.Values.FOV)


LP_TAB:Toggle('No Clip', function(state)
    Client.Toggles.NoClip = state
end,Client.Toggles.NoClip)
LP_TAB:Toggle('Inf Stamina', function(state)
    Client.Toggles.Stamina = state
end,Client.Toggles.Stamina)
LP_TAB:Toggle('Custom WalkSpeed Enabled?', function(state)
    Client.Toggles.WalkSpeed = state
end,Client.Toggles.WalkSpeed)
LP_TAB:Slider('Custom WalkSpeed', 13, 350, function(num)
    Client.Values.Speed = num
end,Client.Values.Speed)
   LP_TAB:Textbox("Custom Outfit (Clothes ID)", false, function(Text)
game:GetService("ReplicatedStorage")["_CS.Events"].EquipAvatarItem:FireServer("CustomCloth",Text)
end)

LP_TAB:Colorpicker("Skin Color",Color3.new(1,1,1), function(color)
game:GetService("ReplicatedStorage")["_CS.Events"].EquipAvatarItem:FireServer("Color",color,"SkinColor")
end)

LP_TAB:Colorpicker("Hair Color",Color3.new(1,1,1), function(color)
game:GetService("ReplicatedStorage")["_CS.Events"].EquipAvatarItem:FireServer("Color",color,"HairColor")
end)


Teleport:Button("Pahrump", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations.Pahrump:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)

Teleport:Button("Arway", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations.Arway:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)

Teleport:Button("Sheriff Station", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Sheriff Station"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)

Teleport:Button("Depository", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Depository"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)

Teleport:Button("Eastdike", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Eastdike"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)

Teleport:Button("Eaphis Plateau", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Eaphis Plateau"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)

Teleport:Button("Okby Steppe", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Okby Steppe"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)

Teleport:Button("Towing Company", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Towing Company"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)
Teleport:Button("Clinic", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Clinic"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)
Teleport:Button("Airfield", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Airfield"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)
Teleport:Button("Depot", function()
    for _,v in pairs(game:GetService("Workspace").Spawns.SpawnLocations["Depot"]:GetChildren()) do
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v.Position + Vector3.new(0,4,0))
    end
end)
local function getNearestGun()
    local TargetDistance = math.huge
    local Target
for _,v in pairs(game:GetService("Workspace").Entities:GetChildren()) do
    if v:FindFirstChild("Info") then
        if v.Info:FindFirstChild("PrimaryColor") or v.Info:FindFirstChild("SecondaryColor") then
            local Mag = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v:FindFirstChildOfClass("Part").Position).Magnitude
            if Mag < TargetDistance then
                TargetDistance = Mag
                Target = v
            end
        end
    end
end
    return Target
end;
local function getNearestProp()
    local TargetDistance = math.huge
    local Target
for _,v in pairs(game:GetService("Workspace").Entities:GetChildren()) do
    if v:FindFirstChild("Properties") then
        if v.Properties:FindFirstChild("ItemLocked") then
            if v.Properties.ItemLocked.Value == false then
                local Mag = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v:FindFirstChildOfClass("Part").Position).Magnitude
                    if Mag < TargetDistance then
                        TargetDistance = Mag
                        Target = v
                    end
            end
        end
    end
end
    return Target
end;

Teleport:Label('Misc. Teleports')
Teleport:Button("Teleport to Nearest Gun", function()
        local LastPos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
wait(.3)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getNearestProp().Handle.Position + Vector3.new(0,4,0))
wait(.45)
Game:GetService("ReplicatedStorage")["_CS.Events"].Dropper:FireServer(
    getNearestGun(),
    "PickUp"
)
wait(1)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(LastPos)


end)
Teleport:Button("Teleport to Nearest Prop", function()
if getNearestProp() ~= nil then
if getNearestProp().Name == "Simple Printer" and getNearestProp().Properties.CurrentPrinted.Value ~= 0 then
    local LastPos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getNearestProp().Handle.Position)
      wait(.45)
         Game:GetService("ReplicatedStorage")["_CS.Events"].UsePrinter:FireServer(
        getNearestProp()
 )
 wait(1)
       game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(LastPos)


elseif getNearestProp().Name ~= "Simple Printer" then
     local LastPos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
 game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getNearestProp().Handle.Position)
wait(.45)
     Game:GetService("ReplicatedStorage")["_CS.Events"].DeliveryFunction:FireServer(
     "TakeItem",
     v
 )
  wait(1)
       game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(LastPos)

end
else
    game.StarterGui:SetCore("SendNotification", {
Title = "DarkHub";
Text = "Hey, It seems there is no current Entities that can be picked up or claimed!";
Duration = 10;
})
end
end)




spawn(function()
    while true do wait(.2)
        if Client.Toggles.Stamina and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild('Humanoid') then
            for i,v in pairs(getconnections(game.Players.LocalPlayer.Character.Humanoid:GetPropertyChangedSignal("Jump"))) do
                if getfenv(v.Function).script.Parent and getfenv(v.Function).script.Parent.Name == game.Players.LocalPlayer.Name then
                    print('yuo')
                    setupvalue(v.Function,2,100)
                end
            end
        end
    end
end)


spawn(function()
    while true do wait(5)
        if DarkHub_Client.SaveSettings then
            writefile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB',game:GetService('HttpService'):JSONEncode({['Toggles'] = Client.Toggles,['Values'] = Client.Values}))    
        end
    end
end)
