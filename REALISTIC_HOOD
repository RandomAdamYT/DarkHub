Client = {
    Toggles = {
     AutoFarm = false   
        
    }
}
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub_V3/main/UILIB",true))()
main = lib:Window()
Extra = main:Tab('Extra')


Extra:Toggle('Cash-AutoFarm',function(state)
Client.Toggles.AutoFarm = state
end)

while task.wait() do
    for i = 1,10 do
        if Client.Toggles.AutoFarm then
    game:GetService("ReplicatedStorage").Money:FireServer(' Watermelon ? ')
        end
        end
    end
