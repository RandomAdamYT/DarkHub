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

--Client Values that will save basicly
IsUpToDate = pcall(function()
    Client = {
        Toggles = {
            SilentAim = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.SilentAim or false,
            VisibleCheck = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.VisibleCheck or false,
            Head = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Head or false,
            UseFov = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.UseFov or false,
            NoRecoil = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoRecoil or false,
            NoSpread = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoSpread or false,
            SmallCrosshair = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.SmallCrosshair or false,
            NoSway = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoSway or false,
            NoBob = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoBob or false,
            NoCamBob = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.NoCamBob or false,
            Boxes = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Boxes or false,
            Tracers = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Tracers or false,
            Skeleton = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Skeleton or false,
            Invisible = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Toggles.Invisible or false
        },
        Values = {
            Fov = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.Fov or 500,
            WalkSpeed = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.WalkSpeed or 0,
            JumpPower = DarkHub_Client.SavedSettings and DarkHub_Client.GameSettings.Values.JumpPower or 0
        }
    }
end)

if not IsUpToDate and DarkHub_Client.SavedSettings and isfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB') then
    delfile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB')
    game.Players.LocalPlayer:Kick('DarkHub Settings Out Of Date - Issue Fixed | Restart DarkHub to Continue')
end

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB",true))()
local main = lib:Window()
local Aimbot = main:Tab('Aimbot')
local GunMods = main:Tab('Gun Mods')
local Esp = main:Tab('Esp')
local Misc = main:Tab('Miscellaneous')
local FovCircle = Drawing.new("Circle")
FovCircle.Visible = Client.Toggles.UseFov
FovCircle.Radius = Client.Values.Fov
FovCircle.Color = Color3.new(1, 1, 1)
FovCircle.Thickness = 1
FovCircle.Position = Vector2.new(workspace.Camera.ViewportSize.X * 0.5, workspace.Camera.ViewportSize.Y * 0.5)

local whitelistedcharacters = "abcdefghijklmnopqrstuvwxyz"

local found = {}
local hashes = {}
for i, v in pairs(getnilinstances()) do
    if v.ClassName == "ModuleScript" and (v.Name == "effects" or v.Name == "camera" or v.Name == "particle") then
        found[v.Name] = require(v)
    end
end

for i, v in pairs(getgc(false)) do
    if getinfo(v).name == "loadgun" then
        getgenv()["loadgun"] = v
        break
    end
end

found["network"] = debug.getupvalue(found.effects.breakwindow, 1)
found["char"] = debug.getupvalue(found.effects.muzzleflash, 2)
found["replication"] = debug.getupvalue(found.camera.setspectate, 1)
found["hud"] = debug.getupvalue(found.char.setmovementmode, 10)
found["gamelogic"] = debug.getupvalue(found.char.setsprint, 1)
found["input"] = debug.getupvalue(found.gamelogic.controllerstep, 2)
local gunsway = debug.getupvalue(found.char.loadgrenade, 34)
local gunbob = debug.getupvalue(found.char.loadgrenade, 33)
local gunrequire = debug.getupvalue(loadgun, 2)
local fromaxisangle = debug.getupvalue(found.camera.step, 11)
local physicsignore = {workspace.Players, workspace.Camera, workspace.Ignore}
local userinputservice = game:GetService("UserInputService")
local runservice = game:GetService("RunService")
local workspace = game:GetService("Workspace")
local players = game:GetService("Players")
local localplayer = players.LocalPlayer
local rendertime = tick()
local playeresp = {}
local v3 = Vector3.new()
local newcf = CFrame.new()
local dot = v3.Dot
local accel = Vector3.new(0, -workspace.Gravity, 0)
local badtick, add, reset = tick(), 0, true

for i, v in pairs(found) do
    getgenv()[i] = v

    for o, b in pairs(v) do
        if not getgenv()[o] and type(b) == "function" then
            getgenv()[o] = b
        end
    end
end
local chartable = debug.getupvalue(getbodyparts, 1)
setreadonly(particle, false)

--Framework under this along with ui elements

Aimbot:Toggle('Silent Aim', function(state)
    Client.Toggles.SilentAim = state
end,Client.Toggles.SilentAim)

Aimbot:Toggle('Visible Check', function(state)
    Client.Toggles.VisibleCheck = state
end,Client.Toggles.VisibleCheck)

Aimbot:Toggle('Head Shots Only', function(state)
    Client.Toggles.Head = state
end,Client.Toggles.Head)

Aimbot:Toggle('Use Fov', function(state)
    Client.Toggles.UseFov = state
    FovCircle.Visible = state
end,Client.Toggles.UseFov)

