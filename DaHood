
        local Settings = {
            Silent = false,
            FovUsed = false,
            Fov = 100,
            Boxes = false,
            Names = false
        }
        local Locations = {
            ["Tyrones Guns"] = Vector3.new(481.709137, 48.0050011, -607.184204),
            ["Tyrones Guns 2"] = Vector3.new(-565.284302, 7.99984598, -737.196106),
            ["Hood Fitness"] = Vector3.new(-73.8321609, 21.755003, -589.94519),
            ["Hood Kicks"] = Vector3.new(-191.520126, 21.755003, -410.607056),
            ["Da Furniture"] = Vector3.new(-490.54541, 21.75, -125.106834),
            ["Da Casino"] = Vector3.new(-903.9823, 21.75, -167.42247),
            ["Da Bank"] = Vector3.new(-422.269836, 22.6496277, -284.017639),
            ["Hospital"] = Vector3.new(85.076828, 21.755003, -486.052185),
            ["Police Station"] = Vector3.new(-268.431824, 21.2549973, -132.52446),
            ["Gas Station"] = Vector3.new(568.421204, 49.0000458, -257.565735),
            ["Klips"] = Vector3.new(13.4705801, 21.75, -117.35498),
        }
        local RunService = game:GetService("RunService")
        local UserInputService = game:GetService("UserInputService")
        local Camera = game:GetService("Workspace").CurrentCamera
        local Players = game:GetService("Players")
        local Player = Players.LocalPlayer
        local Mouse = Player:GetMouse()
        local Metatable = getrawmetatable(game)
        local Index = Metatable.__index
        local Target = nil
        Client = {
            Toggles = {
                CashRegFarm = false,
                AutoFarm = false,
                CashDropRegFarm = false,
                WalkSpeed = false
            },
            Values = {
                Walkspeed = 16
            }
        }
        function GetCombat()
            if game.Players.LocalPlayer.Character:FindFirstChild('Combat') then
                return game.Players.LocalPlayer.Character:FindFirstChild('Combat')
            elseif game.Players.LocalPlayer.Backpack:FindFirstChild('Combat') then
                game.Players.LocalPlayer.Character.Humanoid:EquipTool(game.Players.LocalPlayer.Backpack:FindFirstChild('Combat'))
                return game.Players.LocalPlayer.Character:FindFirstChild('Combat')
            else
                return nil
            end
        end
        function GrabCash()
            for i,v in pairs(game:GetService("Workspace").Ignored.Drop:GetChildren()) do
                if v.Name == 'MoneyDrop' and game.Players.LocalPlayer.Character:FindFirstChild('HumanoidRootPart') and (v.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude < 15 then
                    fireclickdetector(v.ClickDetector)
                    wait(.3)
                end
            end    
        end
        function GetCash()
            for i,v in pairs(game:GetService("Workspace").Ignored.Drop:GetChildren()) do
                if v.Name == 'MoneyDrop' and game.Players.LocalPlayer.Character:FindFirstChild('HumanoidRootPart') and (v.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude < 15 then
                    return v
                end
            end
            return nil
        end
        function GetCashRegister()
            for i,v in pairs(game:GetService("Workspace").Cashiers:GetChildren()) do
                if v:FindFirstChild("Humanoid") and v:FindFirstChild('Head') and v.Humanoid.Health > 0 and v:FindFirstChild('Open') then
                    return v
                end
            end
        end
        function GetShoes()
            for i,v in pairs(game:GetService("Workspace").Ignored.Drop:GetChildren()) do
                if v.Name == 'MeshPart' and v:FindFirstChild('ClickDetector') then
                    if game.Players.LocalPlayer.Character:FindFirstChild('HumanoidRootPart') then
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(v.CFrame.p + Vector3.new(0,2,0))) 
                        wait(.4)
                        fireclickdetector(v.ClickDetector)
                    end
                end
            end
            if game.Players.LocalPlayer.Character:FindFirstChild('HumanoidRootPart') and game.Players.LocalPlayer.Character.BodyEffects.ShoesCollect.Value ~= 0 then
                game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(game:GetService("Workspace").Ignored["Clean the shoes on the floor and come to me for cash"].HumanoidRootPart.CFrame.p + Vector3.new(2,2,0))) 
                wait(.2)
                fireclickdetector(game:GetService("Workspace").Ignored["Clean the shoes on the floor and come to me for cash"].ClickDetector)
            end
        end
        local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
        local Window = Lib:Window()
        local Main = Window:Tab('Main')
        local Tps = Window:Tab('Teleports')
        local Farming = Window:Tab('Autofarm')
        Farming:Toggle('AutoFarm',function(state)
            Client.Toggles.AutoFarm = state
        end)
        Farming:Label('Options')
        Farming:Toggle('Farm Shoes When No Cash Registers',function(state)
            Client.Toggles.CashRegFarm = state
        end)
        Farming:Toggle('Farm Medical Job When No Registers',function(state)
            Client.Toggles.CashDropRegFarm = state
        end)


        Main:Button('God Block',function(state)
            game.Players.LocalPlayer.Character.BodyEffects.Defense.CurrentTimeBlock:Destroy()
            game.Players.LocalPlayer.Character.BodyEffects.Defense:Destroy()
        end)
        Main:Toggle('WalkSpeed',function(state)
            Client.Toggles.WalkSpeed = state
            if game.Players.LocalPlayer.Character:FindFirstChild('Animate') then
                getsenv(game.Players.LocalPlayer.Character.Animate).checkingSPEED = function() return nil end
            end
            if Client.Toggles.WalkSpeed == true then
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Client.Values.WalkSpeed
            else
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
            end
        end)
        Main:Slider('WalkSpeed Value',10,150,function(num)
            Client.Values.WalkSpeed = num
            if Client.Toggles.WalkSpeed == true then
                if game.Players.LocalPlayer.Character:FindFirstChild('Animate') then
                    getsenv(game.Players.LocalPlayer.Character.Animate).checkingSPEED = function() return nil end
                end
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Client.Values.WalkSpeed
            end
        end)
        Main:Toggle('Inf Jump',function(state)
            Client.Toggles.InfJump = state
        end)
        Main:Toggle('No Clip',function(state)
            Client.Toggles.NoClip = state
        end)
        game:GetService("RunService").Stepped:Connect(function()
            if Client.Toggles.NoClip then
                for i, v in ipairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
                    if v:IsA("BasePart")then
                        v.CanCollide = false
                    end
                end
            end
        end)
        game.Players.LocalPlayer.Character.Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
            if game.Players.LocalPlayer.Character:FindFirstChild('Animate') then
                getsenv(game.Players.LocalPlayer.Character.Animate).checkingSPEED = function() return nil end
            end
            if Client.Toggles.WalkSpeed == true then
                game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Client.Values.WalkSpeed
            end
        end)
        game.Players.LocalPlayer.CharacterAdded:Connect(function(Char)
            repeat wait() until Char:FindFirstChild('Humanoid')
            Char.Humanoid.WalkSpeed = 17
            Char.Humanoid.JumpPower = 51
            Char.Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
                if game.Players.LocalPlayer.Character:FindFirstChild('Animate') then
                    getsenv(game.Players.LocalPlayer.Character.Animate).checkingSPEED = function() return nil end
                end
                if Client.Toggles.WalkSpeed == true then
                    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Client.Values.WalkSpeed
                end
            end)
            Char.Humanoid:GetPropertyChangedSignal("JumpPower"):Connect(function()
                if Client.Toggles.JumpPower == true then
                    game.Players.LocalPlayer.Character.Humanoid.JumpPower = Client.Values.JumpPower
                end
            end)
        end)        
        game:GetService("UserInputService").JumpRequest:connect(function()
            if Client.Toggles.InfJump then
                game:GetService"Players".LocalPlayer.Character:FindFirstChildOfClass'Humanoid':ChangeState("Jumping")
            end
        end)
        local Circle = Drawing.new("Circle")
        Circle.Color = Color3.new(1, 1, 1)
        Circle.Thickness = 1
        Circle.Radius = Settings.Fov
        Circle.Visible = Settings.FovUsed
        Circle.NumSides = 1000
        Circle.Filled = false
        Circle.Transparency = 1
        
        Main:Toggle('Silent Aim', function(Bool)
            Settings.Silent = Bool
        end)
        
        Main:Toggle('Use Fov', function(Bool)
            Settings.FovUsed = Bool
            Circle.Visible = Bool
        end)
        
        Main:Slider('Fov', 1, 1000, function(Number)
            Settings.Fov = Number
            Circle.Radius = Number
        end)
        
        Main:Toggle('Box Esp', function(Bool)
            Settings.Boxes = Bool
        end)
        
        Main:Toggle('Name Esp', function(Bool)
            Settings.Names = Bool
        end)
        
        Tps:Textbox("Tp To Player", false, function(Text)
            if Players:FindFirstChild(Text) then
                Player.Character:MoveTo(Players[Text].Character.HumanoidRootPart.Position)
            end
        end)
        
        for i, v in pairs(Locations) do
            Tps:Button(i, function()
                Player.Character:MoveTo(v)
            end)
        end
        
        function DrawText()
            local Text = Drawing.new("Text")
            Text.Color = Color3.fromRGB(190, 190, 0)
            Text.Size = 20
            Text.Outline = true
            Text.Center = true
            
            return Text
        end
        
        function DrawSquare()
            local Box = Drawing.new("Square")
            Box.Color = Color3.fromRGB(190, 190, 0)
            Box.Thickness = 0.5
            Box.Filled = false
            Box.Transparency = 1
            
            return Box
        end
        
        function IsPlayerAlive(player)
            if player.Character ~= nil and player.Character:FindFirstChild("HumanoidRootPart") then
                return true
            end
            
            return false
        end
        
        function GetOffset(part, pos)
            local FarPosition = Camera:WorldToViewportPoint(Vector3.new(part.Position.X, part.Position.Y + (part.Size.Y / 2), part.Position.Z))
            
            return FarPosition.Y - pos.Y
        end
        
        function GetCorners(player)
            local TopY = 69696969
            local BottomY = -69696969
            local RightX = -69696969
            local LeftX = 69696969
            local Offsets
            local Positions = {}
            
            for i, v in next, player.Character:GetChildren() do
                if v.ClassName == "MeshPart" or v.Name == "Head" then
                    local Position, OnScreen = Camera:WorldToViewportPoint(v.Position)
                    Positions[v.Name] = Position
                    Offsets = GetOffset(v, Position)
                    
                    if OnScreen then
                        if Position.Y < TopY then
                            TopY = Position.Y
                        end
                        if Position.Y > BottomY then
                            BottomY = Position.Y
                        end
                        if Position.X < LeftX then
                            LeftX = Position.X
                        end
                        if Position.X > RightX then
                            RightX = Position.X
                        end
                    end
                end
            end
        
            return {TopLeft = Vector2.new(LeftX + Offsets, TopY + Offsets), TopRight = Vector2.new(RightX - Offsets, TopY + Offsets), BottomLeft = Vector2.new(LeftX + Offsets, BottomY - Offsets), BottomRight = Vector2.new(RightX - Offsets, BottomY - Offsets), Positions = Positions}
        end
        
        function GetClosest() 
            local Closest = nil;
            local Magnitude = math.huge
        
            for i, v in next, Players:GetPlayers() do 
                if v ~= Player and v.Character and v.Character:FindFirstChild("HumanoidRootPart") then 
                    local Position, Visible = Camera:WorldToScreenPoint(v.Character["HumanoidRootPart"].Position) 
        
                    if Visible then
                        local Mouse = Player:GetMouse()
                        local Distance = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(Position.X, Position.Y)).Magnitude 
        
                        if not Settings.FovUsed and Distance < Magnitude or Settings.FovUsed and Distance < Magnitude and Distance < Settings.Fov then 
                            Closest = v 
                            Magnitude = Distance
                        end
                    end
                end
            end
        
            return Closest 
        end
        
        setreadonly(Metatable, false)
        
        Metatable.__index = newcclosure(function(self, Property)
            if Settings.Silent and self == Mouse and Property == "Hit" and Target ~= nil then
                
        	    return CFrame.new(Target.Character.Head.Position)
            end
            
            return Index(self, Property)
        end)
        
        setreadonly(Metatable, true)
        
        function AddEsp(player)
            local Box = DrawSquare()
            local Name = DrawText()
          
            RunService.Stepped:Connect(function()
                IsAlive = IsPlayerAlive(player)
                
                if IsAlive and player.Character:FindFirstChild("HumanoidRootPart") then
                    local Corners = GetCorners(player)
                    local Positions = Corners.Positions
                    local xDist = Corners.BottomRight.X - Corners.TopLeft.X
                    local yDist = Corners.BottomRight.Y - Corners.TopLeft.Y
                    local RootPosition, OnScreen = Camera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position)
              
                    if Settings.Boxes then
                        Box.Visible = OnScreen
                        Box.Size = Vector2.new(xDist, yDist)
                        Box.Position = Corners.TopLeft
                    else
                        Box.Visible = false
                    end
                    if Settings.Names then
                        Name.Visible = OnScreen
                        Name.Position = Vector2.new(Corners.BottomRight.X - (xDist / 2), Corners.TopLeft.Y - 45)
                        Name.Text = "[ " .. player.Name .. " ]"
                    else
                        Name.Visible = false
                    end
                else
                    Box.Visible = false
                    Name.Visible = false
                end
            end)
        end
        
        for i, v in pairs(Players:GetPlayers()) do
            if v ~= Player then
                AddEsp(v)
            end
        end
        
        Players.PlayerAdded:Connect(function(player)
            if v ~= Player then
                AddEsp(player)
            end
        end)
        
        RunService.RenderStepped:Connect(function()
            local Mouse = UserInputService:GetMouseLocation()
        
            Circle.Position = Vector2.new(Mouse.X, Mouse.Y)
            Target = GetClosest()
        end)
        while true do wait()
            pcall(function()
                if Client.Toggles.AutoFarm then
                    CurrCash = GetCashRegister()
                    if CurrCash ~= nil then
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CurrCash.Head.CFrame * CFrame.new(.4,0,3))
                        Combat = GetCombat()
                        Combat:Activate()
                        repeat wait(1.2)
                            game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CurrCash.Head.CFrame * CFrame.new(.4,0,3))
                            Combat = GetCombat()
                            Combat:Activate()
                        until CurrCash.Humanoid.Health < 0 or Client.Toggles.AutoFarm == false
                        repeat wait(.1)
                            GrabCash()
                        until GetCash() == nil or Client.Toggles.AutoFarm == false
                    else
                        if Client.Toggles.CashRegFarm == true then
                            GetShoes()
                        end
                        if Client.Toggles.CashDropRegFarm and game:GetService("Workspace").Ignored.HospitalJob:FindFirstChildOfClass('Model') then
                            for i,v in pairs(game:GetService("Workspace").Ignored.HospitalJob:GetChildren()) do
                                if v:IsA('Part') then
                                    if string.match(game:GetService("Workspace").Ignored.HospitalJob:FindFirstChildOfClass('Model').Name,v.Name) then
                                        if game.Players.LocalPlayer.Character:FindFirstChild('HumanoidRootPart') then
                                            game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(v.CFrame * CFrame.new(.2,0,-2))
                                            wait(.5)
                                            fireclickdetector(v.ClickDetector)
                                            wait(.2)
                                            if game:GetService("Workspace").Ignored.HospitalJob:FindFirstChildOfClass('Model') then
                                                fireclickdetector(game:GetService("Workspace").Ignored.HospitalJob:FindFirstChildOfClass('Model').ClickDetector)    
                                            end
                                        end
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        end

