local Swag = game:GetService("ReplicatedStorage").Assets.PlayerNameGui:Clone()

Swag.TextLabel.Text = "DarkHub Winning!"
Swag.TextLabel.TextColor3 = Color3.fromRGB(255, 43, 43)
Swag.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
local settings = {
    Takis = false,
    Treat = false,
    Bite = false,
    God = false,
    WS = false,
    Rev = false,
}

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
Mainz = main:Tab('Main')
Combat = main:Tab('Combat')


        Mainz:Toggle('Toggle WalkSpeed', function(state)
            settings.WS = state
        end)
        
        Mainz:Slider('WalkSpeed Value',16,150,function(num)
            if game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") and settings.WS then
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = num    
        end
        end)
        
        Mainz:Toggle('Revive All (SS)', function(state)
            settings.Rev = state
        end)

        Mainz:Toggle('Eat Takis (Spit Fire / Sound Spam) ', function(state)
            settings.Takis = state
        end)
        
        Mainz:Toggle('Collect Treats ', function(state)
            settings.Treat = state
        end)
        
        Combat:Toggle('Godmode', function(state)
            settings.God = state
            end)
        
        Combat:Toggle('Auto-Attack', function(state)
            settings.Bite = state
        end)
        


       
        
        while task.wait() do
            if settings.Takis then
                for i = 1, 100 do
                    game:GetService("ReplicatedStorage").Remotes.BarkEvent:FireServer()
                end
            end
            if settings.Treat then
                game:GetService("ReplicatedStorage").Remotes.TreatTouched:FireServer()
            end
            if settings.Bite then
                game:GetService("ReplicatedStorage").Remotes.BiteEvent:FireServer()
            end
            if settings.God then
                if game:GetService("Players").LocalPlayer.Energy.Value < 100 then
                    repeat wait() game:GetService("ReplicatedStorage").Remotes.HealEvent:FireServer(10) until game:GetService("Players").LocalPlayer.Energy.Value > 99
                end
            end
            if settings.Rev then
                for _,v in pairs(game.Players:GetPlayers()) do
                    game:GetService("ReplicatedStorage").Remotes.reviveFriendEvent:FireServer(v)
                end
            end
        end