Aimbot:Slider("Fov", 1, 1000, function(num)
    Client.Values.Fov = num
    FovCircle.Radius = num
end,Client.Values.Fov)

GunMods:Toggle('No Recoil', function(state)
    Client.Toggles.NoRecoil = state
end,Client.Toggles.NoRecoil)

GunMods:Toggle('No Spread', function(state)
    Client.Toggles.NoSpread = state
end,Client.Toggles.NoSpread)

GunMods:Toggle('Small Crosshair', function(state)
    Client.Toggles.SmallCrosshair = state
end,Client.Toggles.SmallCrosshair)

GunMods:Toggle('No Sway', function(state)
    Client.Toggles.NoSway = state
end,Client.Toggles.NoSway)

GunMods:Toggle('No Bob', function(state)
    Client.Toggles.NoBob = state
end,Client.Toggles.NoBob)

GunMods:Toggle('No Camera Bob', function(state)
    Client.Toggles.NoCamBob = state
end,Client.Toggles.NoCamBob)

Esp:Toggle('Box Esp', function(state)
    Client.Toggles.Boxes = state
end,Client.Toggles.Boxes)

Esp:Toggle('Tracer Esp', function(state)
    Client.Toggles.Tracers = state
end,Client.Toggles.Tracers)

Esp:Toggle('Skeleton Esp', function(state)
    Client.Toggles.Skeleton = state
end,Client.Toggles.Skeleton)

Misc:Slider("Walk Speed", 0, 100, function(num)
    Client.Values.WalkSpeed = num

    if char.alive then
        char:setbasewalkspeed(gamelogic.currentgun.data.walkspeed + num)
    end
end,Client.Values.WalkSpeed)

Misc:Slider("Jump Power", 0, 100, function(num)
    Client.Values.JumpPower = num
end,Client.Values.JumpPower)

local Gravity = workspace.Gravity
Misc:Slider("Gravity", 0, 100, function(num)
    workspace.Gravity = (Gravity * 0.01) * (100 - num)
end,Client.Values.Gravity)

Misc:Toggle('Invisible', function(state)
    Client.Toggles.Invisible = state
    reset = true
end,Client.Toggles.Invisible)

--Goes under all framework
spawn(function()
    while true do wait(5)
        if DarkHub_Client.SaveSettings then
            writefile('DarkHub/DarkHub_'..tostring(Game.PlaceId)..'.DARKHUB',game:GetService('HttpService'):JSONEncode({['Toggles'] = Client.Toggles,['Values'] = Client.Values}))    
        end
    end
end)

function trajectory(o, a, t, s, e)
    local f = -a
    local ld = t - o
    local a = dot(f, f)
    local b = 4 * dot(ld, ld)
    local k = (4 * (dot(f, ld) + s * s)) / (2 * a)
    local v = (k * k - b / a) ^ 0.5
    local t, t0 = k - v, k + v

    if not (t > 0) then
        t = t0
    end

    t = t ^ 0.5
    return f * t / 2 + (e or v3) + ld / t, t
end

function isvisible(o, t)
    local dist = (o - t).Magnitude
    local part = workspace:FindPartOnRayWithIgnoreList(Ray.new(o, (t - o).Unit * dist), physicsignore)

    return part == nil or part.Transparency ~= 0
end

function getclosest()
    local closest, pos, maxdist = nil, nil, Client.Toggles.UseFov and Client.Values.Fov or math.huge

    for i, v in pairs(chartable) do
        if i.Team ~= localplayer.Team and v.head then
            local screenpos, visible = workspace.Camera:WorldToViewportPoint(v.head.Position)
            local distance = (FovCircle.Position - Vector2.new(screenpos.X, screenpos.Y)).Magnitude

            if visible and (not Client.Toggles.VisibleCheck or isvisible(camera.cframe.Position, v.head.Position)) and distance < maxdist then
                closest = i
                pos = v[Client.Toggles.Head and "head" or "torso"].Position
                maxdist = distance
            end
        end
    end

    return closest, pos
end

function particle.new(data)
    if gamelogic.currentgun and gamelogic.currentgun.barrel and Client.Toggles.SilentAim and gamelogic.currentgun and (data.visualorigin == gamelogic.currentgun.barrel.Position or data.visualorigin == gamelogic.currentgun.aimsightdata[1].sightpart.Position) then
        local closest, pos = getclosest()

        if closest then
            data.velocity = trajectory(data.visualorigin, accel, pos, gamelogic.currentgun.data.bulletspeed)
            data.position = pos
        end
    end

    return new(data)
end

