
--[[
	we 𐎠re tr𐏑v5 𐏃𐎢𐎲 𐎠nd 𐎭rk 𐏃𐎢𐎲
]] 

--[[Tabs and Uilib]]--
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
local main = lib:Window()
local AutoW = main:Tab("AutoFarm")
local AutoBuyW = main:Tab("AutoBuy")
local PlayerW = main:Tab("LocalPlayer")
local gis = main:Tab("Gui")
local MiscW = main:Tab("Misc")

--[[Config]]--
Client = {
    AutoFarm = {
        AutoFarmArea = "",
        AutoFarmCoin = false,
        AutoChestArea = "",
        AutoChestFarm = false,
        AutoGemSnipe = false,
        Autouse3xCoinsBoost = false,
        Autouse3xCoinsDamage = false,
        AutoCollectLootBag = false,
        AutoCollectOrbs = false
    },
    AutoBuy = {
        SelectedEgg = "",
        AutoBuyOneEgg = false,
        AutoBuyTripleEgg = false, -- // You must own the gamepass 
        AutouseSuperLucky = false,
        AutouseUltraLucky = false,
    },
    Player = {
        InfJump = false
    },
    Misc = {
        SelectedHov = ""
    },
}

--[[Functions And Stuff]]--

local AreaList = { 
    'VIP', 
    'Town',
    'Forest',
    'Beach',
    'Mine',
    'Winter',
    'Glacier',
    'Desert',
    'Volcano',
    'Enchanted Forest', 
    'Ancient',
    'Samurai', 
    'Candy', 
    'Haunted', 
    'Hell', 
    'Heaven',
    'Ice Tech',
    'Tech City',
    'Dark Tech',
    'Steampunk',
    'Alien Lab',
    'Alien Forest',
    'Glitch',
    'Axolotl Ocean', 
    'Axolotl Deep Ocean',
    'Axolotl Cave',
    'Pixel Forest',
    'Pixel Kyoto',
    'Pixel Alps',
    'Pixel Vault'
}

local ChestsPlace = {
    "Magma Chest",
    "Enchanted Chest", 
    "Hell Chest", 
    "Haunted Chest", 
    "Angel Chest", 
    "Grand Heaven Chest",
    "Giant Tech Chest",
    "Giant Steampunk Chest", 
    "Giant Alien Chest", 
    "Giant Hacker Chest",
    "Giant Ocean Chest",
    "Giant Pixel Chest"
}

local AllHov = {
    "Blue Flying Carpet",
    "Flame",
    "Sleigh",
    "Red Flying Carpet",
    "VIP",
    "Bling",
    "Rainbow",
    "Original",
    "Cat",
    "Steampunk"
}

function eggers()
    local eggtable = {} -- Grabbs all Egg names and puts in a Table (Auto Update)
        for i,v in pairs(game:GetService("ReplicatedStorage").Game.Eggs:GetChildren()) do
            for i2,v2 in pairs(v:GetChildren()) do
                table.insert(eggtable, v2.Name)
            end
        end
    return eggtable
end

local petmod = require(game:GetService("ReplicatedStorage").Framework.Library)

local function farmcoin(coinid, petid)
    game.workspace['__THINGS']['__REMOTES']["join coin"]:InvokeServer({[1] = coinid, [2] = {[1] = petid}})
    game.workspace['__THINGS']['__REMOTES']["farm coin"]:FireServer({[1] = coinid, [2] = petid})
end

local function getpets()
    local pettable = {}
    for i,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.Inventory.Frame.Main.Pets:GetChildren()) do
        if v.ClassName == 'TextButton' and v.Equipped.Visible then
            table.insert(pettable, v.Name)
        end
    end
    return pettable
end

function CollectOrbs()
    local Table = {[1] = {}} -- Will Grab Orbs ID/Table
    for i,v in pairs(game.workspace['__THINGS'].Orbs:GetChildren()) do
        Table[1][i] = v.Name
    end
    game.workspace['__THINGS']['__REMOTES']["claim orbs"]:FireServer(Table)
end

