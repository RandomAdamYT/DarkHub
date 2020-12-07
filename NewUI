if game.CoreGui:FindFirstChild("DarkHubLib") then
    game.CoreGui.DarkHubLib:Destroy()
end
game:GetService("UserInputService").InputBegan:connect(
    function(key, gpe)
        if key.KeyCode == Enum.KeyCode.RightControl then
            pcall(
                function()
                    for i, v in pairs(game.CoreGui.DarkHubLib:GetChildren()) do
                        v.Visible = not v.Visible
                    end
                end
            )
        end
    end
)

local DarkLib = {RainbowColorValue = 0, HueSelectionPosition = 0}
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local Mouse = LocalPlayer:GetMouse()

coroutine.wrap(
	function()
		while wait() do
			DarkLib.RainbowColorValue = DarkLib.RainbowColorValue + 1 / 255
			DarkLib.HueSelectionPosition = DarkLib.HueSelectionPosition + 1

			if DarkLib.RainbowColorValue >= 1 then
				DarkLib.RainbowColorValue = 0
			end

			if DarkLib.HueSelectionPosition == 93 then
				DarkLib.HueSelectionPosition = 0
			end
		end
	end
)()

local function MakeDraggable(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil

	local function Update(input)
		local Delta = input.Position - DragStart
		local pos =
			UDim2.new(
				StartPosition.X.Scale,
				StartPosition.X.Offset + Delta.X,
				StartPosition.Y.Scale,
				StartPosition.Y.Offset + Delta.Y
			)
		local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})
		Tween:Play()
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if
				input.UserInputType == Enum.UserInputType.MouseMovement or
					input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = input
			end
		end
	)

	UserInputService.InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end

function Ripple(obj)
	spawn(
		function()
			local Mouse = game.Players.LocalPlayer:GetMouse()
			local Circle = Instance.new("ImageLabel")
			Circle.Name = "Circle"
			Circle.Parent = obj
			Circle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Circle.BackgroundTransparency = 1.000
			Circle.ZIndex = 10
			Circle.Image = "rbxassetid://266543268"
			Circle.ImageColor3 = Color3.fromRGB(211, 211, 211)
			Circle.ImageTransparency = 0.6
			local NewX, NewY = Mouse.X - Circle.AbsolutePosition.X, Mouse.Y - Circle.AbsolutePosition.Y
			Circle.Position = UDim2.new(0, NewX, 0, NewY)
			local Size = 0
			if obj.AbsoluteSize.X > obj.AbsoluteSize.Y then
				Size = obj.AbsoluteSize.X * 1
			elseif obj.AbsoluteSize.X < obj.AbsoluteSize.Y then
				Size = obj.AbsoluteSize.Y * 1
			elseif obj.AbsoluteSize.X == obj.AbsoluteSize.Y then
				Size = obj.AbsoluteSize.X * 1
			end
			Circle:TweenSizeAndPosition(
				UDim2.new(0, Size, 0, Size),
				UDim2.new(0.5, -Size / 2, 0.5, -Size / 2),
				"Out",
				"Quad",
				0.2,
				false
			)
			for i = 1, 15 do
				Circle.ImageTransparency = Circle.ImageTransparency + 0.05
				wait()
			end
			Circle:Destroy()
		end
	)
end

local DarkHubLib = Instance.new("ScreenGui")
DarkHubLib.Name = "DarkHubLib"
DarkHubLib.Parent = game.CoreGui
DarkHubLib.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