function network.send(self, hashedname, ...)
    local args = {...}
    local name = ""

    for i = 1, hashedname:len() do
        local char = hashedname:sub(i, i)

        if whitelistedcharacters:find(char) then
            name = name .. char
        end
    end

    if name == "newbullets" then
        if Client.Toggles.SilentAim then
            local closest, pos = getclosest()

            if closest and gamelogic.currentgun then
                local velocity = trajectory(args[1].firepos, accel, pos, gamelogic.currentgun.data.bulletspeed)
                
                for i = 1, #args[1].bullets do
                    args[1].bullets[i][1] = velocity
                end
            end
        end
    elseif name == "falldamage" then
        return
   elseif name == "ping" then
       reset = true
    elseif name == "repupdate" and Client.Toggles.Invisible then
       if reset then
           badtick = args[3]
           reset = false
           add = 0
       end
       
        args[1] += Vector3.new(camera.cframe.LookVector.X * add * 0.01, -add, camera.cframe.LookVector.Z * add * 0.01) * 5000
        args[2] = Vector2.new(0, args[2].Y)
        args[3] = badtick + add
        add = add + 0.0000025
    end

    return send(self, hashedname, unpack(args))
end

function char.jump(self, power)
    return jump(self, power + Client.Values.JumpPower)
end

function char.setbasewalkspeed(self, speed)
    return setbasewalkspeed(self, speed + Client.Values.WalkSpeed)
end

function addesp(player)
    playeresp[player] = {
        visible = false,
        all = {},
        boxoutline = Drawing.new("Square"),
        box = Drawing.new("Square"),
        tracer = Drawing.new("Line"),
        skeleton = {
            head = Drawing.new("Line"),
            secondhead = Drawing.new("Line"),
            torso = Drawing.new("Line"),
            leftupperarm = Drawing.new("Line"),
            leftlowerarm = Drawing.new("Line"),
            rightupperarm = Drawing.new("Line"),
            rightlowerarm = Drawing.new("Line"),
            leftupperleg = Drawing.new("Line"),
            leftlowerleg = Drawing.new("Line"),
            rightupperleg = Drawing.new("Line"),
            rightlowerleg = Drawing.new("Line")
        }
    }

    table.insert(playeresp[player].all, playeresp[player].box)
    table.insert(playeresp[player].all, playeresp[player].boxoutline)
    table.insert(playeresp[player].all, playeresp[player].tracer)
    for i, v in pairs(playeresp[player].skeleton) do
        table.insert(playeresp[player].all, v)
    end

    for i, v in pairs(playeresp[player].all) do
        v.Visible = false
        v.Color = Color3.new(1, 1, 1)
        pcall(function()
            v.Thickness = 1
            v.Filled = false
        end)
    end
    playeresp[player].tracer.Color = Color3.new(1, 0, 0)
    playeresp[player].tracer.From = Vector2.new(workspace.Camera.ViewportSize.X * 0.5, 0)
    playeresp[player].boxoutline.Color = Color3.new(0, 0, 0)
    playeresp[player].boxoutline.Thickness = 3
end

function removeesp(player)
    playeresp[player].box:Remove()
    playeresp[player].tracer:Remove()
    for i, v in pairs(playeresp[player].skeleton) do
        v:Remove()
    end
    playeresp[player] = nil
end

for i, v in pairs(players:GetPlayers()) do
    if v ~= localplayer then
        addesp(v)
    end
end

players.PlayerAdded:Connect(addesp)
players.PlayerRemoving:Connect(removeesp)

function getscreenpos(position)
    local screenpos, onscreen = workspace.Camera:WorldToViewportPoint(position)

    return Vector2.new(screenpos.X, screenpos.Y), onscreen
end

function getpartends(part)
    local cf, s = part.CFrame, part.Size
    return getscreenpos(cf * Vector3.new(0, s.Y * 0.5, 0)), getscreenpos(cf * Vector3.new(0, -s.Y * 0.5, 0))
end

