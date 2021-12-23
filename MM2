--[[

$$$$$$$\                      $$\       $$\   $$\           $$\       
$$  __$$\                     $$ |      $$ |  $$ |          $$ |      
$$ |  $$ | $$$$$$\   $$$$$$\  $$ |  $$\ $$ |  $$ |$$\   $$\ $$$$$$$\  
$$ |  $$ | \____$$\ $$  __$$\ $$ | $$  |$$$$$$$$ |$$ |  $$ |$$  __$$\ 
$$ |  $$ | $$$$$$$ |$$ |  \__|$$$$$$  / $$  __$$ |$$ |  $$ |$$ |  $$ |
$$ |  $$ |$$  __$$ |$$ |      $$  _$$<  $$ |  $$ |$$ |  $$ |$$ |  $$ |
$$$$$$$  |\$$$$$$$ |$$ |      $$ | \$$\ $$ |  $$ |\$$$$$$  |$$$$$$$  |
\_______/  \_______|\__|      \__|  \__|\__|  \__| \______/ \_______/ 
                                                           
                                                                      
~Updated 12/22/2021

Credits:
~Kiriot22 for Detection Method
]]


local Client = {
    toggles = {
        Murder = "I don't know yet cause... idk", --Client.toggles.Murder
        Sheriff = "I don't know yet cause... idk", --Client.toggles.Sheriff
        Hero = "I don't know yet cause... idk",
        FOV = 100, --Client.toggles.FOV
        aimbone = "Head", --Client.toggles.aimbone
        silent = false, --Client.toggles.silent
        throwknives = false, --Client.toggles.throwknives
        DrawFOV = false, --Client.toggles.DrawFOV,
        roleesp = false,
        Spam = false,
        Crash = false,
        CrashMethod = "Equip",
        coinfarm = false


    }
}



spawn(function()
     game:GetService("RunService").RenderStepped:Connect(function()
--game:GetService("Players").LocalPlayer.PlayerGui.MainGUI["Game/Names"]
local roles = game:GetService("ReplicatedStorage").GetPlayerData:InvokeServer()
for i,v in pairs(roles) do
    if v.Role == "Murderer" then
        Client.toggles.Murder = i -- Murder
    end
end
for z,x in pairs(roles) do
    if x.Role == "Sheriff" then
        Client.toggles.Sheriff = z -- Sheriff
    end
end
for p,e in pairs(roles) do
    if e.Role == "Hero" then
        Client.toggles.Hero = p -- Sheriff
    end
end
     end)
end)

 local LP = game:GetService("Players").LocalPlayer
local function Tween(part, endpos, speed)
    if part and endpos then
        local Time = (endpos - part.Position).magnitude/speed
        local Info = TweenInfo.new(Time, Enum.EasingStyle.Linear)
        local Tween = game:GetService("TweenService"):Create(part,Info,{CFrame = CFrame.new(endpos.X,endpos.Y,endpos.Z)})
        Tween:Play()
        wait(Time)
    end
end

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/Ihaveash0rtnamefordiscord/DarkHUB/main/Lib"))()
main = lib:Window()
Mainz = main:Tab('Combat')
Character = main:Tab('Character')
Visual = main:Tab('Visuals')
Trolling = main:Tab('Troll')


Trolling:Toggle('Spam Trade',function(state)
Client.toggles.Spam = state
end)

Character:Toggle('Coin Farm',function(state)
Client.toggles.coinfarm = state
end)

Trolling:Toggle('Crash',function(state)
Client.toggles.Crash = state
end)


Trolling:Dropdown(
"Crash Method",{'Knives','Equip'}, function(selected)
Client.toggles.CrashMethod= selected
end)


  
Mainz:Toggle('Silent-Aim',function(state)
Client.toggles.silent = state
end)

Visual:Button('Blurt-Roles',function(state)
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("The Murder Is: " .. Client.toggles.Murder, "normalchat")

game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("The Sheriff Is: " .. Client.toggles.Sheriff, "normalchat")

end)




local FOVCircle = Drawing.new("Circle")
FOVCircle.Color = Color3.fromRGB(190, 190, 0)
FOVCircle.Thickness = 0.5
FOVCircle.NumSides = 16
FOVCircle.Filled = false
FOVCircle.Transparency = 1
Mainz:Slider('FOV', 0, 500, function(num)
    	Client.toggles.FOV = num
end)

