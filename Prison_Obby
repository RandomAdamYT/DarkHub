local Settings = {
    Aimbot = false,
    Smoothness = 50,
    TeamCheck = false,
    FovUsed = false,
    Fov = 100,
    Boxes = false,
    Names = false,
    Walkspeed = 16,
    Jumppower = 50,
    CtrlClickTP = false
}
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local Camera = game:GetService("Workspace").CurrentCamera
local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local Mouse = Player:GetMouse()

local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
local Window = Lib:Window()
local obby = Window:Tab('Prison Obby')
local Main = Window:Tab('Main')
local Char = Window:Tab('Character')

local Circle = Drawing.new("Circle")
Circle.Color = Color3.new(1, 1, 1)
Circle.Thickness = 1
Circle.Radius = Settings.Fov
Circle.Visible = Settings.FovUsed
Circle.NumSides = 1000
Circle.Filled = false
Circle.Transparency = 1

obby:Button('Free Skip Stages (Once pressed, press button to right of screen)',function()
game:GetService("Players").LocalPlayer.PlayerGui.Shop.SkipStage.Script.Disabled = true
game:GetService("Players").LocalPlayer.PlayerGui.Shop.SkipStage.MouseButton1Click:Connect(function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Stages[game:GetService("Players").LocalPlayer.leaderstats.Stage.Value + 1].Position + Vector3.new(0,2,0))
end)
end)
    
obby:Button('Get All Shop Items (CS)',function()
for _,v in pairs(game:GetService("ReplicatedStorage").Tools:GetChildren()) do
    v:Clone().Parent = game.Players.LocalPlayer.Backpack
end
end)

obby:Button('Obtain Secret Badges',function()
for _,v in pairs(game:GetService("Workspace"):GetChildren()) do
    if v.Name == "BadgeAwarder" then
        firetouchinterest(v:FindFirstChild("Platform"), game.Players.LocalPlayer.Character.HumanoidRootPart,0)
            wait()
        firetouchinterest(v:FindFirstChild("Platform"), game.Players.LocalPlayer.Character.HumanoidRootPart,1)
    end
end
end)


obby:Button('Trigger Pennywise',function()

button = true;
local Penny = game.Workspace.ClownJumpscare.Pennywise;
	if button then
		button = false;
		print("clownJumpscare");
		game:GetService("Players").LocalPlayer.PlayerGui.ClownJumpscare.ClownJumpscare.HiyaGeorgie:Play();
		game:GetService("Players").LocalPlayer.PlayerGui.ClownJumpscare.ClownJumpscare.Pop:Play();
		for v1 = 0, 4 do
			Penny:SetPrimaryPartCFrame(Penny:GetPrimaryPartCFrame() + Vector3.new(0, 0, -0.6));
			wait();
		end;
		print("hi");
		wait(3);
		game:GetService("Players").LocalPlayer.PlayerGui.ClownJumpscare.ClownJumpscare.concrete:Play();
		Penny.MeshPart.FunnelSmoke.Enabled = true;
		for v2 = 0, 60 do
			Penny:SetPrimaryPartCFrame(Penny:GetPrimaryPartCFrame() + Vector3.new(0, 0, 0.045));
			wait();
		end;
		print("end");
		wait(0.1);
		game:GetService("Players").LocalPlayer.PlayerGui.ClownJumpscare.ClownJumpscare.concrete:Stop();
		Penny.MeshPart.FunnelSmoke.Enabled = false;
	end;
end)

obby:Button('Developer Ending (Play game normally, but parts changed)',function()

local l__trigfake__1 = game:GetService("ReplicatedStorage"):WaitForChild("trigfake");
while wait(0.001) do
		print("run");
		script.Parent = game.Players.LocalPlayer.Character;
		game:GetService("StarterGui"):SetCoreGuiEnabled(Enum.CoreGuiType.PlayerList, false);
		print("switch successful");
		if game.Players.LocalPlayer.Character:FindFirstChild("ShopCharacterScripts") then
			game.Players.LocalPlayer.Character.ShopCharacterScripts:Destroy();
			l__trigfake__1:FireServer();
			game.Workspace.YourCamera:Destroy();
			game.Workspace.PServ:Destroy();
			game.Workspace.KeycardScene.keycard.BillboardGui.Frame.ImageLabel.Image = "rbxassetid://917186753";
			game.Players.LocalPlayer.PlayerGui.AngryCutscene.AngryGuyCutscene.Parent = game.Lighting;
			game.ReplicatedStorage.AngryGuyCutscene.Parent = game.Players.LocalPlayer.PlayerGui.AngryCutscene;
			print("gone");
		else
			print("complete");
		end;
end;
end)

Main:Toggle('Aimbot', function(Bool)
    Settings.Aimbot = Bool
end)

Main:Slider('Smoothness', 1, 250, function(Number)
    Settings.Smoothness = Number
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


Char:Slider('Walk Speed', 16, 100, function(Number)
    Settings.Walkspeed = Number
    if Player.Character ~= nil and Player.Character:FindFirstChild("Humanoid") then
        Player.Character.Humanoid.WalkSpeed = Number
    end
end)

Char:Slider('Jump Power', 50, 250, function(Number)
    Settings.Jumppower = Number
    if Player.Character ~= nil and Player.Character:FindFirstChild("Humanoid") then
        Player.Character.Humanoid.JumpPower = Number
    end
end)

Char:Toggle('Ctrl Click TP', function(Bool)
    Settings.CtrlClickTP = Bool
end)

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
    local TopY = math.huge
    local BottomY = -math.huge
    local RightX = -math.huge
    local LeftX = math.huge
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
    local Closest = nil
    local Magnitude = math.huge
    for i, v in next, Players:GetPlayers() do 
        if v ~= Player and IsPlayerAlive(v) then 
            if not Settings.TeamCheck or Settings.TeamCheck and v.Team ~= LocalPlayer.Team then
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
    end
    return Closest 
end

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
                Name.Text = player.Name
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

Mouse.Button1Down:Connect(function()
    if Settings.CtrlClickTP and Player.Character ~= nil then
        if UserInputService:IsKeyDown(Enum.KeyCode.LeftControl) or UserInputService:IsKeyDown(Enum.KeyCode.RightControl) then
            Player.Character:MoveTo(Mouse.Hit.Position)
        end
    end
end)

RunService.RenderStepped:Connect(function()
    local Mouse = UserInputService:GetMouseLocation()
    Circle.Position = Vector2.new(Mouse.X, Mouse.Y)
end)

while wait(0.05) do
    if Settings.Aimbot and UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton2) then
        local Target = GetClosest()
        if Target ~= nil then
            local Position = Camera:WorldToViewportPoint(Target.Character.Head.Position)
            local Mouse = UserInputService:GetMouseLocation()
            mousemoverel((Position.X - Mouse.X) / (Settings.Smoothness / 10), (Position.Y - Mouse.Y) / (Settings.Smoothness / 10))
        end
    end
end