runservice.RenderStepped:Connect(function()
    local time = tick()

    if time - rendertime > 0.02 then
        rendertime = time

        if Client.Toggles.UseFov then
            FovCircle.Radius = (char.unaimedfov / workspace.Camera.FieldOfView) * Client.Values.Fov 
            FovCircle.Position = Vector2.new(workspace.Camera.ViewportSize.X * 0.5, workspace.Camera.ViewportSize.Y * 0.5)
        end

        for player, drawings in pairs(playeresp) do
            local char = chartable[player]

            if player.Team ~= localplayer.Team and char and char.head then
                local headpos, onscreen = getscreenpos(char.head.Position)
                local torsopos = getscreenpos(char.torso.Position)

                if onscreen then
                    if not drawings.visible then
                        drawings.visible = true
    
                        drawings.box.Visible = Client.Toggles.Boxes
                        drawings.boxoutline.Visible = Client.Toggles.Boxes
                        drawings.tracer.Visible = Client.Toggles.Tracers
    
                        if Client.Toggles.Skeleton then
                            for i, v in pairs(drawings.skeleton) do
                                v.Visible = true
                            end
                        end
                    end

                    if Client.Toggles.Tracers then
                        drawings.tracer.To = headpos
                    end

                    if Client.Toggles.Boxes then
                        drawings.box.Size = Vector2.new((torsopos.Y - headpos.Y) * 3, (torsopos.Y - headpos.Y) * 4)
                        drawings.box.Position = torsopos - drawings.box.Size * 0.5
                        drawings.boxoutline.Size = drawings.box.Size
                        drawings.boxoutline.Position = drawings.box.Position
                    end

                    if Client.Toggles.Skeleton then
                        local torsotop, torsobottom = getpartends(char.torso)
                        local rarmtop, rarmbottom = getpartends(char.rarm)
                        local larmtop, larmbottom = getpartends(char.larm)
                        local rlegtop, rlegbottom = getpartends(char.rleg)
                        local llegtop, llegbottom = getpartends(char.lleg)
                        local rarm = getscreenpos(char.rarm.Position)
                        local larm = getscreenpos(char.larm.Position)
                        local rleg = getscreenpos(char.rleg.Position)
                        local lleg = getscreenpos(char.lleg.Position)
                        local endpoint = getscreenpos(char.torso.CFrame * Vector3.new(0, -char.torso.Size.Y * 0.5, -1))

                        drawings.skeleton.head.From = headpos
                        drawings.skeleton.head.To = torsotop
                        drawings.skeleton.secondhead.From = torsobottom
                        drawings.skeleton.secondhead.To = endpoint
                        drawings.skeleton.torso.From = torsobottom
                        drawings.skeleton.torso.To = torsotop
                        drawings.skeleton.leftupperarm.From = torsotop
                        drawings.skeleton.leftupperarm.To = larm
                        drawings.skeleton.leftlowerarm.From = larmbottom
                        drawings.skeleton.leftlowerarm.To = larm
                        drawings.skeleton.rightupperarm.From = torsotop
                        drawings.skeleton.rightupperarm.To = rarm
                        drawings.skeleton.rightlowerarm.From = rarmbottom
                        drawings.skeleton.rightlowerarm.To = rarm
                        drawings.skeleton.leftupperleg.From = torsobottom
                        drawings.skeleton.leftupperleg.To = lleg
                        drawings.skeleton.leftlowerleg.From = llegbottom
                        drawings.skeleton.leftlowerleg.To = lleg
                        drawings.skeleton.rightupperleg.From = torsobottom
                        drawings.skeleton.rightupperleg.To = rleg
                        drawings.skeleton.rightlowerleg.From = rlegbottom
                        drawings.skeleton.rightlowerleg.To = rleg
                    end
                elseif drawings.visible then
                    drawings.visible = false
                    drawings.box.Visible = false
                    drawings.boxoutline.Visible = false
                    drawings.tracer.Visible = false
                    
                    for i, v in pairs(drawings.skeleton) do
                        v.Visible = false
                    end
                end
            elseif drawings.visible then
                drawings.visible = false
                drawings.box.Visible = false
                drawings.boxoutline.Visible = false
                drawings.tracer.Visible = false
                
                for i, v in pairs(drawings.skeleton) do
                    v.Visible = false
                end
            end
        end
    end
end)

debug.setupvalue(loadgun, 2, function(...)
    local data = gunrequire(...)
    setreadonly(data, false)

    if Client.Toggles.NoRecoil then
        data["aimcamkickspeed"] = 9999999
        data["camkickspeed"] = 9999999
        data["modelkickspeed"] = 9999999
    end

    if Client.Toggles.NoSpread then
        data["hipfirespreadrecover"] = 9999999
        data["hipfirespread"] = 9999999
    end

    if Client.Toggles.SmallCrosshair then
        data["crosssize"] = 1
        data["crossexpansion"] = 0
    end

    return data
end)

debug.setupvalue(camera.step, 11, function(...)
    return Client.Toggles.NoCamBob and newcf or fromaxisangle(...)
end)

debug.setupvalue(loadgun, 57, function(...)
    return Client.Toggles.NoBob and newcf or gunbob(...)
end)

debug.setupvalue(loadgun, 58, function(...)
    return Client.Toggles.NoSway and newcf or gunsway(...)
end)
