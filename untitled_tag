 -- FeIix was here <3
local Client = {
    toggles = {
        Spam = false,
        Float = false,
        WST = false,
        WS = 50,
        JP = 100,
        JPT = false

    }
}

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB"))()
local main = lib:Window()
local LP = main:Tab('LocalPlayer')
local Troll = main:Tab('Troll')


LP:Toggle('WalkSpeed Toggle',function(state)
Client.toggles.WST = state
end)

LP:Slider('WalkSpeed', 11, 150, function(num)
    	Client.toggles.WS = num
end)
LP:Toggle('JumpPower Toggle',function(state)
Client.toggles.JPT = state
end)
LP:Slider('JumpPower', 35, 150, function(num)
    	Client.toggles.JP = num
end)

local function Check()
    if Client.toggles.WST then
    game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = Client.toggles.WS
    end
    end
game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):GetPropertyChangedSignal("WalkSpeed"):Connect(Check)

local function Check2()
    if Client.toggles.JPT then
    game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").JumpPower = Client.toggles.JP
    end
    end
game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):GetPropertyChangedSignal("JumpPower"):Connect(Check2)

Troll:Button('Force Jump All',function()
    for _,v in pairs(game.Players:GetPlayers()) do
        if v.Character and v ~= game.Players.LocalPlayer then
            game:GetService("ReplicatedStorage").RemoteEvents.TagPlayer:InvokeServer(Vector3.new(2,2,2), v.Character:FindFirstChild("Head"), v.Character:FindFirstChild("Head"))
        end
    end
end)
Troll:Toggle('Float ClosestToCursor',function(state)
Client.toggles.Float = state
end)

Troll:Toggle('Sound Spam',function(state)
Client.toggles.Spam = state
end)


local function MurderTarget()
    local target = nil
    local dist = math.huge

for _,v in pairs(game.Players:GetPlayers()) do
         if v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then

                local screenpoint = game.Workspace.CurrentCamera:WorldToScreenPoint(v.Character.HumanoidRootPart.Position)
                    local check = (Vector2.new( game:GetService("Players").LocalPlayer:GetMouse().X, game:GetService("Players").LocalPlayer:GetMouse().Y)-Vector2.new(screenpoint.X,screenpoint.Y)).magnitude

            if check < dist and check <= 100 then
                target  = v
                dist = check
            end
                        
                    end
                end

return target
end



spawn(function()
    while task.wait() do
            if MurderTarget() ~= nil and Client.toggles.Float == true then
        game:GetService("ReplicatedStorage").RemoteEvents.TagPlayer:InvokeServer(Vector3.new(2,2,2), MurderTarget().Character:FindFirstChild("Head"), MurderTarget().Character:FindFirstChild("Head"))
    end
        if Client.toggles.Spam then
game:GetService("ReplicatedStorage").RemoteEvents.ReplicateSound:FireServer(
    "rbxassetid://8397068820", -- ID / Must be game default id
    workspace, -- parent
    nil,  -- Ignore
    10, -- pitch
    10, -- volume
    "AlertAll" -- Key (AlertAll, DeathCry, ReturnData, Scream)
     )

end
end
    end)
