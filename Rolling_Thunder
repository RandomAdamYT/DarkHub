local Q = syn and syn.queue_on_teleport or queue_on_teleport
if not Q then game.Players.LocalPlayer:Kick('Exploit not supported!') return end
Q(game:HttpGet(('https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/Rolling_Thunder'), true))
repeat wait() until game:IsLoaded()
local Network;
repeat wait() pcall(function()
    Network = getupvalue(getupvalue(require(game.ReplicatedStorage.Network),1),2)
end) until Network
local Old = tonumber(game.Players.LocalPlayer:GetAttribute("Kills"))
function ServerHop() 
    local HttpService, TPService = game:GetService("HttpService"), game:GetService("TeleportService")
    function RandomServer()
        Temp_Servers = {}
        local ServersToTP = HttpService:JSONDecode(game:HttpGet("https://games.roblox.com/v1/games/"..game.PlaceId.."/servers/Public?sortOrder=Asc&limit=100"))
        for i,v in pairs(ServersToTP.data) do
            if v.playing ~= v.maxPlayers then
                table.insert(Temp_Servers,v)
            end
        end
        return Temp_Servers[math.random(1,#Temp_Servers)]
    end
    TPService:TeleportToPlaceInstance(game.PlaceId, RandomServer().id)
end
spawn(function()
    while true do wait(.2)
        if game:GetService("Players").LocalPlayer.PlayerGui:FindFirstChild('Menu') then
            repeat wait() pcall(function()
                getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Menu.Deploy.D.MouseButton1Down)[1].Function()
            end) until not game:GetService("Players").LocalPlayer.PlayerGui:FindFirstChild('Menu')
            wait(1.3)
        else
            game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(game:GetService("Workspace").SpawnLocation.CFrame)
            for i,v in pairs(game.Workspace:GetChildren()) do
                if v:FindFirstChild('Fire') and v:FindFirstChild('HumanoidRootPart') then
                    Network:FireServer('Nade',v.HumanoidRootPart.CFrame,workspace.CurrentCamera.CFrame.LookVector,'Frag',5)
                end
            end
            if (tonumber(game.Players.LocalPlayer:GetAttribute("Kills")) - Old) > 900 then
                ServerHop()
                break
            end
        end
    end
end)