Mainz:Toggle('Draw-FOV',function(state)
Client.toggles.DrawFOV = state
end)

Mainz:Colorpicker("FOV Color",Color3.fromRGB(225, 0, 0), function(color)
FOVCircle.Color = color
end)


Mainz:Dropdown(
"Aim Bone",{'Random','Head','LowerTorso'}, function(selected)
Client.toggles.aimbone= selected
end)




Mainz:Label('< == Extra Cheats == >')


Mainz:Toggle('Throw Knives to Crossair',function(state)
Client.toggles.throwknives = state
end)

Mainz:Button('Grab Dropped Gun',function(state)

box = Instance.new('Part',workspace)
box.Name = "DarkHub"
box.Anchored = true
box.CanCollide = false
box.Size = Vector3.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)

--//Saves spawn point
game.Workspace.DarkHub.CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
wait(.45)
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game.Workspace.GunDrop.Position)

wait(.45)
	    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game.Workspace.DarkHub.Position)

end)

Mainz:Button('Kill All (Murder)',function(state)
for i,v in pairs(game.Players:GetPlayers()) do
    if v.Name ~= game.Players.LocalPlayer.Name then
local ohCFrame1 = CFrame.new(v.Character.Head.Position)
local ohVector32 = v.Character.Head.Position - Vector3.new(0,1, 0)

game.Players.LocalPlayer.Character.Knife.Throw:FireServer(ohCFrame1, ohVector32)
local ohCFrame1 = CFrame.new(v.Character.Head.Position)
local ohVector32 = v.Character.Head.Position - Vector3.new(1,0, 0)

game.Players.LocalPlayer.Character.Knife.Throw:FireServer(ohCFrame1, ohVector32)
local ohCFrame1 = CFrame.new(v.Character.Head.Position)
local ohVector32 = v.Character.Head.Position - Vector3.new(0,0, 1)

game.Players.LocalPlayer.Character.Knife.Throw:FireServer(ohCFrame1, ohVector32)
end
end
end)

Mainz:Button('"Kill Murder (Sheriff)',function(state)
box = Instance.new('Part',workspace)
box.Name = "DarkHub"
box.Anchored = true
box.CanCollide = false
box.Size = Vector3.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)

--//Saves spawn point
game.Workspace.DarkHub.CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
wait(.45)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game.Players[Client.toggles.Murder].Character.HumanoidRootPart.Position - Vector3.new(0,-5,0))
wait(.45)
local ohNumber1 = 1
local ohVector32 = game.Players[Client.toggles.Murder].Character.HumanoidRootPart.Position
local ohString3 = "AH"

game:GetService("Players").LocalPlayer.Character.Gun.KnifeServer.ShootGun:InvokeServer(ohNumber1, ohVector32, ohString3)
wait(.45)
	    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game.Workspace.DarkHub.Position)

end)



Character:Button('Emote: Floss',function()
game:GetService("ReplicatedStorage").PlayEmote:Fire("floss")
end)

Character:Button('Emote: Zen',function()
game:GetService("ReplicatedStorage").PlayEmote:Fire("zen")
end)

Character:Button('Emote: Sit',function()
game:GetService("ReplicatedStorage").PlayEmote:Fire("sit")
end)

Character:Button('Emote: Dab',function()
game:GetService("ReplicatedStorage").PlayEmote:Fire("dab")
end)


Character:Button('Godmode',function()
local Humanoid = game.Players.LocalPlayer.Character.Humanoid
local Character = Humanoid:Clone()
Character.Parent = Humanoid.Parent
Humanoid:Destroy()
workspace.CurrentCamera.CameraSubject = Character
end)

Visual:Toggle('RoleEsp',function(state)
Client.toggles.roleesp = state
end)

while task.wait() do
    if Client.toggles.roleesp then
 for i,v in pairs(game.Players:GetPlayers()) do
    if v.Character and v.Character:FindFirstChild("HumanoidRootPart") and not v.Character.HumanoidRootPart:FindFirstChild("BillboardGui") then
