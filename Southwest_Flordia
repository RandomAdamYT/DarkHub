local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/NewUI"))()
main = lib:Window()
Vehicle = main:Tab('Vehicle')

local function GetCar()
    for _,v in pairs(game:GetService("Workspace").Cars:GetChildren()) do
        if v.ClassName == "Model" then
            for _,v2 in pairs(v:GetChildren()) do
                if v2.Name == "DriveSeat" then
                    for _,v3 in pairs(v2:GetChildren()) do
                        if v3.Name == "carOwner" then
                            if v3.Value == game.Players.LocalPlayer.Name then
                               local Car = require(v["A-Chassis Tune"])
                                return Car
                            end
                        end
                    end
                end
            end
        end
    end
end
Vehicle:Slider('E_Torque', 0, 10000, function(num)
    GetCar()["E_Torque"] = num
end)

Vehicle:Slider('Horsepower', 163, 10000, function(num)
    GetCar()["Horsepower"] = num
end)

Vehicle:Slider('Weight', -1000, 10000, function(num)
    GetCar()["Weight"] = num
end)

Vehicle:Slider('ClutchEngage', .5, 1000, function(num)
    GetCar()["ClutchEngage"] = num
end)

Vehicle:Slider('KickRPMThreshold', 200, 10000, function(num)
    GetCar()["KickRPMThreshold"] = num
end)

Vehicle:Slider('RPMEngage', 1000, 100000, function(num)
    GetCar()["RPMEngage"] = num
end)

Vehicle:Slider('BrakeForce', 0, 100000, function(num)
    GetCar()["BrakeForce"] = num
end)

Vehicle:Slider('RevAccel', 0, 100000, function(num)
    GetCar()["RevAccel"] = num
end)

Vehicle:Slider('ThrotAccel', 0, 100, function(num)
    GetCar()["ThrotAccel"] = num
end)



                       
