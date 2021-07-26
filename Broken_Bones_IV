function GetScript()
    for i,v in pairs(game:GetService("ReplicatedFirst"):GetChildren()) do
        if (v.Name):match("^%-?%d+$") then
            return v    
        end
    end
end
local FireServer = getupvalue(getsenv(GetScript()).Respawn,5)
local Remotes = getupvalue(getsenv(GetScript()).Respawn,6)
function GiveMoney(Money)
    u5 = getupvalue(getconnections(Remotes["19574636"].OnClientEvent)[1].Function,1)
    u6 = getupvalue(getconnections(Remotes["38593640"].OnClientEvent)[1].Function,1)
    u7 = getupvalue(getconnections(Remotes["75924856"].OnClientEvent)[1].Function,1)
    Code = ("money"):byte() * Money + u5 * -21 + u6 * -45 + u7 * -63
    Remotes.UpdateStat:InvokeServer('money',Money,nil,Code)
    getsenv(GetScript()).pstats.money = getsenv(GetScript()).pstats.money + Money
    getsenv(GetScript()).gui.Data.Money.Text = getsenv(GetScript()).Comma(getsenv(GetScript()).pstats.money)
end
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB",true))()
main = lib:Window()
MainWindow = main:Tab('Broken Bones 4')
MainWindow:Button('Give 10000 Money',function()
    GiveMoney(10000)
end)
MainWindow:Button('Give 1M Money',function()
    GiveMoney(1000000)
end)
MainWindow:Button('Give 1B Money',function()
    GiveMoney(1000000000)
end)
