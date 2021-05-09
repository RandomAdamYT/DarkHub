--Made by nameless#3675

local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
local Farming_Tab = main:Tab('Farming')
Client = {
	Toggles = {
		AutoFarm = false
	}
}
Farming_Tab:Toggle('AutoFarm',function(state)
	Client.Toggles.AutoFarm = state
end)

local Meepcity = game
Meepcity.ReplicatedStorage.Connection:InvokeServer(9, 1)
Meepcity:GetService("RunService").RenderStepped:Connect(function()
	if Client.Toggles.AutoFarm then
		Meepcity.ReplicatedStorage.Connection:InvokeServer(49)
		Meepcity.ReplicatedStorage.Connection:InvokeServer(50)
		Meepcity.ReplicatedStorage.Connection:InvokeServer(51)
		local ohNumber1 = 11
		local ohTable2 = {
			["FishingPolePos"] = Meepcity:GetService("Workspace").TempFish.Position,
			["Power"] = 1,
			["Face"] = Meepcity:GetService("Workspace").TempFish.Position,
			["PlayerPos"] = Meepcity:GetService("Workspace").TempFish.Position,
			["FishingZonePos"] = Vector3.new(-5.29345703, -18.0412292, 43.7173767)
		}
		Meepcity:GetService("ReplicatedStorage").Connection:InvokeServer(ohNumber1, ohTable2)
	end
end)
-------------------------------------------------------------------------------------


--> Get Plus (local only) <--
game.ReplicatedStorage.PlayerData[game.Players.LocalPlayer.UserId].PLUS.Value = true
--use it whit Auto Farm to Get 1,5 % More coins when you farm

