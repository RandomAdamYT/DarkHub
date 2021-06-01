--Created by : Bye...#0001
--Discord.gg/darkhub
--Please give credits if you plan on using anything ;))
Client = {
    Toggles = {
        SilentAim = false,
        NoRecoil = false,
        NoSpread = false,
        InfAmmo = false,
        FOV = false
    },
    Values = {
        FOV = 250
    }
}
for i,v in pairs(getgc(true)) do
    if type(v) == 'table' and rawget(v,'Bullet') and rawget(v,'TouchBullet') then
        Yawninglmao = v
        break
    end
end

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))();main = lib:Window();
CombatW = main:Tab('Combat')
local FOVCircle = Drawing.new("Circle")
FOVCircle.Thickness = 2
FOVCircle.NumSides = 460
FOVCircle.Filled = false
FOVCircle.Transparency = 0.6
FOVCircle.Radius = Client.Values.FOV
FOVCircle.Color = Color3.new(0,255,0)

CombatW:Toggle('Silent Aim',function(state)
    Client.Toggles.SilentAim = state
end)
CombatW:Slider('FOV',100,1000,function(num)
    Client.Values.FOV = num
end)
CombatW:Toggle('Show FOV',function(state)
    Client.Toggles.FOV = state
end)
CombatW:Toggle('No Recoil',function(state)
    Client.Toggles.NoRecoil = state
end)
CombatW:Toggle('No Spread',function(state)
    Client.Toggles.NoSpread = state
end)
CombatW:Toggle('Inf Ammo',function(state)
    Client.Toggles.InfAmmo = state
end)

function GetClosestPlr()
    Plr = nil
    MaxDis = math.huge
    for i,v in pairs(game.Players:GetPlayers()) do
        if v ~= game.Players.LocalPlayer and v.Team ~= game.Players.LocalPlayer.Team and v.Character and v.Character:FindFirstChild("Head") then
            local Pos, Vis = game.Workspace.CurrentCamera:WorldToScreenPoint(v.Character:FindFirstChild("Head").Position)
            if Vis then
                mag = (Vector2.new(Pos.X,Pos.Y) - Vector2.new(game.Players.LocalPlayer:GetMouse().X,game.Players.LocalPlayer:GetMouse().Y)).magnitude
                if mag < MaxDis and mag <= Client.Values.FOV then
                    Plr = v
                    MaxDis = mag
                end
            end
        end
    end
    return Plr
end

OldFire = (Yawninglmao.Bullet)
Yawninglmao.Bullet = function(...)
    Args = {...}
    if Client.Toggles.SilentAim == true and GetClosestPlr() ~= nil then
        Targ = GetClosestPlr()
        Camera = {CFrame = CFrame.new(game.Workspace.CurrentCamera.CFrame.p,Targ.Character.Head.Position)}
        v141 = (Camera.CFrame * CFrame.new(0, 0, -1)).p
        local v146, v147, v148 = workspace:FindPartOnRayWithWhitelist(Ray.new(Camera.CFrame.p, (v141 - Camera.CFrame.p).unit * 100), {}, false, true);
        Args[2] = Camera.CFrame
        Args[3] = v147
    end
    return OldFire(unpack(Args))
end

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

spawn(function()
    while true do wait(.1)
        if Client.Toggles.NoRecoil == true then
            getupvalue(Yawninglmao.TouchBullet,1).Gun.VRecoil = 0
            getupvalue(Yawninglmao.TouchBullet,1).Gun.HRecoil = 0
            getupvalue(Yawninglmao.TouchBullet,1).Gun.VerticalRecoil = 0
            getupvalue(Yawninglmao.TouchBullet,1).Gun.HorizontalRecoil = 0
            getupvalue(Yawninglmao.TouchBullet,1).Gun.HorizontalRecoilADS = 0
            getupvalue(Yawninglmao.TouchBullet,1).Gun.HorizontalRecoilADS = 0
        end
        if Client.Toggles.NoSpread == true then
            getupvalue(Yawninglmao.TouchBullet,1).Gun.Spread = 0
        end
        if Client.Toggles.InfAmmo == true then
            pcall(function() getupvalue(Yawninglmao.TouchBullet,1).Gun.Ammo.Value = getupvalue(Yawninglmao.TouchBullet,1).Gun.AmmoMax.Value end)
        end
    end
end)
