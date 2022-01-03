local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/GreenDeno/Venyx-UI-Library/main/source.lua"))()
local venyx = library.new("PREM X HENG | AUTO FARM", 5013109572)
 
 
function Redeem(Code)
local args = {
    [1] = Code
}
game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(unpack(args))
end
 
local Code = {
    "3BVISITS",
    "UPD16",
    "THEGREATACE",
    "SUB2GAMERROBOT_EXP1",
    "StrawHatMaine",
    "Sub2OfficialNoobie",
    "SUB2NOOBMASTER123",
    "Sub2Daigrock",
    "Axiore",
    "TantaiGaming",
    "STRAWHATMAINE"
}
 
 
local Main = venyx:addPage("Main", 5012544693)
local AutoFarm = Main:addSection("AutoFarm")
local WeaponSection = Main:addSection("Weapon")
local StatsPage = venyx:addPage("Stats", 5012544693)
local Statselection = StatsPage:addSection("Auto Stats")
local theme = venyx:addPage("Config", 5012544693)
local colors = theme:addSection("Colors")
local setting = theme:addSection("Setting")
 
AutoFarm:addToggle("Auto Farm Level", nil, function(value)
    _G.AutoFarm_Level = value
    for i,v in pairs(Code) do
        Redeem(v)
    end
end)
 
AutoFarm:addToggle("Fast attack", nil, function(value)
    _G.FastAttack = value
end)
 
local WeaponTable = {}
 
for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
    if v:IsA("Tool") then
        table.insert(WeaponTable,v.Name)
    end
end
 
for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
    if v:IsA("Tool") then
        table.insert(WeaponTable,v.Name)
    end
end
 
WeaponSection:addDropdown("Select Weapon", WeaponTable, function(text)
    _G.WeaponSelected = text
end)
 
WeaponSection:addToggle("Auto Equip", nil, function(value)
    _G.AutoEquieTool = value
end)
 
spawn(function()
    while wait() do
        if _G.AutoEquieTool then
            pcall(function()
                wait(1)
                game.Players.LocalPlayer.Character.Humanoid:EquipTool(game.Players.LocalPlayer.Backpack:FindFirstChild(_G.WeaponSelected))
            end)
        end
    end
end)
 
 
if _G.PointUp == nil then
   _G.PointUp = 3 
end
 
Statselection:addToggle("Melee", nil, function(value)
    _G.StatsUp_Melee = value
end)
 
 
Statselection:addSlider("Point", _G.PointUp, 1, 100, function(value)
    _G.PointUp = value
end)
 
 
 
spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
        if  _G.StatsUp_Melee then
            local args = {
                [1] = "AddPoint",
                [2] = "Melee",
                [3] = _G.PointUp
            }
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
        end
    end)
end)
 
 
 
 
 
 
 
local themes = {
    Background = Color3.fromRGB(24, 24, 24),
    Glow = Color3.fromRGB(0, 0, 0),
    Accent = Color3.fromRGB(10, 10, 10),
    LightContrast = Color3.fromRGB(20, 20, 20),
    DarkContrast = Color3.fromRGB(14, 14, 14),  
    TextColor = Color3.fromRGB(255, 255, 255)
}
 
setting:addKeybind("Toggle UI", Enum.KeyCode.RightControl, function()
    venyx:toggle()
end)
 
