--Love from Felix
local LP = game:GetService("Players").LocalPlayer
local ts = game:GetService("TweenService")
local function Tween(part, endpos, speed)
    if part and endpos then
        local Time = (endpos - part.Position).magnitude/speed
        local Info = TweenInfo.new(Time, Enum.EasingStyle.Linear)
        local Tween = ts:Create(part,Info,{CFrame = CFrame.new(endpos.X,endpos.Y,endpos.Z)})
        Tween:Play()
        wait(Time)
    end
end

settings = {
    AutoAttack = false,
    TweenCoolDown = .25,
    SlashCooldown = 1,
    KillCount = 3,
    Cooldown = 5,
    TweenSpeed = 800
    
}
    local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB",true))() -- UI Lib do not change
    main = lib:Window() -- lets us create a black Window 
    MainWindow = main:Tab('untitled AOT') -- make a first Tab1 
    LP = main:Tab('Character') -- make a first Tab1 

    LP:Slider("WalkSpeed", 28, 200, function(num) -- slidder can be used for Walkspeed changer, FOV, etc.
        game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = num
    end)
        LP:Slider("JumpPower", 50, 200, function(num) -- slidder can be used for Walkspeed changer, FOV, etc.
        game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid").JumpPower = num
    end)
    MainWindow:Toggle("AutoAttack", function(state) -- Toggle for making a toggle for ex. Esp.
         settings.AutoAttack = state
    end)
    
    MainWindow:Slider("Tween To Target Cooldown", 0, 10, function(num) -- slidder can be used for Walkspeed changer, FOV, etc.
        settings.TweenCoolDown = num
    end)
    MainWindow:Slider("Attack Speed", 0, 5, function(num) -- slidder can be used for Walkspeed changer, FOV, etc.
        settings.SlashCooldown = num
    end)
    MainWindow:Slider("Tween Speed", 100, 2500, function(num) -- slidder can be used for Walkspeed changer, FOV, etc.
        settings.TweenSpeed = num
    end)
    

    MainWindow:Slider("How many kills before cooldown", 0, 5, function(num) -- slidder can be used for Walkspeed changer, FOV, etc.
        settings.KillCount = num
    end)    

    MainWindow:Slider("Kill Cooldown Between kills", 0, 5, function(num) -- slidder can be used for Walkspeed changer, FOV, etc.
        settings.Cooldown = num
    end)
    
-- // MAIN SOURCE LEAVE BELOW  \\ -- 
local Count = 0


local function getNearestTitan()
    local TargetDistance = math.huge
    local Target
    for i, v in ipairs(workspace:GetChildren()) do
        if v.Name == "Titan" then
            if v:FindFirstChildOfClass("Humanoid").Health >= 1 then
            local Mag = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v:FindFirstChild("Head").Position).Magnitude
                    if Mag < TargetDistance then
                        TargetDistance = Mag
                        Target = v
                    end
            end
        end
    end
    return Target
end;

local LastSafePos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
local LastKnowKillStreakData = game:GetService("Players").LocalPlayer.leaderstats.Killstreak.Value
spawn(function()
while task.wait() do
       if game:GetService("Players").LocalPlayer.leaderstats.Killstreak.Value == LastKnowKillStreakData + settings.KillCount then
            print('Player has gained '.. settings.KillCount..' kills!')
            Count = Count + settings.KillCount 
            LastKnowKillStreakData = game:GetService("Players").LocalPlayer.leaderstats.Killstreak.Value
        end
    end
end)

 spawn(function()
     while task.wait(settings.TPCoolDown) do
         if settings.AutoAttack then
         pcall(function()
            if Count >= settings.KillCount then
                print(Count .. ' Titans were killed! Waiting cooldown...')
                wait(settings.Cooldown) -- Cooldown as game detects fast movement/kills
                         Count = 0 -- reset out counter
                         print('Cooldown down! Starting Auto-Farm!') -- debug print
                         else -- if we are not on cooldown
                             if getNearestTitan() then -- just testing that we do have a target
                            --  print('going to a new titan')
            if Count <= settings.KillCount - 1 then
                Tween(game.Players.LocalPlayer.Character.HumanoidRootPart, getNearestTitan().Head.Position + getNearestTitan().Head.CFrame.LookVector *-2, settings.TweenSpeed)
            --game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getNearestTitan().Head.Position + getNearestTitan().Head.CFrame.LookVector *-2) -- go behind the target
            
                end
                end
            end
         end)
         end
    end
 end)


 spawn(function()
     while task.wait(settings.SlashCooldown) do
         if settings.AutoAttack then
         pcall(function()
             if Count <= settings.KillCount - 1 and getNearestTitan() then
                 -- print("Attempting to Attack a Titan")
                game:GetService("ReplicatedStorage").DamageEvent:FireServer(nil, getNearestTitan():FindFirstChildOfClass("Humanoid"), "&@&*&@&", getNearestTitan())
             end
         
         end)
         end
    end
 end)
