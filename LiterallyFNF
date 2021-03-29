Client = {
    Toggles = {
        AutoPlayer = false
    }
}

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))();main = lib:Window();
MainW = main:Tab('AutoFarm')
MainW:Toggle('Auto Play',function(state)
    Client.Toggles.AutoPlayer = state
end)

local IncomingArrows = game:GetService("Players").LocalPlayer.PlayerGui.FNF.LocalScript.Parent.Screen.UI.Arrows.IncomingArrows;
local getnearestarrow = getsenv(game:GetService("Players").LocalPlayer.PlayerGui.FNF.LocalScript).getnearestarrow
game:GetService('RunService').RenderStepped:Connect(function()
    if Client.Toggles.AutoPlayer then
        if getnearestarrow("Left", IncomingArrows:GetChildren(), IncomingArrows) ~= nil then
            local Arrow = getnearestarrow("Left", IncomingArrows:GetChildren(), IncomingArrows):FindFirstChildWhichIsA("Frame")
            if Arrow.Sus.Size.Y.Scale > 0 then
                if IncomingArrows.Parent.Left.AbsolutePosition.Y - Arrow:FindFirstChild('Sus').End.AbsolutePosition.Y > -40 then
                    game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.A, false,nil)
                else
                    game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.A, false,nil)
                end
                return    
            end
            if IncomingArrows.Parent.Left.AbsolutePosition.Y - Arrow:FindFirstChildWhichIsA('ImageLabel').AbsolutePosition.Y > -5 then
                game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.A, false,nil)
                game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.A, false,nil)
            end
        end
        if getnearestarrow("Up", IncomingArrows:GetChildren(), IncomingArrows) ~= nil then
            local Arrow = getnearestarrow("Up", IncomingArrows:GetChildren(), IncomingArrows):FindFirstChildWhichIsA("Frame")
            if Arrow.Sus.Size.Y.Scale > 0 then
                if IncomingArrows.Parent.Up.AbsolutePosition.Y - Arrow:FindFirstChild('Sus').End.AbsolutePosition.Y > -40 then
                    game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.W, false,nil)
                else
                    game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.W, false,nil)
                end
                return    
            end
            if IncomingArrows.Parent.Up.AbsolutePosition.Y - Arrow:FindFirstChildWhichIsA('ImageLabel').AbsolutePosition.Y > -5 then
                game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.W, false,nil)
                game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.W, false,nil)
            end
        end
        if getnearestarrow("Right", IncomingArrows:GetChildren(), IncomingArrows) ~= nil then
            local Arrow = getnearestarrow("Right", IncomingArrows:GetChildren(), IncomingArrows):FindFirstChildWhichIsA("Frame")
            if Arrow.Sus.Size.Y.Scale > 0 then
                if IncomingArrows.Parent.Right.AbsolutePosition.Y - Arrow:FindFirstChild('Sus').End.AbsolutePosition.Y > -40 then
                    game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.D, false,nil)
                else
                    game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.D, false,nil)
                end
                return    
            end
            if IncomingArrows.Parent.Right.AbsolutePosition.Y - Arrow:FindFirstChildWhichIsA('ImageLabel').AbsolutePosition.Y > -5 then
                game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.D, false,nil)
                game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.D, false,nil)
            end
        end
        if getnearestarrow("Down", IncomingArrows:GetChildren(), IncomingArrows) ~= nil then
            local Arrow = getnearestarrow("Down", IncomingArrows:GetChildren(), IncomingArrows):FindFirstChildWhichIsA("Frame")
            if Arrow.Sus.Size.Y.Scale > 0 then
                if IncomingArrows.Parent.Down.AbsolutePosition.Y - Arrow:FindFirstChild('Sus').End.AbsolutePosition.Y > -40 then
                    game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.S, false,nil)
                else
                    game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.S, false,nil)
                end
                return    
            end
            if IncomingArrows.Parent.Down.AbsolutePosition.Y - Arrow:FindFirstChildWhichIsA('ImageLabel').AbsolutePosition.Y > -5 then
                game:GetService('VirtualInputManager'):SendKeyEvent(true, Enum.KeyCode.S, false,nil)
                game:GetService('VirtualInputManager'):SendKeyEvent(false, Enum.KeyCode.S, false,nil)
            end
        end
    end
end)
