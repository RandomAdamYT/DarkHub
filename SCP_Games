local getname = function(str) -- skidded from Adam
    for i,v in next, game:GetService("Players"):GetChildren() do
        if string.find(string.lower(v.Name), string.lower(str)) then
            return v
        end
    end
end
local function Damage(player, value)
    if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool"):FindFirstChild("Receiver") then
    player = getname(player)
    game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Receiver:FireServer("Damage", player.Character.Humanoid, value)
    else
        for _,v in pairs(game:GetService("Workspace").Dekorasi:GetChildren()) do
    if v.Name == "Uniform Giver" then
        if v:FindFirstChild("Coathanger"):FindFirstChild("Pants").PantsTemplate == "http://www.roblox.com/asset/?id=316069126" then
            local lastposition = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v:FindFirstChild("ClickPart").Position+Vector3.new(0,3,0))
            wait(.2)
            fireproximityprompt(v:FindFirstChild("ClickPart"):FindFirstChild("ProximityPrompt"))
            wait(.45)
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(lastposition)
            game.Players.LocalPlayer.Backpack:FindFirstChild("Shotgun").Parent = game.Players.LocalPlayer.Character
            game.StarterGui:SetCore("SendNotification", {Title = "DarkHub Notify";Text = "Re-Input Players Name...";Duration = 2; })
        end
    end
end


    end
end
local settings = {
    WS = false,
    JP = false
}

    local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB",true))() -- UI Lib do not change
    main = lib:Window() -- lets us create a black Window 
    MainWindow = main:Tab('Main') -- make a first Tab1 
    LP = main:Tab('LocalPlayer') -- make a 2nd Tab2

      LP:Toggle('Toggle WalkSpeed', function(state)
            settings.WS = state
        end)
        
        LP:Slider('WalkSpeed Value',16,150,function(num)
            if settings.WS then
                if game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = num
                end
            end
        end)

    
    local SCPNames = {}
    for _,v in pairs(workspace:GetChildren()) do
    if v.ClassName == "Model" then
        if v:FindFirstChild("Active") then
            table.insert(SCPNames, v.Name)
        end
    end
end

    MainWindow:Dropdown("Teleport To SCP's",SCPNames,function(Sele) -- drop down for multiple options that go under the same catagory, ex. Aimbone (Head, UpperTorso, Legs)
       game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(workspace:FindFirstChild(Sele):FindFirstChild("Active").Position)
    end)
       
    MainWindow:Textbox("Kill Player", false, function(Text)
            if Text then
                Damage(Text, 100)
            end
    end)
    
        MainWindow:Textbox("Godmode Player", false, function(Text)
            if Text then
                Damage(Text, 0/0)
            end
    end)

        MainWindow:Button('Godmode', function()
            Damage(game.Players.LocalPlayer.Name, 0/0)
        end)
        

    