for theme, color in pairs(themes) do
colors:addColorPicker(theme, color, function(color3)
venyx:setTheme(theme, color3)
end)
end
 
 
venyx:SelectPage(venyx.pages[1], true)
 
 
 
 
 
 
 
 
 
 
 
 
--------------------------------------
 
 
 
 
function checklevel()
    local Level = game:GetService("Players").LocalPlayer.Data.Level.Value
    if Level == 1 or Level <= 9 then
        MON = "Bandit [Lv. 5]"
        QUESTTITLE = "Bandit"
        QUESTPOS = CFrame.new(1060.0158691406, 16.424287796021, 1547.9769287109)
        MONPOS = CFrame.new(1148.8698730469, 16.432844161987, 1630.5396728516)
        QUESTNAME = "BanditQuest1"
        QUESTNUMBER = 1
        SPAWNPOINT = "Default"
        SPAWNPOINTPOS = CFrame.new(973.96197509766, 16.273551940918, 1413.2775878906)
    elseif Level == 10 or Level <= 14 then
        MON = "Monkey [Lv. 14]"
        QUESTTITLE = "Monkey"
        QUESTPOS = CFrame.new(-1599, 37, 154)
        MONPOS = CFrame.new(-1616, 37, 145)
        QUESTNAME = "JungleQuest"
        QUESTNUMBER = 1
        SPAWNPOINT = "Jungle"
        SPAWNPOINTPOS = CFrame.new(-1337, 12, 498)
    elseif Level == 15 or Level <= 29 then
        MON = "Gorilla [Lv. 20]"
        QUESTTITLE = "Gorilla"
        QUESTPOS = CFrame.new(-1599, 37, 154)
        MONPOS = CFrame.new(-1322, 82, -458)
        QUESTNAME = "JungleQuest"
        QUESTNUMBER = 2
        SPAWNPOINT = "Jungle"
        SPAWNPOINTPOS = CFrame.new(-1337, 12, 498)
    end
end
Method = CFrame.new(0,25,0)
 
spawn(function()
   while wait(3) do
       if Methodnow == 1 then
        Methodnow = 2
        Method = CFrame.new(0,25,0)
        else
        Methodnow = 1
        Method = CFrame.new(0,0,25)
       end
    end
end)
 
spawn(function()
   while wait() do
       if _G.WARP then
           game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
        else
            game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
        end
    end
end)
 
spawn(function()
   while wait(1.5) do
       if _G.AutoFarm_Level then
           if _G.WARP then
               _G.WARP = false
            else
                _G.WARP = true
            end
        end
    end
end)
 
 
spawn(function()
   while wait() do
       if not _G.AutoFarm_Level then
            game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
        end
    end
end)
 
 
spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function()
        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid") and _G.AutoFarm_Level then
            setfflag("HumanoidParallelRemoveNoPhysics", "False")
            setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
            game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
end)
 
 
spawn(function()
    while wait() do
        if _G.AutoFarm_Level then
            pcall(function()
                checklevel()
    
                if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,QUESTTITLE) then
                    local args = {
                        [1] = "AbandonQuest"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                    
                    if game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT then
                        local args = {
                            [1] = "SetTeam",
                            [2] = "Pirates"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        wait(0.5)
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = QUESTPOS
                        wait(0.8)
                            local args = {
                                [1] = "StartQuest",
                                [2] = QUESTNAME,
                                [3] = QUESTNUMBER
                            }
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        wait(0.8)
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = MONPOS
                    else
                        _G.WARP = true
                        repeat
                            wait()
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = SPAWNPOINTPOS
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT or _G.AutoFarm_Level == false
                        game.Players.LocalPlayer.Character.Humanoid.Health = 0
                        wait(5)
                        _G.WARP = false
                    end
                end
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    for i2,v2 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == MON and v2.Name == MON then
                            v2.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                            v2.HumanoidRootPart.CanCollide = false
                            v2.Humanoid:ChangeState(11)
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * Method
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        end
                    end
                end
            end)
        end
    end
end)
 
 
 
spawn(function()
   game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        if _G.FastAttack and _G.AutoFarm_Level then
            local Combat = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
            local Cemara = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
            Cemara.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}
            Combat.activeController.timeToNextAttack = 0
            Combat.activeController.hitboxMagnitude = 120
            Combat.activeController.increment = 3
        end
    end)
end) 
end)
 
 
spawn(function()
   game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        if _G.AutoFarm_Level then
            local Combat = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
            local Cemara = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
            Cemara.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}
            Combat.activeController.hitboxMagnitude = 120
            Combat.activeController.increment = 3
            game:GetService'VirtualUser':CaptureController()
            game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
        end
    end)
end) 
end)
