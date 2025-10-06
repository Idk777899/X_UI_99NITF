local Item = workspace:WaitForChild("Items")
local CH = workspace:WaitForChild("Characters")
local P = game:GetService("Players")
local R = game:GetService("ReplicatedStorage")
local L = P.LocalPlayer
local C = L.Character or L.CharacterAdded:Wait()
local H = C:WaitForChild("Humanoid")
local HRP = C:WaitForChild("HumanoidRootPart")
local T = game:GetService("TweenService")
local CORE = game:GetService("CoreGui")
local PG = L:WaitForChild("PlayerGui")
local V = game:GetService("VirtualUser")
local SG = game:GetService("StarterGui")
local Option
local Dis
getgenv().FA = nil
task.spawn(function()
    while task.wait() do
        if getgenv().FA then
            pcall(function()
                for i,v in pairs(CH:GetChildren()) do
                    if v.HumanoidRootPart then
                        local ds = (v.HumanoidRootPart.Position - HRP.Position).Magnitude
                        if ds <= Dis then
                            local args = {
                                v,
                                game:GetService("Players").LocalPlayer:WaitForChild("Inventory"):WaitForChild("Old Axe"),
                                "1_9551232603",
                                HRP.CFrame
                            }
                            game:GetService("ReplicatedStorage"):WaitForChild("RemoteEvents"):WaitForChild("ToolDamageObject"):InvokeServer(unpack(args))
                        end
                    end
                end
            end)
        end
    end
end)
local WindUI = loadstring(game:HttpGet("https://github.com/Footagesus/WindUI/releases/latest/download/main.lua"))()
local Window = WindUI:CreateWindow({
    Title = "X-99 (in game)",
    Icon = "x",
    Author = "by K_1Nr",
    Folder = "MySuperHub",
    Size = UDim2.fromOffset(580, 460),
    MinSize = Vector2.new(560, 350),
    MaxSize = Vector2.new(850, 560),
    Transparent = true,
    Theme = "Dark",
    Resizable = true,
    SideBarWidth = 200,
    BackgroundImageTransparency = 0.42,
    HideSearchBar = true,
    ScrollBarEnabled = false,
    User = {
        Enabled = true,
        Anonymous = false,
        Callback = function()
            print("clicked")
        end,
    },
})
Window:Tag({
        Title = "Legacy",
        Color = Color3.fromHex("#FF0000"),
        Radius = 5, -- from 0 to 13
    })
