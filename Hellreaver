DarkHub_Client = {SavedSettings = false}
if isfolder and makefolder and not isfolder('DarkHub') then
    makefolder('DarkHub')
    DarkHub_Client.SaveSettings = true
    if isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
        DarkHub_Client.SavedSettings = true
        DarkHub_Client.GameSettings = game:GetService('HttpService'):JSONDecode(readfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB'))
    end
elseif isfolder('DarkHub') then
    DarkHub_Client.SaveSettings = true
    if isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
        DarkHub_Client.SavedSettings = true
        DarkHub_Client.GameSettings = game:GetService('HttpService'):JSONDecode(readfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB'))
    end
else
    DarkHub_Client.SaveSettings = false
end

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB"))()
main = lib:Window()

IsUpToDate = pcall(function()
    Client = {
        Toggles = {
            SilentAim = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.SilentAim or false,
            FOV = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.FOV or false
        },
        Values = {
            FOV = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.FOV or 100
        }
    } 
end)
if not IsUpToDate and DarkHub_Client.SavedSettings and isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
    delfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB')
    game.Players.LocalPlayer:Kick('DarkHub Settings Out Of Date - Issue Fixed | Restart DarkHub to Continue')
end

local FOVCircle = Drawing.new("Circle")
FOVCircle.Thickness = 2
FOVCircle.NumSides = 460
FOVCircle.Filled = false
FOVCircle.Transparency = 0.6
FOVCircle.Radius = Client.Values.FOV
FOVCircle.Color = Color3.new(0,255,0)

local Main = main:Tab("Main")
Main:Toggle('Silent Aim',function(state)
    Client.Toggles.SilentAim = state
end,Client.Toggles.SilentAim)

Main:Toggle('Show FOV',function(state)
    Client.Toggles.FOV = state
end,Client.Toggles.FOV)

Main:Slider('FOV',100,1000,function(num)
    Client.Values.FOV = num
end,Client.Values.FOV)

game:GetService("RunService").Stepped:Connect(function()
    FOVCircle.Radius = Client.Values.FOV
    FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation()
    FOVCircle.Radius = Client.Values.FOV
    if Client.Toggles.FOV == true then
        FOVCircle.Visible = true
    else
        FOVCircle.Visible = false
    end
end)

function GetClosestPlr()
    Plr = nil
    MaxDis = math.huge
    for i,v in pairs(game.Players.GetPlayers(game.Players)) do
        if v ~= game.Players.LocalPlayer and v.TeamColor ~= game.Players.LocalPlayer.TeamColor and v.Character and v.Character.FindFirstChild(v.Character,"Head") and v.Character.FindFirstChild(v.Character,"Head").IsA(v.Character.FindFirstChild(v.Character,"Head"),'Part') then
            local Pos, Vis = game.Workspace.CurrentCamera.WorldToScreenPoint(game.Workspace.CurrentCamera,v.Character.FindFirstChild(v.Character,"Head").Position)
            if Vis then
                mag = (Vector2.new(Pos.X,Pos.Y) - Vector2.new(game.Players.LocalPlayer.GetMouse(game.Players.LocalPlayer).X,game.Players.LocalPlayer.GetMouse(game.Players.LocalPlayer).Y)).magnitude
                if mag < MaxDis and mag <= Client.Values.FOV then
                    Plr = v
                    MaxDis = mag
                end
            end
        end
    end
    return Plr
end
local GameMT = getrawmetatable(game)
local OldNC = GameMT.__namecall
setreadonly(GameMT, false)
GameMT.__namecall = newcclosure(function(self, ...)
    if Client.Toggles.SilentAim and tostring(getnamecallmethod()) == 'FindPartOnRayWithIgnoreList' and getfenv(2).script.Name == '_client' then
        local Args = {...}
        if GetClosestPlr() ~= nil then
            return OldNC(self,Ray.new(game.Workspace.CurrentCamera.CFrame.p,CFrame.new(game.Workspace.CurrentCamera.CFrame.p,GetClosestPlr().Character.Head.Position).LookVector.Unit * 999),Args[2])
        end
    end
    return OldNC(self, ...)
end)
setreadonly(GameMT, true)

while true do wait(5)
    if DarkHub_Client.SaveSettings then
        writefile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB',game:GetService('HttpService'):JSONEncode({['Toggles'] = Client.Toggles,['Values'] = Client.Values}))    
    end
end