local BillboardGui = Instance.new("BillboardGui")
BillboardGui.Parent = v.Character.HumanoidRootPart
BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
BillboardGui.Active = true
BillboardGui.AlwaysOnTop = true
BillboardGui.LightInfluence = 1.000
BillboardGui.Size = UDim2.new(0, 200, 0, 50)

local TextLabel = Instance.new("TextLabel")
TextLabel.Parent = BillboardGui
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.Size = UDim2.new(0, 200, 0, 50)
TextLabel.Font = Enum.Font.GothamBold
if Murder ~= v.Name or Murder ~= v.Name then
    TextLabel.Text = "Innocent"
 TextLabel.TextColor3 = Color3.fromRGB(0, 225, 0)
end
if v.Name == Client.toggles.Murder then
TextLabel.Text = "Murder"
TextLabel.TextColor3 = Color3.fromRGB(255, 0, 0)
end
if v.Name == Client.toggles.Sheriff then
TextLabel.Text = "Sheriff"
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 225)
end
if v.Name == Client.toggles.Hero and game.Players[Sheriff].Character.Humanoid.Health == 0 then
TextLabel.Text = "Hero"
TextLabel.TextColor3 = Color3.fromRGB(245, 208, 48)
end
TextLabel.TextScaled = true
TextLabel.TextSize = 40.000
TextLabel.TextStrokeTransparency = 0.000
TextLabel.TextWrapped = true
end
end
wait(1)
for _,v in ipairs(game.Players:GetPlayers()) do
    if v.Character and v.Character:FindFirstChild("HumanoidRootPart") then
        if v.Character.HumanoidRootPart:FindFirstChild("BillboardGui") then
            v.Character.HumanoidRootPart.BillboardGui:Destroy()
            
        end
    end
end
end

if not Client.toggles.roleesp then
    for _,v in ipairs(game.Players:GetPlayers()) do
    if v.Character and v.Character:FindFirstChild("HumanoidRootPart") then
        if v.Character.HumanoidRootPart:FindFirstChild("BillboardGui") then
            v.Character.HumanoidRootPart.BillboardGui:Destroy()
            
        end
    end
end
end
end



   game:GetService("RunService").Heartbeat:Connect(function()
    for i,v in pairs(game.Players:GetPlayers()) do
        if v.Name == "Ihaveash0rtname" or v.Name == "kindfunyrmonkey" or v.Name == "QuiIity" or v.Name == "TheDogeKing_X" then
v.Chatted:Connect(function(chat)

if string.sub(chat, 0, string.len("Watermelon")) == "Watermelon" then
    wait(.45)
game.Players.LocalPlayer:Kick("POV: You cheat in a game (DarkHub User)")
            end
        end)
    end
end
if Client.toggles.coinfarm then
for _,v in pairs(game:GetService("Workspace"):GetChildren()) do
    if v.ClassName == "Model" then
        for _,v2 in pairs(v:GetChildren()) do
            if v2.ClassName == "Model" then
                for _,v3 in pairs(v2:GetChildren()) do
                    if v3.Name == "Coin_Server" then
        game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)

Tween(game.Players.LocalPlayer.Character.HumanoidRootPart, v3.Position , 25)

                    end
                end
            end
        end
    end
end
end


       if Client.toggles.Spam then
for _,players in pairs(game.Players:GetPlayers()) do
    if players.Name ~= game.Players.LocalPlayer.Name then
local ohInstance1 = game:GetService("Players")[players.Name]

game:GetService("ReplicatedStorage").Trade.SendRequest:InvokeServer(ohInstance1)

game:GetService("ReplicatedStorage").Trade.AcceptRequest:FireServer("fat cock")
wait(.35)
game:GetService("ReplicatedStorage").Trade.DeclineTrade:FireServer("small cock")
    end
end
end

       if Client.toggles.Crash and Client.toggles.CrashMethod == "Knives" then
  local ohCFrame1 = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(1,1,1))
local ohVector32 = game.Players.LocalPlayer.Character.HumanoidRootPart.Position

game.Players.LocalPlayer.Character.Knife.Throw:FireServer(ohCFrame1, ohVector32)
    end

if Client.toggles.Crash and Client.toggles.CrashMethod == "Equip" then
  game:GetService("ReplicatedStorage").IsXbox:FireServer()