local Tab1 = Window:Tab({
    Title = "Main",
    Icon = "house", -- optional
    Locked = false,
})
local Section = Tab1:Section({Title = "Kill Aura",})
local Slider = Tab1:Slider({
    Title = "Slider",
    Step = 1,
    Value = {
        Min = 0,
        Max = 1000,
        Default = 30,
    },
    Callback = function(value)
        Dis = tonumber(value)
        print(Dis)
    end
})
local Toggle = Tab1:Toggle({
    Title = "Toggle Kill Aura",
    Desc = "Kill every mob in the game",
    Icon = "",
    Type = "Toggle",
    Default = false,
    Callback = function(state) 
        getgenv().FA = state
    end
})
local Tab2 = Window:Tab({
    Title = "Bring",
    Icon = "codepen", -- optional
    Locked = false,
})
local Section = Tab2:Section({Title = "Bring Config",})
local Dropdown = Tab2:Dropdown({
    Title = "Bring at?",
    Values = { "Campfire", "Player", "Grinder"},
    Value = "...",
    Callback = function(option) 
        Option = option
        print(Option)
    end
})
Tab2:Divider()
local Section = Tab2:Section({Title = "Fuels",})
local G
local Dropdown = Tab2:Dropdown({
    Title = "Fuels Schedule",
    Values = { "Log", "Coal", "Fuel Canister", "Oil Barrel" },
    Value = "...",
    Callback = function(option)
        G = option
    end
})
local Button = Tab2:Button({
    Title = "Bring Item",
    Locked = false,
    Callback = function()
        for i,v in pairs(Item:GetChildren()) do
            if v.Name == G then
                for i,c in pairs(v:GetChildren()) do
                    if not c.CFrame then return end
                    if Option == "Campfire" then
                        c.CFrame = CFrame.new(1.62860501, 11.7039776, 0.2124511, -0.786170661, 5.61900073e-08, -0.618009448, 9.28167125e-08, 1, -2.71513123e-08, 0.618009448, -7.8707167e-08, -0.786170661) * CFrame.new(0,35,0)
                    elseif Option == "Player" then
                        c.CFrame = HRP.CFrame
                    elseif Option == "Grinder" then
                        c.CFrame = workspace.Map.Campground.Scrapper.Movers.Right.GrindersRight.CFrame * CFrame.new(0,35,0)
                    end
                end
            end
        end
    end
})
Tab2:Divider()
local Section = Tab2:Section({Title = "Foods",})
local Dropdown = Tab2:Dropdown({
    Title = "Foods Schedule",
    Values = { "Apple", "Carrot", "Berry", "Chili", "Corn" , "Pumpkin", "Morsel", "Steak", "Ribs", "Cake", "Stew", "Hearty Stew", "Meat? Sandwich", "Seafood Chowder", "Steak Dinner", "Pumpkin Soup", "BBQ Ribs", "Carrot Cake", "Jar o' Jelly", "Mackerel", "Salmon", "Clownfish", "Jellyfish", "Char", "Eel", "Swordfish", "Shark", "Lava Eel", "Lionfish"},
    Value = "...",
    Callback = function(option)
        G = option
    end
})
local Button = Tab2:Button({
    Title = "Bring Item",
    Locked = false,
    Callback = function()
        for i,v in pairs(Item:GetChildren()) do
            if v.Name == G then
                for i,c in pairs(v:GetChildren()) do
                    if not c.CFrame then return end
                    if Option == "Campfire" then
                        c.CFrame = CFrame.new(1.62860501, 11.7039776, 0.2124511, -0.786170661, 5.61900073e-08, -0.618009448, 9.28167125e-08, 1, -2.71513123e-08, 0.618009448, -7.8707167e-08, -0.786170661) * CFrame.new(0,35,0)
                    elseif Option == "Player" then
                        c.CFrame = HRP.CFrame
                    elseif Option == "Grinder" then
                        c.CFrame = workspace.Map.Campground.Scrapper.Movers.Right.GrindersRight.CFrame * CFrame.new(0,35,0)
                    end
                end
            end
        end
    end
})
Tab2:Divider()
local Section = Tab2:Section({Title = "Materials",})
local Dropdown = Tab2:Dropdown({
    Title = "Materials Schedule",
    Values = { "Log", "Chair", "Bolt", "Sheet Metal", "UFO Junk", "UFO Componenet", "Broken Fan", "Old Radio", "Broken Microwave", "Tyre", "Metal Chair", "Old Car Engine", "Cultist Experiment", "Cultist Prototype", "UFO Scrap", "Cultist Gem", "Gem of the Forest Fragment", "Coin Stack", "Flower", "Sapling", "Sacrifice Totem", "Meteor Shard", "Gold Shard", "Raw Obsidiron Ore", },
    Value = "...",
    Callback = function(option)
        G = option
    end
})
local Button = Tab2:Button({
    Title = "Bring Item",
    Locked = false,
    Callback = function()
        for i,v in pairs(Item:GetChildren()) do
            if v.Name == G then
                for i,c in pairs(v:GetChildren()) do
                    if not c.CFrame then return end
                    if Option == "Campfire" then
                        c.CFrame = CFrame.new(1.62860501, 11.7039776, 0.2124511, -0.786170661, 5.61900073e-08, -0.618009448, 9.28167125e-08, 1, -2.71513123e-08, 0.618009448, -7.8707167e-08, -0.786170661) * CFrame.new(0,35,0)
                    elseif Option == "Player" then
                        c.CFrame = HRP.CFrame
                    elseif Option == "Grinder" then
                        c.CFrame = workspace.Map.Campground.Scrapper.Movers.Right.GrindersRight.CFrame * CFrame.new(0,35,0)
                    end
                end
            end
        end
    end
})
Tab2:Divider()
local Section = Tab2:Section({Title = "Heal items",})
local Dropdown = Tab2:Dropdown({
    Title = "Heal items Schedule",
    Values = { "Bandage", "Medkit" },
    Value = "...",
    Callback = function(option)
        G = option
    end
})
local Button = Tab2:Button({
    Title = "Bring Item",
    Locked = false,
    Callback = function()
        for i,v in pairs(Item:GetChildren()) do
            if v.Name == G then
                for i,c in pairs(v:GetChildren()) do
                    if not c.CFrame then return end
                    if Option == "Campfire" then
                        c.CFrame = CFrame.new(1.62860501, 11.7039776, 0.2124511, -0.786170661, 5.61900073e-08, -0.618009448, 9.28167125e-08, 1, -2.71513123e-08, 0.618009448, -7.8707167e-08, -0.786170661) * CFrame.new(0,35,0)
                    elseif Option == "Player" then
                        c.CFrame = HRP.CFrame
                    elseif Option == "Grinder" then
                        c.CFrame = workspace.Map.Campground.Scrapper.Movers.Right.GrindersRight.CFrame * CFrame.new(0,35,0)
                    end
                end
            end
        end
    end
})
Tab2:Divider()
local Section = Tab2:Section({Title = "Tools & Kits",})
local Dropdown = Tab2:Dropdown({
    Title = "Tools & Kits Schedule",
    Values = { "Good Sack", "Infernal Sack", "Giant Sack", "Good Axe", "Ice Axe", "Strong Axe", "Chainsaw", "Admin Axe", "Old Taming Flute", "Strong Flashlight", "Spear", "Morningstar", "Laser Sword", "Ice Sword", "Trident", "Poison Spear", "Infernal Sword", "Cultist King Mace", "Obsidiron Hammer", "Leather Body", "Poison Body", "Iron Body", "Thorn Body", "Riot Shield", "Alien Armor", "Obsidiron Body" },
    Value = "...",
    Callback = function(option)
        G = option
    end
})
local Button = Tab2:Button({
    Title = "Bring Item",
    Locked = false,
    Callback = function()
        for i,v in pairs(Item:GetChildren()) do
            if v.Name == G then
                for i,c in pairs(v:GetChildren()) do
                    if not c.CFrame then return end
                    if Option == "Campfire" then
                        c.CFrame = CFrame.new(1.62860501, 11.7039776, 0.2124511, -0.786170661, 5.61900073e-08, -0.618009448, 9.28167125e-08, 1, -2.71513123e-08, 0.618009448, -7.8707167e-08, -0.786170661) * CFrame.new(0,35,0)
                    elseif Option == "Player" then
                        c.CFrame = HRP.CFrame
                    elseif Option == "Grinder" then
                        c.CFrame = workspace.Map.Campground.Scrapper.Movers.Right.GrindersRight.CFrame * CFrame.new(0,35,0)
                    end
                end
            end
        end
    end
})
Tab2:Divider()
local Section = Tab2:Section({Title = "Miscs",})
local Dropdown = Tab2:Dropdown({
    Title = "Miscs Schedule",
    Values = { "Defense Blueprint", "Furniture Blueprint", "Obsidiron Chest Blueprint", "Bunny Foot", "Wolf Pelt", "Alpha Wolf Pelt", "Bear Pelt", "Arctic Fox Pelt", "Polar Bear Pelt", "Mammoth Tusk", "Scorpion Shell", "Cultist King Antler"},
    Value = "...",
    Callback = function(option)
        G = option
    end
})
local Button = Tab2:Button({
    Title = "Bring Item",
    Locked = false,
    Callback = function()
        for i,v in pairs(Item:GetChildren()) do
            if v.Name == G then
                for i,c in pairs(v:GetChildren()) do
                    if not c.CFrame then return end
                    if Option == "Campfire" then
                        c.CFrame = CFrame.new(1.62860501, 11.7039776, 0.2124511, -0.786170661, 5.61900073e-08, -0.618009448, 9.28167125e-08, 1, -2.71513123e-08, 0.618009448, -7.8707167e-08, -0.786170661) * CFrame.new(0,35,0)
                    elseif Option == "Player" then
                        c.CFrame = HRP.CFrame
                    elseif Option == "Grinder" then
                        c.CFrame = workspace.Map.Campground.Scrapper.Movers.Right.GrindersRight.CFrame * CFrame.new(0,35,0)
                    end
                end
            end
        end
    end
})
local Tab3 = Window:Tab({
    Title = "Auto Quest & Smth",
    Icon = "drill", -- optional
    Locked = false,
})
local Tab4 = Window:Tab({
    Title = "Teleport",
    Icon = "eye", -- optional
    Locked = false,
})
local Tab5 = Window:Tab({
    Title = "Player",
    Icon = "user", -- optional
    Locked = false,
})
local Tab6 = Window:Tab({
    Title = "Misc",
    Icon = "ellipsis", -- optional
    Locked = false,
})
local Section = Tab6:Section({Title = "Helper"})
local Toggle = Tab6:Toggle({
    Title = "",
    Desc = "Toggle Description",
    Icon = "bird",
    Type = "Toggle",
    Default = false,
    Callback = function(state) 
        if state then
            for i,v in pairs(Item:GetDescendants()) do
                if v.ClassName == "Proximityprompt" then
                    v.HoldDuration = 0
                end
            end
        end
    end
})
Window:Divider()
local Tabs = Window:Tab({
    Title = "Setting & Config",
    Icon = "cog", -- optional
    Locked = false,
})
