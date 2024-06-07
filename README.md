local Library = loadstring(game:HttpGet("https://pastebin.com/raw/KNBp0LRy"), "Coastified UI")()
local Window = Library:NewWindow("Royal Seas")

local Section = Window:NewSection("AutoFarm")

local PlayerTP1
local TweenService = game:GetService("TweenService")

local Dropdown = Section:CreateDropdown("Select Mobs!", {"Bandit", "Monkey", "DesertBandit", "SkyNewbie"}, 0, function(t)
    PlayerTP1 = t
end)
local Dropdown = Section:CreateDropdown("Select Boss!", {"Buggy", "GorillaKing", "SandBoss", "SkyElite", "StrongBandit"}, 0, function(t)
    PlayerTP1 = t
end)

local Toggle = Section:CreateToggle("Auto [Farm/Lv]", function(Value)
_G.Hit = Value
while _G.Hit do
wait(1)  -- Wait for 1 second before checking for enemies
pcall(function()
for i,v in pairs(workspace:GetDescendants()) do
if v.Name == PlayerTP1 then
if v.Humanoid.Health > 0 then
repeat
    local toolName = "Combat" -- Replace "YourToolNameHere" with the name of your tool
    local LocalPlayer = game:GetService("Players").LocalPlayer
    for i, v in pairs(LocalPlayer.Backpack:GetChildren()) do
    if v:IsA('Tool') and v.Name == toolName then
    v.Parent = LocalPlayer.Character
    break -- Stop the loop after picking up the tool
    end
    end
    LocalPlayer.Character:FindFirstChild(toolName):Activate()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,5)
wait()  -- Wait a short time before checking again
until not _G.Hit or v.Humanoid.Health <= 0
end
end
end
end)
local Player = game.Players.LocalPlayer
local function onCharacterAdded(character)
    character.Archivable = false
    character:WaitForChild("HumanoidRootPart").Anchored = false
    if Player.Character then
            onCharacterAdded(Player.Character)
    end
end
    
Player.CharacterAdded:Connect(onCharacterAdded)
end
end)
local Section = Window:NewSection("Stats")
local Toggle = Section:CreateToggle("Auto [Strength]", function(Value)
_G.Strength = Value
while _G.Strength do
wait(0.1)  -- Wait for 1 second before checking for enemies
local args = {
    [1] = "Strength"
    }
    
    game:GetService("ReplicatedStorage"):WaitForChild("StatSystem"):WaitForChild("Points"):FireServer(unpack(args))	
end
end)
local Toggle = Section:CreateToggle("Auto [Defense]", function(Value)
_G.Defense = Value
while _G.Defense do
wait(0.1)  -- Wait for 1 second before checking for enemies
local args = {
    [1] = "Defense"
    }
    
    game:GetService("ReplicatedStorage"):WaitForChild("StatSystem"):WaitForChild("Points"):FireServer(unpack(args))	
end
end)
local Toggle = Section:CreateToggle("Auto [Weapon]", function(Value)
_G.Weapon = Value
while _G.Weapon do
wait(0.1)  -- Wait for 1 second before checking for enemies
local args = {
    [1] = "Weapon"
    }
    
    game:GetService("ReplicatedStorage"):WaitForChild("StatSystem"):WaitForChild("Points"):FireServer(unpack(args))	
end
end)
local Toggle = Section:CreateToggle("Auto [Royal]", function(Value)
_G.Royal = Value
while _G.Royal do
wait(0.1)  -- Wait for 1 second before checking for enemies
local args = {
    [1] = "Royal"
    }
    
    game:GetService("ReplicatedStorage"):WaitForChild("StatSystem"):WaitForChild("Points"):FireServer(unpack(args))	
end
end)
local Section = Window:NewSection("NPC")
local Dropdown = Section:CreateDropdown("Select Mobs!", {"DualKatanaSeller", "KatanaSeller", "RandomRace", "RandomRoyal", "SukunaSeller", "TripleKatanaSeller"}, 0, function(i)
    PlayerTP3 = i
end)
local Button = Section:CreateButton("Tp", function()
    for i,v in pairs(workspace.NPCS[PlayerTP3]:GetDescendants()) do
        if v.Name == "Head" then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
    end
end
end)
local Section = Window:NewSection("Island")
local Dropdown = Section:CreateDropdown("Select Mobs!", {"StarterIsland", "SkyIsland", "OrangeTown", "MonkeyIsland", "DesertIsland", "CursedIsland"}, 0, function(s)
    PlayerTP4 = s
end)
local Button = Section:CreateButton("Tp", function()
    getgenv().Player = game:GetService("Players").LocalPlayer
    Player.Character.HumanoidRootPart.CFrame = workspace.Safes_Zones[PlayerTP4].CFrame
end)
