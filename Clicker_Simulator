        -- // Config / Localize
        
        local settings = {
            autoclicker = false, -- As fast as the paid autoclicker
            darkhubclicker = false, -- // This basically goes a little slower than the normal auto-clicker but you get wayy more
            doublejump = false,
            clickdelay = 0
        }

        -- // Library 
        
        local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
        local Window = Lib:Window()
        local Main = Window:Tab('Main')
        local tps = Window:Tab('Teleports')
        local Farming = Window:Tab('Autofarm')
        
        -- // Main Features 
        
        Main:Toggle('Semi-Inf Double Jumps',function(state)
           settings.doublejump = state
        end)
        
        -- // Farming

        Farming:Slider('Click Delay (seconds)', 0, 5, function(num)
    	    settings.clickdelay = num
        end)
        Farming:Toggle('Auto-Clicker',function(state)
           settings.autoclicker = state
        end)
        
        Farming:Toggle('2x Auto-Clicker',function(state)
            settings.darkhubclicker = state
        end)
        
    
        -- // Script Source
        
        local IslandNames = {}
        for _,v in pairs(game:GetService("Workspace").Zones:GetChildren()) do
            table.insert(IslandNames, v.Name)
        end
        
        tps:Dropdown(
        "Teleport To Island",IslandNames, function(selected)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Zones[selected].Island.Detector.Position)

        end)
        
        spawn(function() -- Semi-Inf doubleJumping
            print('Loaded doubleJumping')
            while task.wait(.50) do
                if settings.doublejump then
                    game:GetService("Players").LocalPlayer.PlayerScripts.Client.Main.doubleJumping.Disabled = true
                    wait(.23)
                    game:GetService("Players").LocalPlayer.PlayerScripts.Client.Main.doubleJumping.Disabled = false
                end
            end
        end)
        
        spawn(function() -- Game Auto-Clicker
            print('Loaded Auto-Clicker')
            while task.wait(settings.clickdelay) do
                if settings.autoclicker then
                    getsenv(game:GetService("Players").LocalPlayer.PlayerGui.mainUI.LocalScript).autoClickerActivate(1, true)
                end
            end
        end)
        
        spawn(function() -- darkhubclicker
            print('Loaded darkhubclicker')
            while task.wait(.50) do
                if settings.darkhubclicker then
                    game:GetService("ReplicatedStorage").Events.Client.emitClicks:FireServer()
                    game:GetService("ReplicatedStorage").Clickerr:InvokeServer({
                    	["manual"] = {
                    				["10.15e20"] = 64 -- Multiplier : Amount
                    	}
                    })
                end
            end
        end)