local function getcoin(area)
    local cointable = {}
    local allcoins = game.workspace['__THINGS']['__REMOTES']["get coins"]:InvokeServer({})[1]
    for i,v in pairs(allcoins) do
        if v.n:match(area) then
            table.insert(cointable, i)
        end
    end
    return cointable
end

local function getChest(area)
    local cointable = {}
    local allcoins = game.workspace['__THINGS']['__REMOTES']["get coins"]:InvokeServer({})[1]
    for i,v in pairs(allcoins) do
        if v.n:match(Client.AutoFarm.AutoChestArea) then
            table.insert(cointable, i)
        end
    end
    return cointable
end

function GetDiamond(area)
   local returntable = {}
   local ListCoins = game.workspace['__THINGS']['__REMOTES']["get coins"]:InvokeServer({})[1]
   for i,v in pairs(ListCoins) do
       if v.n:match("Diamonds") then
           table.insert(returntable, i)
       end
   end
   return returntable
end

function CollectLootBag()
    local cmod = getsenv(game:GetService("Players").LocalPlayer.PlayerScripts.Scripts.Game.Lootbags)
        for i,v in pairs(game:GetService("Workspace")["__THINGS"].Lootbags:GetChildren()) do
            cmod.Collect(v)
    end
end

task.spawn(function()
    while true do
        task.wait(0.01)
        if Client.AutoFarm.AutoFarmCoin == true then
        local farmablecoin = getcoin(Client.AutoFarm.AutoFarmArea)
        local petequipped = getpets()
            for i = 1, #farmablecoin do
                pcall(function()
                    farmcoin(farmablecoin[i], petequipped[i%#petequipped+1])
                end)
            end
        end
    end
end)

task.spawn(function()
    while true do
        task.wait(0.01)
        if Client.AutoFarm.AutoChestFarm == true then
        local farmablecoin = getChest()
        local petequipped = getpets()
            for i = 1, #farmablecoin do
                pcall(function()
                    farmcoin(farmablecoin[i], petequipped[i%#petequipped+1])
                end)
            end
        end
    end
end)

task.spawn(function()
    while true do
        task.wait(0.01)
        if Client.AutoFarm.AutoGemSnipe == true then
        local farmablecoin = GetDiamond()
        local petequipped = getpets()
            for i = 1, #farmablecoin do
                pcall(function()
                    farmcoin(farmablecoin[i], petequipped[i%#petequipped+1])
                end)
            end
        end
    end
end)

task.spawn(function() 
    while true do
        task.wait(1)
        if Client.AutoFarm.Autouse3xCoinsBoost == true then
            if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Boosts:FindFirstChild("Triple Coins") then
                petmod.Network.Fire("activate boost", "Triple Coins")
            end
        end
    end
end)

task.spawn(function()
    while true do
        task.wait(0.1)
        if Client.AutoBuy.AutoBuyOneEgg == true then
            if Client.AutoBuy.SelectedEgg ~= "" then
                petmod.Network.Invoke("Buy Egg", Client.AutoBuy.SelectedEgg, false)
            end
        end
    end
end)

task.spawn(function()
    while true do
        task.wait(0.1)
        if Client.AutoBuy.AutoBuyTripleEgg == true then
            if Client.AutoBuy.SelectedEgg ~= "" then
                petmod.Network.Invoke("Buy Egg", Client.AutoBuy.SelectedEgg, true)
            end
        end
    end
end)

task.spawn(function()
    while true do
        task.wait(1)
        if Client.AutoFarm.Autouse3xCoinsDamage == true then
            if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Boosts:FindFirstChild("Triple Damage") then
                petmod.Network.Fire("activate boost", "Triple Damage")
            end
        end
    end
end)

task.spawn(function() -- add them in toggle
    while true do
        task.wait(1)
        if Client.AutoBuy.AutouseSuperLucky == true then
            if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Boosts:FindFirstChild("Super Lucky") then
                petmod.Network.Fire("activate boost", "Super Lucky")
            end
        end
    end
end)

task.spawn(function() -- add them in toggle
    while true do
        task.wait(1)
        if Client.AutoBuy.AutouseUltraLucky == true then
            if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Boosts:FindFirstChild("Ultra Lucky") then
                petmod.Network.Fire("activate boost", "Ultra Lucky")
            end
        end
    end
end)


task.spawn(function()
    while true do
        task.wait(0.2)
        if Client.AutoFarm.AutoCollectOrbs == true then 
            CollectOrbs()
        end
    end
end)

game:GetService("UserInputService").JumpRequest:connect(function()
    if Client.Player.InfJump then
        game:GetService"Players".LocalPlayer.Character:FindFirstChildOfClass'Humanoid':ChangeState("Jumping")
    end
end)

task.spawn(function()
    while true do
        task.wait(0.2)
        if Client.AutoFarm.AutoCollectLootBag == true then 
            CollectLootBag()
        end
    end
end)

--// Fly script From Fat IY
 function getRoot(char)
    local rootPart = char:FindFirstChild('HumanoidRootPart') or char:FindFirstChild('Torso') or char:FindFirstChild('UpperTorso')
    return rootPart
    end
    local Players = game:GetService("Players")
     local IYMouse = game:GetService("Players").LocalPlayer:GetMouse()
     FLYING = false
        QEfly = true
        iyflyspeed = 1
        vehicleflyspeed = 1
        function sFLY(vfly)
        repeat wait() until Players.LocalPlayer and Players.LocalPlayer.Character and getRoot(Players.LocalPlayer.Character) and Players.LocalPlayer.Character:FindFirstChild('Humanoid')
        repeat wait() until IYMouse
        if flyKeyDown or flyKeyUp then flyKeyDown:Disconnect() flyKeyUp:Disconnect() end
    
        local T = getRoot(Players.LocalPlayer.Character)
        local CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
        local lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
        local SPEED = 0
    
        local function FLY()
            FLYING = true
            local BG = Instance.new('BodyGyro')
            local BV = Instance.new('BodyVelocity')
            BG.P = 9e3
            BG.Parent = T
            BV.Parent = T
            BG.maxTorque = Vector3.new(9e4, 9e4, 9e4)
            BG.cframe = T.CFrame
            BV.velocity = Vector3.new(0, 0, 0)
            BV.maxForce = Vector3.new(9e4, 9e4, 9e4)
            task.spawn(function()
                repeat wait()
                    if not vfly and Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
                        Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = true
                    end
                    if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0 then
                        SPEED = 50
                    elseif not (CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0) and SPEED ~= 0 then
                        SPEED = 0
                    end
                    if (CONTROL.L + CONTROL.R) ~= 0 or (CONTROL.F + CONTROL.B) ~= 0 or (CONTROL.Q + CONTROL.E) ~= 0 then
                        BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (CONTROL.F + CONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
                        lCONTROL = {F = CONTROL.F, B = CONTROL.B, L = CONTROL.L, R = CONTROL.R}
                    elseif (CONTROL.L + CONTROL.R) == 0 and (CONTROL.F + CONTROL.B) == 0 and (CONTROL.Q + CONTROL.E) == 0 and SPEED ~= 0 then
                        BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (lCONTROL.F + lCONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(lCONTROL.L + lCONTROL.R, (lCONTROL.F + lCONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
                    else
                        BV.velocity = Vector3.new(0, 0, 0)
                    end
                    BG.cframe = workspace.CurrentCamera.CoordinateFrame
                until not FLYING
                CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
                lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
                SPEED = 0
                BG:Destroy()
                BV:Destroy()
                if Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
                    Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = false
                end
            end)
        end
        flyKeyDown = IYMouse.KeyDown:Connect(function(KEY)
            if KEY:lower() == 'w' then
                CONTROL.F = (vfly and vehicleflyspeed or iyflyspeed)
            elseif KEY:lower() == 's' then
                CONTROL.B = - (vfly and vehicleflyspeed or iyflyspeed)
            elseif KEY:lower() == 'a' then
                CONTROL.L = - (vfly and vehicleflyspeed or iyflyspeed)
            elseif KEY:lower() == 'd' then 
                CONTROL.R = (vfly and vehicleflyspeed or iyflyspeed)
            elseif QEfly and KEY:lower() == 'e' then
                CONTROL.Q = (vfly and vehicleflyspeed or iyflyspeed)*2
            elseif QEfly and KEY:lower() == 'q' then
                CONTROL.E = -(vfly and vehicleflyspeed or iyflyspeed)*2
            end
            pcall(function() workspace.CurrentCamera.CameraType = Enum.CameraType.Track end)
        end)
        flyKeyUp = IYMouse.KeyUp:Connect(function(KEY)
            if KEY:lower() == 'w' then
                CONTROL.F = 0
            elseif KEY:lower() == 's' then
                CONTROL.B = 0
            elseif KEY:lower() == 'a' then
                CONTROL.L = 0
            elseif KEY:lower() == 'd' then
                CONTROL.R = 0
            elseif KEY:lower() == 'e' then
                CONTROL.Q = 0
            elseif KEY:lower() == 'q' then
                CONTROL.E = 0
            end
        end)
        FLY()
     end
    
     function NOFLY()
        FLYING = false
        if flyKeyDown or flyKeyUp then flyKeyDown:Disconnect() flyKeyUp:Disconnect() end
        if Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
            Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = false
        end
        pcall(function() workspace.CurrentCamera.CameraType = Enum.CameraType.Custom end)
end

-- // Fire Works
for i = 1, 7 do
    local FireOnPlayer = game:GetService("Players").LocalPlayer
    game:GetService("ReplicatedStorage").Framework.Modules["2 | Network"]["fireworks animation"]:Fire(FireOnPlayer)
end
--

--[[AutoFarm Tab]]--

AutoW:Dropdown('Select Area',AreaList,function(Selected)
    Client.AutoFarm.AutoFarmArea = Selected
end)

AutoW:Toggle('AutoFarm Coin',function(state)
    Client.AutoFarm.AutoFarmCoin = state
end)

AutoW:Dropdown('Select Chest',ChestsPlace,function(Selected)
    Client.AutoFarm.AutoChestArea = Selected
end)

AutoW:Toggle('AutoFarm Chest',function(state)
    Client.AutoFarm.AutoChestFarm = state
end)

AutoW:Toggle('Gem Snipe',function(state)
    Client.AutoFarm.AutoGemSnipe = state
end)

AutoW:Toggle('Insta Collect Orbs',function(state)
    Client.AutoFarm.AutoCollectOrbs = state
end)

AutoW:Toggle('Insta Collect Loot Bags',function(state)
    Client.AutoFarm.AutoCollectLootBag = state
end)

AutoW:Toggle('Auto use 3x Coins Boost',function(state)
    Client.AutoFarm.Autouse3xCoinsBoost = state
end)

AutoW:Toggle('Auto use 3x Coins Damage',function(state)
    Client.AutoFarm.Autouse3xCoinsDamage = state
end)

AutoW:Toggle('No Lag',function(state)
    game:GetService("Players").LocalPlayer.PlayerScripts.Scripts.Game.Coins.Disabled = state
end)

--[[Auto Buy]]--

AutoBuyW:Dropdown('Select Egg',eggers(),function(Selected)
    Client.AutoBuy.SelectedEgg = Selected
end)

AutoBuyW:Toggle('Auto Buy Egg',function(state)
    Client.AutoBuy.AutoBuyOneEgg = state
end)

AutoBuyW:Toggle('Auto Buy Triple Egg',function(state)
    Client.AutoBuy.AutoBuyTripleEgg = state
end)

AutoBuyW:Toggle('Remove Egg Animation',function(state)
    game:GetService("Players").LocalPlayer.PlayerScripts.Scripts.Game["Open Eggs"].Disabled = state
end)

AutoBuyW:Toggle('Auto use Super Lucky',function(state)
    Client.AutoBuy.AutouseSuperLucky = state
end)

AutoBuyW:Toggle('Auto use Ultra Lucky',function(state)
    Client.AutoBuy.AutouseUltraLucky = state
end)

--[[Player Stuff]]--


PlayerW:Slider('Gravity',0,196.2,function(num)
    game.Workspace.Gravity = num
end)

PlayerW:Toggle('Inf Jump ',function(state)
    Client.Player.InfJump = state
end)

PlayerW:Slider('WalkSpeed Config',16,500,function(num)
    game:GetService('Players').LocalPlayer.Character.Humanoid.WalkSpeed = num
end)

PlayerW:Slider('JumpPower Config',50,200,function(num)
    game:GetService('Players').LocalPlayer.Character.Humanoid.JumpPower = num
end)

PlayerW:Toggle('Fly',function(state)
    if state then 
        sFLY()
    else
        NOFLY()
    end
end)

PlayerW:Slider('Fly Config',1,15,function(Value)
    iyflyspeed = Value
end)

--[[Gui Tab]]--

gis:Button("Upgrades",function()
    game.Players.LocalPlayer.PlayerGui.Upgrades.Enabled = true
end)

gis:Button("Fuse Pets",function()
    game.Players.LocalPlayer.PlayerGui.FusePets.Enabled = true
end)

gis:Button("Golden Machine",function()
    game.Players.LocalPlayer.PlayerGui.Golden.Enabled = true
end)

gis:Button("Rainbow Machine",function()
    game.Players.LocalPlayer.PlayerGui.Rainbow.Enabled = true
end)

gis:Button("Collections",function()
    game.Players.LocalPlayer.PlayerGui.Collection.Enabled = true
end)

gis:Button("Merchant Shop",function()
    game.Players.LocalPlayer.PlayerGui.Merchant.Enabled = true
end)

gis:Button("Dark Matter Machine",function()
    game.Players.LocalPlayer.PlayerGui.DarkMatter.Enabled = true
end)

gis:Button("Bank",function()
    game.Players.LocalPlayer.PlayerGui.Bank.Enabled = true
end)

--[[Misc Tab]]--


MiscW:Button("Anti-Afk",function()
    -- // LeLz thx IY for using your AntiAfk
    local GC = getconnections or get_signal_cons
    if GC then
        for i,v in pairs(GC(game.Players.LocalPlayer.Idled)) do
            if v["Disable"] then
                v["Disable"](v)
            elseif v["Disconnect"] then
                v["Disconnect"](v)
            end
        end
    else
        local vu = game:GetService("VirtualUser")
        game:GetService("Players").LocalPlayer.Idled:connect(function()
            vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
            wait(1)
            vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
        end)
    end
end)

MiscW:Button("Redeem Codes",function()
    local codes = {"halfamillion","Clouds","plaid1234","Underworld","morecodes3","blamedavid","Back2Back","FreeDiamonds0","SuperUltra1","Triple275k","FirstUpdate","Ultra225k","DiscordDiamonds","MoreCoins180k","EzDiamonds150k","Easy125k","Triple80k","Lucky50k","Super25k","Release","triple800","easyboosts","VoiceChat"}
        local function redeem(c)
            local A_1 =
                {
                [1] = c
                }
            local Event = game:GetService("Workspace")["__THINGS"]["__REMOTES"]["redeem twitter code"]
            Event:InvokeServer(A_1)
        end
        for _,v in pairs(codes) do
            redeem(v)
        end
end)

MiscW:Button("Collect VIP Rewards",function()
    petmod.Network.Invoke("Redeem VIP Rewards")
end)

MiscW:Dropdown('Select HoverBoard',AllHov,function(Selected) -- // FrontMan𐎺#9917 Did This Whole Script In one and a half day, UNBELIEVABLE 
    Client.Misc.SelectedHov = Selected
end)

MiscW:Button("Free HoverBoard",function() -- // Bye...#0001 Was Here And He Says UwU!
    local HoverBoard = getsenv(game:GetService("Players").LocalPlayer.PlayerScripts.Scripts.Game.Hoverboard)
    local FramWork = require(game:GetService("ReplicatedStorage").Framework.Library)
    FramWork.Save.Get().EquippedHoverboard = Client.Misc.SelectedHov
    HoverBoard.Create(FramWork.LocalPlayer)
end)