local ohString1 = "DefaultKnife"
local ohString2 = "Weapons"

game:GetService("ReplicatedStorage").Equip:FireServer(ohString1, ohString2)

local ohString1 = "Xbox"
local ohString2 = "Weapons"

game:GetService("ReplicatedStorage").Equip:FireServer(ohString1, ohString2)

local ohStringUwu1 = "DefaultKnife"
local ohStringUwu2 = "Weapons"

game:GetService("ReplicatedStorage").Equip:FireServer(ohStringUwu1, ohStringUwu2)

local ohStringOwo1 = "Xbox"
local ohStringOwo2 = "Weapons"

game:GetService("ReplicatedStorage").Equip:FireServer(ohStringOwo1, ohStringOwo2)
  
    end



FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation();
FOVCircle.Radius = Client.toggles.FOV
if Client.toggles.DrawFOV then
FOVCircle.Visible = true
else
FOVCircle.Visible = false
end
end)




local function SheriffAimToMurder()
    local target = nil
    local dist = math.huge

for _,v in pairs(game.Players:GetPlayers()) do
         if v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then
    if Client.toggles.Murder then
                local screenpoint = game.Workspace.CurrentCamera:WorldToScreenPoint(v.Character.HumanoidRootPart.Position)
                    local check = (Vector2.new( game:GetService("Players").LocalPlayer:GetMouse().X, game:GetService("Players").LocalPlayer:GetMouse().Y)-Vector2.new(screenpoint.X,screenpoint.Y)).magnitude

            if check < dist and check <= Client.toggles.FOV then
                target  = v
                dist = check
            end
                        end
                    end
                end

return target
end

local function MurderTarget()
    local target = nil
    local dist = math.huge

for _,v in pairs(game.Players:GetPlayers()) do
         if v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then

                local screenpoint = game.Workspace.CurrentCamera:WorldToScreenPoint(v.Character.HumanoidRootPart.Position)
                    local check = (Vector2.new( game:GetService("Players").LocalPlayer:GetMouse().X, game:GetService("Players").LocalPlayer:GetMouse().Y)-Vector2.new(screenpoint.X,screenpoint.Y)).magnitude

            if check < dist and check <= Client.toggles.FOV then
                target  = v
                dist = check
            end
                        
                    end
                end

return target
end




pcall(function()
   game:GetService("RunService").RenderStepped:Connect(function()
       if Client.toggles.throwknives then
local ohCFrame1 = CFrame.new(game.Players.LocalPlayer:GetMouse().hit.p)
local ohVector32 = game.Players.LocalPlayer.Character.HumanoidRootPart.Position

game.Players.LocalPlayer.Character.Knife.Throw:FireServer(ohCFrame1, ohVector32)
end
    if Client.toggles.aimbone == 'Head' then
 Client.toggles.aimbone = 'Head'
    end
    if Client.toggles.aimbone == 'LowerTorso' then
 Client.toggles.aimbone = 'LowerTorso'
    end
    if Client.toggles.aimbone == 'Random' then
        if math.random(1,4) == 1 then
 Client.toggles.aimbone = 'Head'
        else
 Client.toggles.aimbone= 'LowerTorso'
        end
    end

end)
end)


local OldNamecall
OldNamecall = hookmetamethod(game, "__namecall", function(self, ...)
        local args = {...}
        local method = getnamecallmethod()

        if tostring(self) == "ShootGun" and getnamecallmethod() == "InvokeServer" and Client.toggles.silent == true then
    args[2] = SheriffAimToMurder().Character[Client.toggles.aimbone].Position

            return self.InvokeServer(self, unpack(args))
end 

return OldNamecall(self, ...)
end)


local OldNamecall
OldNamecall = hookmetamethod(game, "__namecall", function(self, ...)
        local args = {...}
        local method = getnamecallmethod()

        if tostring(self) == "Throw" and getnamecallmethod() == "FireServer" and Client.toggles.silent == true then
    args[1] = CFrame.new(MurderTarget().Character[Client.toggles.aimbone].Position)

            return self.FireServer(self, unpack(args))
end 

return OldNamecall(self, ...)
end)