function DarkLib:Window()
	local firsttab = false
	local MainFrame = Instance.new("Frame")
	local MainFrameUICorner = Instance.new("UICorner")
	local Title = Instance.new("TextLabel")
	local Containers = Instance.new("Folder")
	local DraggableFrame = Instance.new("Frame")
	local TabHolderFrame = Instance.new("Frame")
	local TabHolderFrameUICorner = Instance.new("UICorner")
	local Glow_2 = Instance.new("ImageLabel")
	local TabHolder = Instance.new("Frame")
	local TabHolderUIList = Instance.new("UIListLayout")
	local TabHolderPadding = Instance.new("UIPadding")
	local Glow_3 = Instance.new("ImageLabel")

	MainFrame.Name = "MainFrame"
	MainFrame.Parent = DarkHubLib
	MainFrame.BackgroundColor3 = Color3.fromRGB(29, 29, 29)
	MainFrame.Position = UDim2.new(0.330445558, 0, 0.330043852, 0)
	MainFrame.Size = UDim2.new(0, 547, 0, 341)

	MainFrameUICorner.CornerRadius = UDim.new(0, 11)
	MainFrameUICorner.Name = "MainFrameUICorner"
	MainFrameUICorner.Parent = MainFrame

	Title.Name = "Title"
	Title.Parent = MainFrame
	Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Title.BackgroundTransparency = 1.000
	Title.Position = UDim2.new(0.42778793, 0, 0.041837737, 0)
	Title.Size = UDim2.new(0, 78, 0, 30)
	Title.Font = Enum.Font.Gotham
	Title.Text = "Dark Hub"
	Title.TextColor3 = Color3.fromRGB(168, 168, 168)
	Title.TextSize = 20.000

	Containers.Name = "Containers"
	Containers.Parent = MainFrame

	TabHolderFrame.Name = "TabHolderFrame"
	TabHolderFrame.Parent = MainFrame
	TabHolderFrame.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
	TabHolderFrame.Position = UDim2.new(0.0251439176, 0, 0.174975574, 0)
	TabHolderFrame.Size = UDim2.new(0, 519, 0, 31)

	TabHolderFrameUICorner.CornerRadius = UDim.new(0, 11)
	TabHolderFrameUICorner.Name = "TabHolderFrameUICorner"
	TabHolderFrameUICorner.Parent = TabHolderFrame

	Glow_2.Name = "Glow"
	Glow_2.Parent = TabHolderFrame
	Glow_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Glow_2.BackgroundTransparency = 1.000
	Glow_2.BorderSizePixel = 0
	Glow_2.Position = UDim2.new(0, -15, 0, -15)
	Glow_2.Size = UDim2.new(1, 30, 1, 30)
	Glow_2.ZIndex = 0
	Glow_2.Image = "rbxassetid://4996891970"
	Glow_2.ImageColor3 = Color3.fromRGB(15, 15, 15)
	Glow_2.ScaleType = Enum.ScaleType.Slice
	Glow_2.SliceCenter = Rect.new(20, 20, 280, 280)
	Glow_2.ImageTransparency = 1
	TabHolder.Name = "TabHolder"
	TabHolder.Parent = TabHolderFrame
	TabHolder.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
	TabHolder.BackgroundTransparency = 1.000
	TabHolder.Size = UDim2.new(0, 519, 0, 30)

	TabHolderUIList.Name = "TabHolderUIList"
	TabHolderUIList.Parent = TabHolder
	TabHolderUIList.FillDirection = Enum.FillDirection.Horizontal
	TabHolderUIList.SortOrder = Enum.SortOrder.LayoutOrder

	TabHolderPadding.Name = "TabHolderPadding"
	TabHolderPadding.Parent = TabHolder
	TabHolderPadding.PaddingLeft = UDim.new(0, 4)
	TabHolderPadding.PaddingTop = UDim.new(0, 4)

	Glow_3.Name = "Glow"
	Glow_3.Parent = MainFrame
	Glow_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Glow_3.BackgroundTransparency = 1.000
	Glow_3.BorderSizePixel = 0
	Glow_3.Position = UDim2.new(0, -15, 0, -15)
	Glow_3.Size = UDim2.new(1, 30, 1, 30)
	Glow_3.ZIndex = 0
	Glow_3.Image = "rbxassetid://4996891970"
	Glow_3.ImageColor3 = Color3.fromRGB(15, 15, 15)
	Glow_3.ScaleType = Enum.ScaleType.Slice
	Glow_3.SliceCenter = Rect.new(20, 20, 280, 280)
    Glow_3.ImageTransparency = 1
	DraggableFrame.Parent = MainFrame
	DraggableFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	DraggableFrame.BackgroundTransparency = 1.000
	DraggableFrame.Size = UDim2.new(0, 547, 0, 59)

	MakeDraggable(DraggableFrame, MainFrame)
	local Win = {}
	function Win:Tab(text)
		local Tab = Instance.new("TextButton")
		local Container = Instance.new("Frame")
		local ContainerUICorner = Instance.new("UICorner")
		local ItemHolder = Instance.new("ScrollingFrame")
		local ItemHolderUIList = Instance.new("UIListLayout")
		local Glow = Instance.new("ImageLabel")
		Tab.Name = text .. "Tab"
		Tab.Parent = TabHolder
		Tab.BackgroundColor3 = Color3.fromRGB(168, 168, 168)
		Tab.BackgroundTransparency = 1.000
		Tab.Position = UDim2.new(0, 0, 0.13333334, 0)
		Tab.Size = UDim2.new(0, 48, 0, 24)
		Tab.Font = Enum.Font.Gotham
		Tab.Text = text
		Tab.TextColor3 = Color3.fromRGB(195, 195, 195)
		Tab.TextSize = 14.000
		Tab.Size = UDim2.new(0, Tab.TextBounds.X + 10, 0, 24)
		Tab.TextTransparency = 0.5

		Container.Name = "Container"
		Container.Parent = Containers
		Container.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
		Container.Position = UDim2.new(0.0251439176, 0, 0.28937912, 0)
		Container.Size = UDim2.new(0, 519, 0, 227)
		Container.Visible = false

		ContainerUICorner.CornerRadius = UDim.new(0, 11)
		ContainerUICorner.Name = "ContainerUICorner"
		ContainerUICorner.Parent = Container

		Glow.Name = "Glow"
		Glow.Parent = Container
		Glow.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Glow.BackgroundTransparency = 1.000
		Glow.BorderSizePixel = 0
		Glow.Position = UDim2.new(0, -15, 0, -15)
		Glow.Size = UDim2.new(1, 30, 1, 30)
		Glow.ZIndex = 0
		Glow.Image = "rbxassetid://4996891970"
		Glow.ImageColor3 = Color3.fromRGB(15, 15, 15)
		Glow.ScaleType = Enum.ScaleType.Slice
		Glow.SliceCenter = Rect.new(20, 20, 280, 280)

		ItemHolder.Name = "ItemHolder"
		ItemHolder.Parent = Container
		ItemHolder.Active = true
		ItemHolder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ItemHolder.BackgroundTransparency = 1.000
		ItemHolder.BorderSizePixel = 0
		ItemHolder.Position = UDim2.new(0.0260001533, 0, 0.0586211756, 0)
		ItemHolder.Size = UDim2.new(0, 499, 0, 200)
		ItemHolder.BottomImage = "rbxasset://textures/ui/Scroll/scroll-middle.png"
		ItemHolder.CanvasSize = UDim2.new(0, 0, 0, 0)
		ItemHolder.ScrollBarThickness = 2
		ItemHolder.TopImage = "rbxasset://textures/ui/Scroll/scroll-middle.png"

		ItemHolderUIList.Name = "ItemHolderUIList"
		ItemHolderUIList.Parent = ItemHolder
		ItemHolderUIList.SortOrder = Enum.SortOrder.LayoutOrder
		ItemHolderUIList.Padding = UDim.new(0, 3)

		if firsttab == false then
			firsttab = true
			Container.Visible = true
			Tab.TextTransparency = 0
		end

		Tab.MouseButton1Click:Connect(
			function()
				for i, v in next, Containers:GetChildren() do
					if v.Name == "Container" then
						v.Visible = false
					end
				end

				for i, v in next, TabHolder:GetChildren() do
					if v.ClassName == "TextButton" then
						TweenService:Create(
							v,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{TextTransparency = 0.5}
						):Play()
						TweenService:Create(
							Tab,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{TextTransparency = 0}
						):Play()
					end
				end
				Container.Visible = true
			end
		)

		local Cont = {}
		function Cont:Button(text, callback)
			local Button = Instance.new("TextButton")
			local ButtonUICorner = Instance.new("UICorner")

			Button.Name = "Button"
			Button.Parent = ItemHolder
			Button.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Button.Position = UDim2.new(0, 0, 0.174999997, 0)
			Button.Size = UDim2.new(0, 491, 0, 29)
			Button.AutoButtonColor = false
			Button.Font = Enum.Font.Gotham
			Button.TextColor3 = Color3.fromRGB(195, 195, 195)
			Button.TextSize = 14.000
			Button.Text = text
			Button.ClipsDescendants = true

			ButtonUICorner.CornerRadius = UDim.new(0, 6)
			ButtonUICorner.Name = "ButtonUICorner"
			ButtonUICorner.Parent = Button

			Button.MouseEnter:Connect(
				function()
					TweenService:Create(
						Button,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(44, 44, 44)}
					):Play()
				end
			)

			Button.MouseLeave:Connect(
				function()
					TweenService:Create(
						Button,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(39, 39, 39)}
					):Play()
				end
			)

			Button.MouseButton1Click:Connect(
				function()
					pcall(callback)
					Ripple(Button)
					TweenService:Create(
						Button,
						TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{TextSize = 0}
					):Play()
					wait(.1)
					TweenService:Create(
						Button,
						TweenInfo.new(.1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{TextSize = 14}
					):Play()
				end
			)

			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end

		function Cont:Toggle(text, callback)
			local Toggled = false
			local Toggle = Instance.new("TextButton")
			local ToggleUICorner = Instance.new("UICorner")
			local Title = Instance.new("TextLabel")
			local Status = Instance.new("Frame")
			local StatusUICorner = Instance.new("UICorner")

			Toggle.Name = "Toggle"
			Toggle.Parent = ItemHolder
			Toggle.AnchorPoint = Vector2.new(0.5, 0.5)
			Toggle.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Toggle.Position = UDim2.new(-0.436928689, 0, 0.696994126, 0)
			Toggle.Size = UDim2.new(0, 491, 0, 29)
			Toggle.AutoButtonColor = false
			Toggle.Font = Enum.Font.Gotham
			Toggle.Text = ""
			Toggle.TextColor3 = Color3.fromRGB(195, 195, 195)
			Toggle.TextSize = 14.000
			Toggle.ClipsDescendants = true

			ToggleUICorner.CornerRadius = UDim.new(0, 6)
			ToggleUICorner.Name = "ToggleUICorner"
			ToggleUICorner.Parent = Toggle

			Title.Name = "Title"
			Title.Parent = Toggle
			Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title.BackgroundTransparency = 1.000
			Title.Position = UDim2.new(0.0244399179, 0, 0.068965517, 0)
			Title.Size = UDim2.new(0, 1, 0, 24)
			Title.Font = Enum.Font.Gotham
			Title.TextColor3 = Color3.fromRGB(195, 195, 195)
			Title.TextSize = 14.000
			Title.TextXAlignment = Enum.TextXAlignment.Left
			Title.Text = text

			Status.Name = "Status"
			Status.Parent = Toggle
			Status.BackgroundColor3 = Color3.fromRGB(255, 39, 42)
			Status.Position = UDim2.new(0.947046876, 0, 0.172413796, 0)
			Status.Size = UDim2.new(0, 19, 0, 19)

			StatusUICorner.CornerRadius = UDim.new(0, 6)
			StatusUICorner.Name = "StatusUICorner"
			StatusUICorner.Parent = Status

			Toggle.MouseEnter:Connect(
				function()
					TweenService:Create(
						Toggle,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(44, 44, 44)}
					):Play()
				end
			)

			Toggle.MouseLeave:Connect(
				function()
					TweenService:Create(
						Toggle,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(39, 39, 39)}
					):Play()
				end
			)

			Toggle.MouseButton1Click:Connect(
				function()
					Ripple(Toggle)
					if Toggled == false then
						Toggled = not Toggled
						pcall(callback, Toggled)
						TweenService:Create(
							Status,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Color3.fromRGB(44, 255, 58)}
						):Play()
					else
						Toggled = not Toggled
						pcall(callback, Toggled)
						TweenService:Create(
							Status,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Color3.fromRGB(255, 39, 42)}
						):Play()
					end
				end
			)

			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end

		function Cont:Slider(text, min, max, callback)
			local dragging = false
			local Slider = Instance.new("TextButton")
			local SliderUICorner = Instance.new("UICorner")
			local Title = Instance.new("TextLabel")
			local SlideFrame = Instance.new("Frame")
			local ValueFrame = Instance.new("Frame")
			local ValueUICorner = Instance.new("UICorner")
			local SlideUICorner = Instance.new("UICorner")
			local Value = Instance.new("TextLabel")

			Slider.Name = "Slider"
			Slider.Parent = ItemHolder
			Slider.AnchorPoint = Vector2.new(0.5, 0.5)
			Slider.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Slider.Position = UDim2.new(-0.0217271745, 0, 1.37144423, 0)
			Slider.Size = UDim2.new(0, 491, 0, 37)
			Slider.AutoButtonColor = false
			Slider.Font = Enum.Font.Gotham
			Slider.Text = ""
			Slider.TextColor3 = Color3.fromRGB(195, 195, 195)
			Slider.TextSize = 14.000

			SliderUICorner.CornerRadius = UDim.new(0, 6)
			SliderUICorner.Name = "SliderUICorner"
			SliderUICorner.Parent = Slider

			Title.Name = "Title"
			Title.Parent = Slider
			Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title.BackgroundTransparency = 1.000
			Title.Position = UDim2.new(0.0203665979, 0, 0.150045857, 0)
			Title.Size = UDim2.new(0, 0, 0, 24)
			Title.Font = Enum.Font.Gotham
			Title.TextColor3 = Color3.fromRGB(195, 195, 195)
			Title.TextSize = 14.000
			Title.TextXAlignment = Enum.TextXAlignment.Left
			Title.Text = text

			SlideFrame.Name = "SlideFrame"
			SlideFrame.Parent = Slider
			SlideFrame.AnchorPoint = Vector2.new(1, 0.5)
			SlideFrame.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
			SlideFrame.BorderSizePixel = 0
			SlideFrame.Position = UDim2.new(0.985999942, 0, 0.480000257, 0)
			SlideFrame.Size = UDim2.new(0, 192, 0, 26)

			ValueFrame.Name = "ValueFrame"
			ValueFrame.Parent = SlideFrame
			ValueFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
			ValueFrame.BorderSizePixel = 0
			ValueFrame.Size = UDim2.new(0, 0, 1, 0)

			ValueUICorner.CornerRadius = UDim.new(0, 3)
			ValueUICorner.Name = "ValueUICorner"
			ValueUICorner.Parent = ValueFrame

			SlideUICorner.CornerRadius = UDim.new(0, 3)
			SlideUICorner.Name = "SlideUICorner"
			SlideUICorner.Parent = SlideFrame

			Value.Name = "Value"
			Value.Parent = SlideFrame
			Value.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Value.BackgroundTransparency = 1.000
			Value.BorderSizePixel = 0
			Value.Size = UDim2.new(1, 0, 1, 0)
			Value.Font = Enum.Font.Gotham
			Value.Text = min
			Value.TextColor3 = Color3.fromRGB(195, 195, 195)
			Value.TextSize = 14.000

			local function slide(input)
				local pos =
					UDim2.new(
						math.clamp((input.Position.X - SlideFrame.AbsolutePosition.X) / SlideFrame.AbsoluteSize.X, 0, 1),
						0,
						1,
						0
					)
				ValueFrame:TweenSize(pos, Enum.EasingDirection.Out, Enum.EasingStyle.Quart, 0.3, true)
				local s = math.floor(((pos.X.Scale * max) / max) * (max - min) + min)
				Value.Text = tostring(s)
				pcall(callback, s)
			end

			SlideFrame.InputBegan:Connect(
				function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						slide(input)
						dragging = true
					end
				end
			)

			SlideFrame.InputEnded:Connect(
				function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						dragging = false
					end
				end
			)

			UserInputService.InputChanged:Connect(
				function(input)
					if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
						slide(input)
					end
				end
			)

			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end

		function Cont:Dropdown(text, list, callback)
			local DropToggled = false
			local ItemCount = 0
			local DropdownFrameSize = 0
			local ItemFrameSize = 0
			local Selected = text

			local Dropdown = Instance.new("TextButton")
			local DropdownUICorner = Instance.new("UICorner")
			local Title = Instance.new("TextLabel")
			local DropToggle = Instance.new("ImageButton")

			Dropdown.Name = "Dropdown"
			Dropdown.Parent = ItemHolder
			Dropdown.AnchorPoint = Vector2.new(0.5, 0.5)
			Dropdown.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Dropdown.Position = UDim2.new(-0.436928689, 0, 0.696994126, 0)
			Dropdown.Size = UDim2.new(0, 491, 0, 29)
			Dropdown.AutoButtonColor = false
			Dropdown.Font = Enum.Font.Gotham
			Dropdown.Text = ""
			Dropdown.TextColor3 = Color3.fromRGB(195, 195, 195)
			Dropdown.TextSize = 14.000

			DropdownUICorner.CornerRadius = UDim.new(0, 6)
			DropdownUICorner.Name = "DropdownUICorner"
			DropdownUICorner.Parent = Dropdown

			Title.Name = "Title"
			Title.Parent = Dropdown
			Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title.BackgroundTransparency = 1.000
			Title.Position = UDim2.new(0.0244399179, 0, 0.068965517, 0)
			Title.Size = UDim2.new(0, 1, 0, 24)
			Title.Font = Enum.Font.Gotham
			Title.TextColor3 = Color3.fromRGB(195, 195, 195)
			Title.TextSize = 14.000
			Title.TextXAlignment = Enum.TextXAlignment.Left
			Title.Text = text

			DropToggle.Name = "DropToggle"
			DropToggle.Parent = Dropdown
			DropToggle.BackgroundTransparency = 1.000
			DropToggle.Position = UDim2.new(0.943036616, 0, 0.119965516, 0)
			DropToggle.Size = UDim2.new(0, 20, 0, 20)
			DropToggle.ZIndex = 2
			DropToggle.Image = "rbxassetid://3926307971"
			DropToggle.ImageColor3 = Color3.fromRGB(195, 195, 195)
			DropToggle.ImageRectOffset = Vector2.new(324, 364)
			DropToggle.ImageRectSize = Vector2.new(36, 36)

			local DropdownFrame = Instance.new("Frame")
			local DropdownFrameUICorner = Instance.new("UICorner")
			local DropItemHolder = Instance.new("ScrollingFrame")
			local DropItemHolderUIList = Instance.new("UIListLayout")

			DropdownFrame.Name = "DropdownFrame"
			DropdownFrame.Parent = ItemHolder
			DropdownFrame.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			DropdownFrame.Position = UDim2.new(0, 0, 0.202399909, 0)
			DropdownFrame.Size = UDim2.new(0, 491, 0, 0)
			DropdownFrame.ClipsDescendants = true
			DropdownFrame.Visible = false

			DropdownFrameUICorner.CornerRadius = UDim.new(0, 6)
			DropdownFrameUICorner.Name = "DropdownFrameUICorner"
			DropdownFrameUICorner.Parent = DropdownFrame

			DropItemHolder.Name = "DropItemHolder"
			DropItemHolder.Parent = DropdownFrame
			DropItemHolder.Active = true
			DropItemHolder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropItemHolder.BackgroundTransparency = 1.000
			DropItemHolder.BorderSizePixel = 0
			DropItemHolder.Position = UDim2.new(0.0260001067, 0, 0.0687311123, 0)
			DropItemHolder.Size = UDim2.new(0, 470, 0, 0)
			DropItemHolder.BottomImage = "rbxasset://textures/ui/Scroll/scroll-middle.png"
			DropItemHolder.CanvasSize = UDim2.new(0, 0, 0, 0)
			DropItemHolder.ScrollBarThickness = 2
			DropItemHolder.TopImage = "rbxasset://textures/ui/Scroll/scroll-middle.png"

			DropItemHolderUIList.Name = "DropItemHolderUIList"
			DropItemHolderUIList.Parent = DropItemHolder
			DropItemHolderUIList.SortOrder = Enum.SortOrder.LayoutOrder
			DropItemHolderUIList.Padding = UDim.new(0, 3)

			Dropdown.MouseEnter:Connect(
				function()
					TweenService:Create(
						Dropdown,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(44, 44, 44)}
					):Play()
				end
			)

			Dropdown.MouseLeave:Connect(
				function()
					TweenService:Create(
						Dropdown,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(39, 39, 39)}
					):Play()
				end
			)

			Dropdown.MouseButton1Click:Connect(
				function()
					if DropToggled == false then
						DropToggled = not DropToggled
						TweenService:Create(
							Title,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{TextTransparency = 0.5}
						):Play()
						TweenService:Create(
							DropToggle,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Rotation = 360}
						):Play()
						Title.Text = Selected
						DropdownFrame.Visible = true
						DropdownFrame:TweenSize(
							UDim2.new(0, 491, 0, DropdownFrameSize),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						DropItemHolder:TweenSize(
							UDim2.new(0, 470, 0, ItemFrameSize),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						repeat
							wait()
						until DropdownFrame.Size == UDim2.new(0, 491, 0, DropdownFrameSize)
						ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
					else
						DropToggled = not DropToggled
						TweenService:Create(
							Title,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{TextTransparency = 0}
						):Play()
						TweenService:Create(
							DropToggle,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Rotation = 0}
						):Play()
						Title.Text = text
						DropdownFrame:TweenSize(
							UDim2.new(0, 491, 0, 0),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						DropItemHolder:TweenSize(
							UDim2.new(0, 470, 0, 0),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						wait(.05)
						DropdownFrame.Visible = false
						repeat
							wait()
						until DropdownFrame.Size == UDim2.new(0, 491, 0, 0)
						ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
					end
				end
			)

			for i, v in next, list do
				ItemCount = ItemCount + 1
				local Option = Instance.new("TextButton")
				local OptionUICorner = Instance.new("UICorner")

				Option.Name = "Option"
				Option.Parent = DropItemHolder
				Option.AnchorPoint = Vector2.new(0.5, 0.5)
				Option.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
				Option.Position = UDim2.new(0.494680852, 0, 0.147959188, 0)
				Option.Size = UDim2.new(0, 465, 0, 25)
				Option.AutoButtonColor = false
				Option.Font = Enum.Font.Gotham
				Option.TextColor3 = Color3.fromRGB(195, 195, 195)
				Option.TextSize = 14.000
				Option.Text = v

				OptionUICorner.CornerRadius = UDim.new(0, 6)
				OptionUICorner.Name = "ButtonUICorner"
				OptionUICorner.Parent = Option

				if ItemCount <= 3 then
					DropdownFrameSize = DropdownFrameSize + 32
					ItemFrameSize = ItemFrameSize + 27
				elseif ItemCount >= 4 then
					DropItemHolder.CanvasSize = UDim2.new(0, 0, 0, DropItemHolderUIList.AbsoluteContentSize.Y)
				end

				Option.MouseEnter:Connect(
					function()
						TweenService:Create(
							Option,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Color3.fromRGB(44, 44, 44)}
						):Play()
					end
				)

				Option.MouseLeave:Connect(
					function()
						TweenService:Create(
							Option,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Color3.fromRGB(39, 39, 39)}
						):Play()
					end
				)

				Option.MouseButton1Click:Connect(
					function()
						DropToggled = not DropToggled
						TweenService:Create(
							Title,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{TextTransparency = 0}
						):Play()
						TweenService:Create(
							DropToggle,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Rotation = 0}
						):Play()
						Title.Text = text
						Selected = v
						pcall(callback, v)
						DropdownFrame:TweenSize(
							UDim2.new(0, 491, 0, 0),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						DropItemHolder:TweenSize(
							UDim2.new(0, 470, 0, 0),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						wait(.05)
						DropdownFrame.Visible = false
						repeat
							wait()
						until DropdownFrame.Size == UDim2.new(0, 491, 0, 0)
						ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
					end
				)
			end
			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end

		function Cont:Colorpicker(text, preset, callback)
			local ColorPickerToggled = false
			local OldToggleColor = Color3.fromRGB(0, 0, 0)
			local OldColor = Color3.fromRGB(0, 0, 0)
			local OldColorSelectionPosition = nil
			local OldHueSelectionPosition = nil
			local ColorH, ColorS, ColorV = 1, 1, 1
			local RainbowColorPicker = false
			local ColorPickerInput = nil
			local ColorInput = nil
			local HueInput = nil

			local Colorpicker = Instance.new("TextButton")
			local ColorpickerUICorner = Instance.new("UICorner")
			local Title = Instance.new("TextLabel")
			local CurrentColor = Instance.new("Frame")
			local ColorUICorner = Instance.new("UICorner")

			Colorpicker.Name = "Colorpicker"
			Colorpicker.Parent = ItemHolder
			Colorpicker.AnchorPoint = Vector2.new(0.5, 0.5)
			Colorpicker.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Colorpicker.Position = UDim2.new(-0.436928689, 0, 0.696994126, 0)
			Colorpicker.Size = UDim2.new(0, 491, 0, 29)
			Colorpicker.AutoButtonColor = false
			Colorpicker.Font = Enum.Font.Gotham
			Colorpicker.Text = ""
			Colorpicker.TextColor3 = Color3.fromRGB(195, 195, 195)
			Colorpicker.TextSize = 14.000

			ColorpickerUICorner.CornerRadius = UDim.new(0, 6)
			ColorpickerUICorner.Name = "ColorpickerUICorner"
			ColorpickerUICorner.Parent = Colorpicker

			Title.Name = "Title"
			Title.Parent = Colorpicker
			Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title.BackgroundTransparency = 1.000
			Title.Position = UDim2.new(0.0244399179, 0, 0.068965517, 0)
			Title.Size = UDim2.new(0, 1, 0, 24)
			Title.Font = Enum.Font.Gotham
			Title.TextColor3 = Color3.fromRGB(195, 195, 195)
			Title.TextSize = 14.000
			Title.TextXAlignment = Enum.TextXAlignment.Left
			Title.Text = text

			CurrentColor.Name = "CurrentColor"
			CurrentColor.Parent = Colorpicker
			CurrentColor.BackgroundColor3 = preset
			CurrentColor.Position = UDim2.new(0.947046876, 0, 0.172413796, 0)
			CurrentColor.Size = UDim2.new(0, 19, 0, 19)

			ColorUICorner.CornerRadius = UDim.new(0, 6)
			ColorUICorner.Name = "ColorUICorner"
			ColorUICorner.Parent = CurrentColor
			local ColorpickerFrame = Instance.new("Frame")
			local ColorpickerFrameUICorner = Instance.new("UICorner")
			local Hue = Instance.new("ImageLabel")
			local huecorner = Instance.new("UICorner")
			local UIGradient = Instance.new("UIGradient")
			local HueSelection = Instance.new("ImageLabel")
			local Color = Instance.new("ImageLabel")
			local UICorner = Instance.new("UICorner")
			local ColorSelection = Instance.new("ImageLabel")
			local Confirm = Instance.new("TextButton")
			local ButtonUICorner = Instance.new("UICorner")
			local RainbowToggle = Instance.new("TextButton")
			local RainbowToggleUICorner = Instance.new("UICorner")
			local RainbowTitle = Instance.new("TextLabel")
			local RainbowStatus = Instance.new("Frame")
			local RainbowStatusUICorner = Instance.new("UICorner")

			ColorpickerFrame.Name = "ColorpickerFrame"
			ColorpickerFrame.Parent = ItemHolder
			ColorpickerFrame.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			ColorpickerFrame.Position = UDim2.new(0.0457920805, 0, 0.685394764, 0)
			ColorpickerFrame.Size = UDim2.new(0, 491, 0, 0)
			ColorpickerFrame.Visible = false
			ColorpickerFrame.ClipsDescendants = true

			ColorpickerFrameUICorner.CornerRadius = UDim.new(0, 6)
			ColorpickerFrameUICorner.Name = "ColorpickerFrameUICorner"
			ColorpickerFrameUICorner.Parent = ColorpickerFrame

			Hue.Name = "Hue"
			Hue.Parent = ColorpickerFrame
			Hue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Hue.Position = UDim2.new(0, 233, 0, 9)
			Hue.Size = UDim2.new(0, 25, 0, 93)

			huecorner.CornerRadius = UDim.new(0, 3)
			huecorner.Name = "huecorner"
			huecorner.Parent = Hue

			UIGradient.Color =
				ColorSequence.new {
					ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 0, 4)),
					ColorSequenceKeypoint.new(0.20, Color3.fromRGB(234, 255, 0)),
					ColorSequenceKeypoint.new(0.40, Color3.fromRGB(21, 255, 0)),
					ColorSequenceKeypoint.new(0.60, Color3.fromRGB(0, 255, 255)),
					ColorSequenceKeypoint.new(0.80, Color3.fromRGB(0, 17, 255)),
					ColorSequenceKeypoint.new(0.90, Color3.fromRGB(255, 0, 251)),
					ColorSequenceKeypoint.new(1.00, Color3.fromRGB(255, 0, 4))
				}
			UIGradient.Rotation = 270
			UIGradient.Parent = Hue

			HueSelection.Name = "HueSelection"
			HueSelection.Parent = Hue
			HueSelection.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			HueSelection.BackgroundTransparency = 1.000
			HueSelection.Position = UDim2.new(0.48, 0, 1 - select(1, Color3.toHSV(preset)))
			HueSelection.Size = UDim2.new(0, 18, 0, 18)
			HueSelection.Image = "http://www.roblox.com/asset/?id=4805639000"
			HueSelection.AnchorPoint = Vector2.new(0.5, 0.5)

			Color.Name = "Color"
			Color.Parent = ColorpickerFrame
			Color.BackgroundColor3 = preset
			Color.Position = UDim2.new(0, 11, 0, 9)
			Color.Size = UDim2.new(0, 212, 0, 93)
			Color.ZIndex = 10
			Color.Image = "rbxassetid://4155801252"

			UICorner.CornerRadius = UDim.new(0, 3)
			UICorner.Parent = Color

			ColorSelection.Name = "ColorSelection"
			ColorSelection.Parent = Color
			ColorSelection.AnchorPoint = Vector2.new(0.5, 0.5)
			ColorSelection.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			ColorSelection.ZIndex = 25
			ColorSelection.AnchorPoint = Vector2.new(0.5, 0.5)
			ColorSelection.BackgroundTransparency = 1.000
			ColorSelection.Position = UDim2.new(preset and select(3, Color3.toHSV(preset)))
			ColorSelection.Size = UDim2.new(0, 18, 0, 18)
			ColorSelection.Image = "http://www.roblox.com/asset/?id=4805639000"
			ColorSelection.ScaleType = Enum.ScaleType.Fit

			Confirm.Name = "Confirm"
			Confirm.Parent = ColorpickerFrame
			Confirm.AnchorPoint = Vector2.new(0.5, 0.5)
			Confirm.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Confirm.Position = UDim2.new(0.760692477, 0, 0.211035922, 0)
			Confirm.Size = UDim2.new(0, 212, 0, 29)
			Confirm.AutoButtonColor = false
			Confirm.Font = Enum.Font.Gotham
			Confirm.Text = "Confirm"
			Confirm.TextColor3 = Color3.fromRGB(195, 195, 195)
			Confirm.TextSize = 14.000

			ButtonUICorner.CornerRadius = UDim.new(0, 6)
			ButtonUICorner.Name = "ButtonUICorner"
			ButtonUICorner.Parent = Confirm

			RainbowToggle.Name = "RainbowToggle"
			RainbowToggle.Parent = ColorpickerFrame
			RainbowToggle.AnchorPoint = Vector2.new(0.5, 0.5)
			RainbowToggle.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			RainbowToggle.Position = UDim2.new(0.760150731, 0, 0.498795807, 0)
			RainbowToggle.Size = UDim2.new(0, 212, 0, 29)
			RainbowToggle.AutoButtonColor = false
			RainbowToggle.Font = Enum.Font.Gotham
			RainbowToggle.Text = ""
			RainbowToggle.TextColor3 = Color3.fromRGB(195, 195, 195)
			RainbowToggle.TextSize = 14.000

			RainbowToggleUICorner.CornerRadius = UDim.new(0, 6)
			RainbowToggleUICorner.Name = "RainbowToggleUICorner"
			RainbowToggleUICorner.Parent = RainbowToggle

			RainbowTitle.Name = "RainbowTitle"
			RainbowTitle.Parent = RainbowToggle
			RainbowTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			RainbowTitle.BackgroundTransparency = 1.000
			RainbowTitle.Position = UDim2.new(0.0244399179, 0, 0.068965517, 0)
			RainbowTitle.Size = UDim2.new(0, 1, 0, 24)
			RainbowTitle.Font = Enum.Font.Gotham
			RainbowTitle.Text = "Rainbow"
			RainbowTitle.TextColor3 = Color3.fromRGB(195, 195, 195)
			RainbowTitle.TextSize = 14.000
			RainbowTitle.TextXAlignment = Enum.TextXAlignment.Left

			RainbowStatus.Name = "RainbowStatus"
			RainbowStatus.Parent = RainbowToggle
			RainbowStatus.BackgroundColor3 = Color3.fromRGB(255, 39, 42)
			RainbowStatus.Position = UDim2.new(0.909311056, 0, 0.137931034, 0)
			RainbowStatus.Size = UDim2.new(0, 19, 0, 19)

			RainbowStatusUICorner.CornerRadius = UDim.new(0, 6)
			RainbowStatusUICorner.Name = "RainbowStatusUICorner"
			RainbowStatusUICorner.Parent = RainbowStatus

			Colorpicker.MouseEnter:Connect(
				function()
					TweenService:Create(
						Colorpicker,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(44, 44, 44)}
					):Play()
				end
			)

			Colorpicker.MouseLeave:Connect(
				function()
					TweenService:Create(
						Colorpicker,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(39, 39, 39)}
					):Play()
				end
			)

			local function UpdateColorPicker(nope)
				CurrentColor.BackgroundColor3 = Color3.fromHSV(ColorH, ColorS, ColorV)
				Color.BackgroundColor3 = Color3.fromHSV(ColorH, 1, 1)

				pcall(callback, CurrentColor.BackgroundColor3)
			end

			ColorH =
				1 -
				(math.clamp(HueSelection.AbsolutePosition.Y - Hue.AbsolutePosition.Y, 0, Hue.AbsoluteSize.Y) /
					Hue.AbsoluteSize.Y)
			ColorS =
				(math.clamp(ColorSelection.AbsolutePosition.X - Color.AbsolutePosition.X, 0, Color.AbsoluteSize.X) /
					Color.AbsoluteSize.X)
			ColorV =
				1 -
				(math.clamp(ColorSelection.AbsolutePosition.Y - Color.AbsolutePosition.Y, 0, Color.AbsoluteSize.Y) /
					Color.AbsoluteSize.Y)

			CurrentColor.BackgroundColor3 = preset
			Color.BackgroundColor3 = preset
			pcall(callback, CurrentColor.BackgroundColor3)

			Color.InputBegan:Connect(
				function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if RainbowColorPicker then
							return
						end

						if ColorInput then
							ColorInput:Disconnect()
						end

						ColorInput =
							RunService.RenderStepped:Connect(
								function()
								local ColorX =
									(math.clamp(Mouse.X - Color.AbsolutePosition.X, 0, Color.AbsoluteSize.X) /
										Color.AbsoluteSize.X)
								local ColorY =
									(math.clamp(Mouse.Y - Color.AbsolutePosition.Y, 0, Color.AbsoluteSize.Y) /
										Color.AbsoluteSize.Y)

								ColorSelection.Position = UDim2.new(ColorX, 0, ColorY, 0)
								ColorS = ColorX
								ColorV = 1 - ColorY

								UpdateColorPicker(true)
							end
							)
					end
				end
			)

			Color.InputEnded:Connect(
				function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if ColorInput then
							ColorInput:Disconnect()
						end
					end
				end
			)

			Hue.InputBegan:Connect(
				function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if RainbowColorPicker then
							return
						end

						if HueInput then
							HueInput:Disconnect()
						end

						HueInput =
							RunService.RenderStepped:Connect(
								function()
								local HueY =
									(math.clamp(Mouse.Y - Hue.AbsolutePosition.Y, 0, Hue.AbsoluteSize.Y) /
										Hue.AbsoluteSize.Y)

								HueSelection.Position = UDim2.new(0.48, 0, HueY, 0)
								ColorH = 1 - HueY

								UpdateColorPicker(true)
							end
							)
					end
				end
			)

			Hue.InputEnded:Connect(
				function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if HueInput then
							HueInput:Disconnect()
						end
					end
				end
			)

			RainbowToggle.MouseButton1Down:Connect(
				function()
					RainbowColorPicker = not RainbowColorPicker

					if ColorInput then
						ColorInput:Disconnect()
					end

					if HueInput then
						HueInput:Disconnect()
					end

					if RainbowColorPicker then
						TweenService:Create(
							RainbowStatus,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Color3.fromRGB(44, 255, 58)}
						):Play()

						OldToggleColor = CurrentColor.BackgroundColor3
						OldColor = Color.BackgroundColor3
						OldColorSelectionPosition = ColorSelection.Position
						OldHueSelectionPosition = HueSelection.Position

						while RainbowColorPicker do
							CurrentColor.BackgroundColor3 = Color3.fromHSV(DarkLib.RainbowColorValue, 1, 1)
							Color.BackgroundColor3 = Color3.fromHSV(DarkLib.RainbowColorValue, 1, 1)

							ColorSelection.Position = UDim2.new(1, 0, 0, 0)
							HueSelection.Position = UDim2.new(0.48, 0, 0, DarkLib.HueSelectionPosition)

							pcall(callback, CurrentColor.BackgroundColor3)
							wait()
						end
					elseif not RainbowColorPicker then
						TweenService:Create(
							RainbowStatus,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Color3.fromRGB(255, 39, 42)}
						):Play()
						CurrentColor.BackgroundColor3 = OldToggleColor
						Color.BackgroundColor3 = OldColor

						ColorSelection.Position = OldColorSelectionPosition
						HueSelection.Position = OldHueSelectionPosition

						pcall(callback, CurrentColor.BackgroundColor3)
					end
				end
			)

			Colorpicker.MouseButton1Click:Connect(
				function()
					if ColorPickerToggled == false then
						ColorPickerToggled = not ColorPickerToggled
						ColorpickerFrame.Visible = true
						ColorpickerFrame:TweenSize(
							UDim2.new(0, 491, 0, 111),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						repeat
							wait()
						until ColorpickerFrame.Size == UDim2.new(0, 491, 0, 111)
						ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
					else
						ColorPickerToggled = not ColorPickerToggled
						ColorpickerFrame:TweenSize(
							UDim2.new(0, 491, 0, 0),
							Enum.EasingDirection.Out,
							Enum.EasingStyle.Quart,
							0.1,
							true
						)
						wait(.05)
						ColorpickerFrame.Visible = false
						repeat
							wait()
						until ColorpickerFrame.Size == UDim2.new(0, 491, 0, 0)
						ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
					end
				end
			)

			Confirm.MouseButton1Click:Connect(
				function()
					ColorPickerToggled = not ColorPickerToggled
					ColorpickerFrame:TweenSize(
						UDim2.new(0, 491, 0, 0),
						Enum.EasingDirection.Out,
						Enum.EasingStyle.Quart,
						0.1,
						true
					)
					wait(.05)
					ColorpickerFrame.Visible = false
					repeat
						wait()
					until ColorpickerFrame.Size == UDim2.new(0, 491, 0, 0)
					ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
				end
			)
			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end

		function Cont:Textbox(text, disapper, callback)
			local Textbox = Instance.new("TextButton")
			local TextboxUICorner = Instance.new("UICorner")
			local Title = Instance.new("TextLabel")
			local TextBox = Instance.new("TextBox")
			local TextBoxUICorner = Instance.new("UICorner")

			Textbox.Name = "Textbox"
			Textbox.Parent = ItemHolder
			Textbox.AnchorPoint = Vector2.new(0.5, 0.5)
			Textbox.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Textbox.Position = UDim2.new(-0.0217271745, 0, 1.37144423, 0)
			Textbox.Size = UDim2.new(0, 491, 0, 37)
			Textbox.AutoButtonColor = false
			Textbox.Font = Enum.Font.Gotham
			Textbox.Text = ""
			Textbox.TextColor3 = Color3.fromRGB(195, 195, 195)
			Textbox.TextSize = 14.000

			TextboxUICorner.CornerRadius = UDim.new(0, 6)
			TextboxUICorner.Name = "TextboxUICorner"
			TextboxUICorner.Parent = Textbox

			Title.Name = "Title"
			Title.Parent = Textbox
			Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title.BackgroundTransparency = 1.000
			Title.Position = UDim2.new(0.0203665979, 0, 0.150045857, 0)
			Title.Size = UDim2.new(0, 0, 0, 24)
			Title.Font = Enum.Font.Gotham
			Title.TextColor3 = Color3.fromRGB(195, 195, 195)
			Title.TextSize = 14.000
			Title.TextXAlignment = Enum.TextXAlignment.Left
			Title.Text = text

			TextBox.Parent = Textbox
			TextBox.AnchorPoint = Vector2.new(1, 0)
			TextBox.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
			TextBox.Position = UDim2.new(0.985743403, 0, 0.108108111, 0)
			TextBox.Size = UDim2.new(0, 192, 0, 26)
			TextBox.Font = Enum.Font.Gotham
			TextBox.Text = ""
			TextBox.TextColor3 = Color3.fromRGB(195, 195, 195)
			TextBox.TextSize = 14.000

			TextBoxUICorner.CornerRadius = UDim.new(0, 6)
			TextBoxUICorner.Name = "TextBoxUICorner"
			TextBoxUICorner.Parent = TextBox

			TextBox.Focused:Connect(
				function()
					TextBox:TweenSize(
						UDim2.new(0, 240, 0, 26),
						Enum.EasingDirection.Out,
						Enum.EasingStyle.Quart,
						0.1,
						true
					)
				end
			)

			TextBox.FocusLost:Connect(
				function(ep)
					if ep then
						if #TextBox.Text > 0 then
							pcall(callback, TextBox.Text)
							TextBox:TweenSize(
								UDim2.new(0, 192, 0, 26),
								Enum.EasingDirection.Out,
								Enum.EasingStyle.Quart,
								0.1,
								true
							)
							if disapper then
								TextBox.Text = ""
							end
						end
					end
				end
			)
			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end

		function Cont:Keybind(text, key, callback)
			local Key = key.Name

			local Bind = Instance.new("TextButton")
			local BindUICorner = Instance.new("UICorner")
			local Title = Instance.new("TextLabel")
			local BindFrame = Instance.new("Frame")
			local BindFrameUICorner = Instance.new("UICorner")
			local BindLabel = Instance.new("TextLabel")

			Bind.Name = "Bind"
			Bind.Parent = ItemHolder
			Bind.AnchorPoint = Vector2.new(0.5, 0.5)
			Bind.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Bind.Position = UDim2.new(-0.436928689, 0, 0.696994126, 0)
			Bind.Size = UDim2.new(0, 491, 0, 29)
			Bind.AutoButtonColor = false
			Bind.Font = Enum.Font.Gotham
			Bind.Text = ""
			Bind.TextColor3 = Color3.fromRGB(195, 195, 195)
			Bind.TextSize = 14.000

			BindUICorner.CornerRadius = UDim.new(0, 6)
			BindUICorner.Name = "BindUICorner"
			BindUICorner.Parent = Bind

			Title.Name = "Title"
			Title.Parent = Bind
			Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title.BackgroundTransparency = 1.000
			Title.Position = UDim2.new(0.0244399179, 0, 0.068965517, 0)
			Title.Size = UDim2.new(0, 1, 0, 24)
			Title.Font = Enum.Font.Gotham
			Title.TextColor3 = Color3.fromRGB(195, 195, 195)
			Title.TextSize = 14.000
			Title.TextXAlignment = Enum.TextXAlignment.Left
			Title.Text = text

			BindFrame.Name = "BindFrame"
			BindFrame.Parent = Bind
			BindFrame.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
			BindFrame.Position = UDim2.new(0.775967538, 0, 0.172413796, 0)
			BindFrame.Size = UDim2.new(0, 103, 0, 19)

			BindFrameUICorner.CornerRadius = UDim.new(0, 6)
			BindFrameUICorner.Name = "BindFrameUICorner"
			BindFrameUICorner.Parent = BindFrame

			BindLabel.Name = "BindLabel"
			BindLabel.Parent = BindFrame
			BindLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			BindLabel.BackgroundTransparency = 1.000
			BindLabel.Size = UDim2.new(0, 102, 0, 20)
			BindLabel.Font = Enum.Font.Gotham
			BindLabel.Text = Key
			BindLabel.TextColor3 = Color3.fromRGB(195, 195, 195)
			BindLabel.TextSize = 13.000

			Bind.MouseEnter:Connect(
				function()
					TweenService:Create(
						Bind,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(44, 44, 44)}
					):Play()
				end
			)

			Bind.MouseLeave:Connect(
				function()
					TweenService:Create(
						Bind,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(39, 39, 39)}
					):Play()
				end
			)

			Bind.MouseButton1Click:connect(
				function(e)
					BindLabel.Text = "..."
					local a, b = game:GetService("UserInputService").InputBegan:wait()
					if a.KeyCode.Name ~= "Unknown" then
						BindLabel.Text = a.KeyCode.Name
						Key = a.KeyCode.Name
					end
				end
			)

			game:GetService("UserInputService").InputBegan:connect(
			function(current, pressed)
				if not pressed then
					if current.KeyCode.Name == Key then
						pcall(callback)
					end
				end
			end
			)
			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end

		function Cont:Label(text)
			local Label = Instance.new("TextButton")
			local LabelUICorner = Instance.new("UICorner")

			Label.Name = "Label"
			Label.Parent = ItemHolder
			Label.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
			Label.Position = UDim2.new(0, 0, 0.174999997, 0)
			Label.Size = UDim2.new(0, 491, 0, 29)
			Label.AutoButtonColor = false
			Label.Font = Enum.Font.Gotham
			Label.TextColor3 = Color3.fromRGB(195, 195, 195)
			Label.TextSize = 14.000
			Label.Text = text
			Label.ClipsDescendants = true

			LabelUICorner.CornerRadius = UDim.new(0, 6)
			LabelUICorner.Name = "LabelUICorner"
			LabelUICorner.Parent = Label
			ItemHolder.CanvasSize = UDim2.new(0, 0, 0, ItemHolderUIList.AbsoluteContentSize.Y)
		end
		return Cont
	end
	return Win
end
return DarkLib
