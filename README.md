local Fun = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/nightmares.fun-UI-Library/main/source.lua"))()

local window = Fun.Create("Axafy Free")

local tab = window:Tab("Main")

local section = tab:Section("Discord Link")

section:Label("user 1yyz")

local tab = window:Tab("Visuals")


local section = tab:Section("Esp Rainbow Corner")

section:Button("Execute", function()local notificationLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/laagginq/ui-libraries/main/xaxas-notification/src.lua"))();
local notifications = notificationLibrary.new({            
    NotificationLifetime = 3, 
    NotificationPosition = "Middle",
    
    TextFont = Enum.Font.Code,
    TextColor = Color3.fromRGB(255, 255, 255),
    TextSize = 15,
    
    TextStrokeTransparency = 0, 
    TextStrokeColor = Color3.fromRGB(0, 0, 0)
});

notifications:BuildNotificationUI();
notifications:Notify("1yyz ESP");

local Settings = {
    Box_Color = Color3.fromRGB(255, 0, 0),
    Box_Thickness = 2,
    Team_Check = false,
    Team_Color = false,
    Autothickness = true
}

--Locals
local Space = game:GetService("Workspace")
local Player = game:GetService("Players").LocalPlayer
local Camera = Space.CurrentCamera

-- Locals
local function NewLine(color, thickness)
    local line = Drawing.new("Line")
    line.Visible = false
    line.From = Vector2.new(0, 0)
    line.To = Vector2.new(0, 0)
    line.Color = color
    line.Thickness = thickness
    line.Transparency = 1
    return line
end

local function Vis(lib, state)
    for i, v in pairs(lib) do
        v.Visible = state
    end
end

local function Colorize(lib, color)
    for i, v in pairs(lib) do
        v.Color = color
    end
end

local Black = Color3.fromRGB(0, 0, 0)

local function Rainbow(lib, delay)
    for hue = 0, 1, 1/30 do
        local color = Color3.fromHSV(hue, 0.6, 1)
        Colorize(lib, color)
        wait(delay)
    end
    Rainbow(lib)
end
--Main Draw Function
local function Main(plr)
    repeat wait() until plr.Character ~= nil and plr.Character:FindFirstChild("Humanoid") ~= nil
    local R15
    if plr.Character.Humanoid.RigType == Enum.HumanoidRigType.R15 then
        R15 = true
    else 
        R15 = false
    end
    local Library = {
        TL1 = NewLine(Settings.Box_Color, Settings.Box_Thickness),
        TL2 = NewLine(Settings.Box_Color, Settings.Box_Thickness),

        TR1 = NewLine(Settings.Box_Color, Settings.Box_Thickness),
        TR2 = NewLine(Settings.Box_Color, Settings.Box_Thickness),

        BL1 = NewLine(Settings.Box_Color, Settings.Box_Thickness),
        BL2 = NewLine(Settings.Box_Color, Settings.Box_Thickness),

        BR1 = NewLine(Settings.Box_Color, Settings.Box_Thickness),
        BR2 = NewLine(Settings.Box_Color, Settings.Box_Thickness)
    }
    coroutine.wrap(Rainbow)(Library, 0.15)
    local oripart = Instance.new("Part")
    oripart.Parent = Space
    oripart.Transparency = 1
    oripart.CanCollide = false
    oripart.Size = Vector3.new(1, 1, 1)
    oripart.Position = Vector3.new(0, 0, 0)
    --Updater Loop
    local function Updater()
        local c 
        c = game:GetService("RunService").RenderStepped:Connect(function()
            if plr.Character ~= nil and plr.Character:FindFirstChild("Humanoid") ~= nil and plr.Character:FindFirstChild("HumanoidRootPart") ~= nil and plr.Character.Humanoid.Health > 0 and plr.Character:FindFirstChild("Head") ~= nil then
                local Hum = plr.Character
                local HumPos, vis = Camera:WorldToViewportPoint(Hum.HumanoidRootPart.Position)
                if vis then
                    oripart.Size = Vector3.new(Hum.HumanoidRootPart.Size.X, Hum.HumanoidRootPart.Size.Y*1.5, Hum.HumanoidRootPart.Size.Z)
                    oripart.CFrame = CFrame.new(Hum.HumanoidRootPart.CFrame.Position, Camera.CFrame.Position)
                    local SizeX = oripart.Size.X
                    local SizeY = oripart.Size.Y
                    local TL = Camera:WorldToViewportPoint((oripart.CFrame * CFrame.new(SizeX, SizeY, 0)).p)
                    local TR = Camera:WorldToViewportPoint((oripart.CFrame * CFrame.new(-SizeX, SizeY, 0)).p)
                    local BL = Camera:WorldToViewportPoint((oripart.CFrame * CFrame.new(SizeX, -SizeY, 0)).p)
                    local BR = Camera:WorldToViewportPoint((oripart.CFrame * CFrame.new(-SizeX, -SizeY, 0)).p)

                    if Settings.Team_Check then
                        if plr.TeamColor == Player.TeamColor then
                            Colorize(Library, Color3.fromRGB(0, 255, 0))
                        else 
                            Colorize(Library, Color3.fromRGB(255, 0, 0))
                        end
                    end

                    if Settings.Team_Color then
                        Colorize(Library, plr.TeamColor.Color)
                    end

                    local ratio = (Camera.CFrame.p - Hum.HumanoidRootPart.Position).magnitude
                    local offset = math.clamp(1/ratio*750, 2, 300)

                    Library.TL1.From = Vector2.new(TL.X, TL.Y)
                    Library.TL1.To = Vector2.new(TL.X + offset, TL.Y)
                    Library.TL2.From = Vector2.new(TL.X, TL.Y)
                    Library.TL2.To = Vector2.new(TL.X, TL.Y + offset)

                    Library.TR1.From = Vector2.new(TR.X, TR.Y)
                    Library.TR1.To = Vector2.new(TR.X - offset, TR.Y)
                    Library.TR2.From = Vector2.new(TR.X, TR.Y)
                    Library.TR2.To = Vector2.new(TR.X, TR.Y + offset)

                    Library.BL1.From = Vector2.new(BL.X, BL.Y)
                    Library.BL1.To = Vector2.new(BL.X + offset, BL.Y)
                    Library.BL2.From = Vector2.new(BL.X, BL.Y)
                    Library.BL2.To = Vector2.new(BL.X, BL.Y - offset)

                    Library.BR1.From = Vector2.new(BR.X, BR.Y)
                    Library.BR1.To = Vector2.new(BR.X - offset, BR.Y)
                    Library.BR2.From = Vector2.new(BR.X, BR.Y)
                    Library.BR2.To = Vector2.new(BR.X, BR.Y - offset)

                    Vis(Library, true)

                    if Settings.Autothickness then
                        local distance = (Player.Character.HumanoidRootPart.Position - oripart.Position).magnitude
                        local value = math.clamp(1/distance*100, 1, 4) --0.1 is min thickness, 6 is max
                        for u, x in pairs(Library) do
                            x.Thickness = value
                        end
                    else 
                        for u, x in pairs(Library) do
                            x.Thickness = Settings.Box_Thickness
                        end
                    end
                else 
                    Vis(Library, false)
                end
            else 
                Vis(Library, false)
                if game:GetService("Players"):FindFirstChild(plr.Name) == nil then
                    for i, v in pairs(Library) do
                        v:Remove()
                        oripart:Destroy()
                    end
                    c:Disconnect()
                end
            end
        end)
    end
    coroutine.wrap(Updater)()
end

-- Draw Boxes
for i, v in pairs(game:GetService("Players"):GetPlayers()) do
    if v.Name ~= Player.Name then
      coroutine.wrap(Main)(v)
    end
end

game:GetService("Players").PlayerAdded:Connect(function(newplr)
    coroutine.wrap(Main)(newplr)
end)
end)

local section = tab:Section("rainbow character")

section:Button("Execute", function()for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
    if v:IsA("MeshPart") then
        v.Material = "ForceField"
        spawn(function()
            while wait() do
                for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
                    if v:IsA("MeshPart") then
                        v.Color = Color3.fromHSV(tick()%5/5,1,1)
                        wait()
                    end
                end 
            end
        end)
    end
end
end)

local section = tab:Section("strech res")

section:Button("Execute", function()getgenv().Resolution = {
    [".gg/scripters"] = 0.65
}

local Camera = workspace.CurrentCamera
if getgenv().gg_scripters == nil then
    game:GetService("RunService").RenderStepped:Connect(
        function()
            Camera.CFrame = Camera.CFrame * CFrame.new(0, 0, 0, 1, 0, 0, 0, getgenv().Resolution[".gg/scripters"], 0, 0, 0, 1)
        end
    )
end
getgenv().gg_scripters = "g5s"
end)

local section = tab:Section("auto reload")

section:Button("Execute", function()_G.AutoReload = true -- change to false if u don't want it anymore.

while _G.AutoReload == true and game:GetService("RunService").Heartbeat:Wait() do
if game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool") then
            if game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool"):FindFirstChild("Ammo") then
                if game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool"):FindFirstChild("Ammo").Value <= 0 then
                    game:GetService("ReplicatedStorage").MainEvent:FireServer("Reload", game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool")) 
                    wait(1)
                end
            end
        end
end
end)

local tab = window:Tab("universal hubs")

local section = tab:Section("scripthub")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/scripthubekitten/SCRIPTHUBV3/main/SCRIPTHUBV3", true))()
end)

local tab = window:Tab("Da Hood Mobile")

local section = tab:Section("Whim Camlock")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Aepione/Whimsical.cc-gui/refs/heads/main/V8"))()
   
end)

local section = tab:Section("Mob Cam")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/k0nkx/Aura-x-skid-ez-remake-by-k0nkx/main/Sigma"))()
   
end)

local section = tab:Section("phyx")

section:Button("Execute", function()getgenv().phyx_target = {
    ["Main"] = {
       ["Prediction"] = 0.140,
       ["Partz"] = "UpperTorso",
       ["Air Delay"] = 0.12, -- // this is NOT an prediction, don't mess with it if you don't know how to.
       ["AutoPred"] = true,
       ["Dot"] = true,
       ["No Floor Shots"] = true,
       ["Pred Increase"] = false
    },
    ["Aim Assist"] = {
       ["Cam Enabled"] = true,
       ["Partz"] = "UpperTorso",
       ["Use Smoothness"] = true,
       ["Smoothness Value"] = 2
    },
    ["GUIs"] = {
       ["Save Position"] = true,
       ["Auto Air"] = true,
       ["Buy Items"] = true, -- // Only works on VFS games
       ["Reset"] = true,
       ["Leave"] = false,
       ["Trigger Bot"] = { true, delay = 5.5 }, -- // under maintenance
       ["Macro"] = { true, type = "Legit" } -- // Can be: "Legit" , "Speed" , "CFrame".
    }
}

loadstring(game:HttpGet("https://raw.githubusercontent.com/plah911/phyx/refs/heads/main/betaphyx"))()
end)

local section = tab:Section("trust.lua")
section:Button("Execute", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/Mc4121ban/skidscript/refs/heads/main/trust.lua"))()
end)

local section = tab:Section("polos")

section:Button("Execute", function()loadstring(game:HttpGet("https://pastebin.com/raw/EFvQ5hDw",true))()
end)

local section = tab:Section("psalms lock")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Mc4121ban/skidscript/refs/heads/main/Psalms%20Texh%20(Sentinal.CC%20Rewrite).lua"))()
end)

local section = tab:Section("polos")

section:Button("Execute", function()loadstring(game:HttpGet("https://pastebin.com/raw/EFvQ5hDw",true))()
end)

local section = tab:Section("josh camlock")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/DudesAimer/JOSHZZ.VERSION2OPCAMLOCK/refs/heads/main/OPJOSHZZCAMLOCK"))()
end)

local section = tab:Section("lolxd")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/yoitsyamans/takedatrisklillll/refs/heads/main/lol.xd"))()
end)


local section = tab:Section("aim assist")

section:Button("Execute", function()getgenv().RecurringPoint = "UpperTorso"
getgenv().Hitbox = "UpperTorso"
getgenv().Keybind = "e"
getgenv().AimbotStrengthAmount = 0.0335
getgenv().PredictionAmount = 10
getgenv().Radius = 25
getgenv().UsePrediction = true
getgenv().AimbotStrength = true
getgenv().FirstPerson = true
getgenv().ThirdPerson = true
getgenv().TeamCheck = false
getgenv().Enabled = true


-- // main script use with silent aim / / -- 

loadstring(game:HttpGet("https://raw.githubusercontent.com/tenaaki/GenericAimbot/main/v1.0.0"))()
end)

local tab = window:Tab("Da Hood Pc")

local section = tab:Section("Howl (c)")

section:Button("Execute", function()getgenv().Howl = {
    Aimbot = {
        Keybind = Enum.KeyCode.C,
        AimBotSkid = 0.187,
        Prediction = 0.1247724521,

        ShakeEnabled = false,
        Shake = 0,
        
        Amount = 0.160145,
        Style = "Back",
        Direction = "Inout",

        TargetPart = "HumanoidRootPart",
    
    },
    ['HitBox'] = {
        Part = "HumanoidRootPart",
    },
    ['Resolver'] = {
        Enabled = true,
    },
    ['Silent'] = {
        Prediction = 0.1279,
        Detection = {Close = 27, Mid = 38, Far = math.huge},
    },
    ['SpecificDis'] = {
        Enabled = true,
        Prediction = {
            Close = 0.116243115666,
            Mid = 0.1188237,
            Far = 0.1224451,
        },
    },
    ['OffSets'] = {
        Jump = {Amount = 0.90},
        Fall = {Amount = -1.50},
    },  
    ['FieldOfView'] = {
        Enabled = false,
        Size = 240,
        Color = Color3.fromRGB(255, 255, 255),
        Transparency = 1,
        Filled = false,
    },
    ['Air'] = {
        Enabled = true,
        AirPart = "Head",
    },
    ['Checks'] = {
        TargetDeath = true,
        PlayerDeath = true,
        PlayerDeath = true,
    },
    
    ['Macro'] = {
        Enabled = false,
        Keybind = "x",
        Speed = 0.0200,
        Type = "Third", -- "First", "Third"
    },
    
    ['Spin'] = {
        Enabled = true,
        SpinSpeed = 4900,
        Degrees = 360,
        Keybind = Enum.KeyCode.V,
    },
}



if (not getgenv().Loaded) then
local userInputService = game:GetService("UserInputService")

local function CheckAnti(Plr) -- // Anti-aim detection
    if Plr.Character.HumanoidRootPart.Velocity.Y < -70 then
        return true
    elseif Plr and (Plr.Character.HumanoidRootPart.Velocity.X > 450 or Plr.Character.HumanoidRootPart.Velocity.X < -35) then
        return true
    elseif Plr and Plr.Character.HumanoidRootPart.Velocity.Y > 60 then
        return true
    elseif Plr and (Plr.Character.HumanoidRootPart.Velocity.Z > 35 or Plr.Character.HumanoidRootPart.Velocity.Z < -35) then
        return true
    else
        return false
    end
end

local function getnamecall()
     if game.PlaceId == 2788229376 or game.PlaceId == 7213786345 or game.PlaceId == 16033173781 or game.PlaceId == 16158576873 then 
        return "UpdateMousePosI"
    elseif game.PlaceId == 5602055394 or game.PlaceId == 7951883376 then
        return "MousePos"
    elseif game.PlaceId == 9825515356 then
        return "GetMousePos"
    end
end

function MainEventLocate()
    for _,v in pairs(game:GetService("ReplicatedStorage"):GetDescendants()) do
        if v.Name == "MainEvent" then
            return v
        end
    end
end

local Locking = false
local Players = game:GetService("Players")
local Client = Players.LocalPlayer
local Plr = nil -- Initialize Plr here

-- 360 on bind
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local Camera = workspace.CurrentCamera
local Toggle = false -- Initialize Toggle to false

local function OnKeyPress(Input, GameProcessedEvent)
    if Input.KeyCode == getgenv().Howl.Aimbot.Keybind and not GameProcessedEvent then 
        Toggle = not Toggle
    elseif Input.KeyCode == getgenv().Howl.Macro.SpeedGlitchKey then
        if getgenv().Howl.Macro.Enabled then 
            getgenv().Howl.Macro.SpeedGlitch = not getgenv().Howl.Macro.SpeedGlitch
            if getgenv().Howl.Macro.SpeedGlitch then
                repeat
                    game:GetService("RunService").Heartbeat:Wait()
                    keypress(0x49)
                    game:GetService("RunService").Heartbeat:Wait()
                    keypress(0x4F)
                    game:GetService("RunService").Heartbeat:Wait()
                    keyrelease(0x49)
                    game:GetService("RunService").Heartbeat:Wait()
                    keyrelease(0x4F)
                    game:GetService("RunService").Heartbeat:Wait()
                until not getgenv().Howl.Macro.SpeedGlitch
            end
        end
    end
end

UserInputService.InputBegan:Connect(OnKeyPress)

UserInputService.InputBegan:Connect(function(keygo, ok)
    if (not ok) then
        if (keygo.KeyCode == getgenv().Howl.Aimbot.Keybind) then
            Locking = not Locking
            if Locking then
                Plr = getClosestPlayerToCursor()
            elseif not Locking then
                if Plr then
                    Plr = nil
                end
            end
        end
    end
end)

function getClosestPlayerToCursor()
    local closestDist = math.huge
    local closestPlr = nil
    for _, v in ipairs(Players:GetPlayers()) do
        if v ~= Client and v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health > 0 then
            local screenPos, cameraVisible = workspace.CurrentCamera:WorldToViewportPoint(v.Character.HumanoidRootPart.Position)
            if cameraVisible then
                local distToMouse = (Vector2.new(UserInputService:GetMouseLocation().X, UserInputService:GetMouseLocation().Y) - Vector2.new(screenPos.X, screenPos.Y)).Magnitude
                if distToMouse < closestDist then
                    closestPlr = v
                    closestDist = distToMouse
                end
            end
        end
    end
    return closestPlr
end

function getClosestPartToCursor(Player)
    local closestPart, closestDist = nil, math.huge
    if Player.Character and Player.Character:FindFirstChild("Humanoid") and Player.Character:FindFirstChild("Head") and Player.Character.Humanoid.Health ~= 0 and Player.Character:FindFirstChild("HumanoidRootPart") then
        for i, part in pairs(Player.Character:GetChildren()) do
            if part:IsA("BasePart") then
                local screenPos, cameraVisible = workspace.CurrentCamera:WorldToViewportPoint(part.Position)
                local distToMouse = (Vector2.new(UserInputService:GetMouseLocation().X, UserInputService:GetMouseLocation().Y) - Vector2.new(screenPos.X, screenPos.Y)).Magnitude
                if distToMouse < closestDist and table.find(getgenv().Howl.Aimbot.MultipleTargetPart, part.Name) then
                    closestPart = part
                    closestDist = distToMouse
                end
            end
        end
        return closestPart
    end
end

game:GetService("RunService").RenderStepped:Connect(function()
    if Plr and Plr.Character then
        if getgenv().Howl.Aimbot.NearestPart == true and getgenv().Howl.Aimbot.Basic == false then
            getgenv().Howl.Aimbot.TargetPart = tostring(getClosestPartToCursor(Plr))
        elseif getgenv().Howl.Aimbot.Basic == true and getgenv().Howl.Aimbot.NearestPart == false then
            getgenv().Howl.Aimbot.TargetPart = getgenv().Howl.Aimbot.TargetPart
        end
    end
end)

local function getVelocity(Player)
    local Old = Player.Character.HumanoidRootPart.Position
    wait(0.145)
    local Current = Player.Character.HumanoidRootPart.Position
    return (Current - Old) / 0.145
end

local function GetShakedVector3(Setting)
    return Vector3.new(math.random(-Setting * 1e9, Setting * 1e9), math.random(-Setting * 1e9, Setting * 1e9), math.random(-Setting * 1e9, Setting * 1e9)) / 1e9;
end

local v = nil
game:GetService("RunService").Heartbeat:Connect(function(deltaTime)
    if Plr ~= nil and Plr.Character and Plr.Character:FindFirstChild("HumanoidRootPart") then
        v = getVelocity(Plr)
    end
end)

local mainevent = game:GetService("ReplicatedStorage").MainEvent

Client.Character.ChildAdded:Connect(function(child)
    if child:IsA("Tool") and child:FindFirstChild("MaxAmmo") then
        child.Activated:Connect(function()
            if Plr and Plr.Character then
                local Position = Plr.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall and Plr.Character[getgenv().Howl.Aimbot.TargetPart].Position + Vector3.new(0, getgenv().Howl.Aimbot.JumpOffset, 0) or Plr.Character[getgenv().Howl.Aimbot.TargetPart].Position
                if game.PlaceId == 2788229376 or game.PlaceId == 7213786345 or game.PlaceId == 16033173781 or game.PlaceId == 16158576873 then 
                    mainevent:FireServer("UpdateMousePosI", Position + ((Plr.Character.HumanoidRootPart.Velocity) * getgenv().Howl.Aimbot.Prediction))
                else
                    mainevent:FireServer("UpdateMousePos", Position + ((Plr.Character.Humanoid.MoveDirection * Plr.Character.Humanoid.WalkSpeed) * getgenv().Howl.Aimbot.Prediction))
                end
            end
        end)
    end
end)

Client.CharacterAdded:Connect(function(character)
    character.ChildAdded:Connect(function(child)
        if child:IsA("Tool") and child:FindFirstChild("MaxAmmo") then
            child.Activated:Connect(function()
                if Plr and Plr.Character then
                    local Position = Plr.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall and Plr.Character[getgenv().Howl.Aimbot.TargetPart].Position + Vector3.new(0, getgenv().Howl.Aimbot.JumpOffset, 0) or Plr.Character[getgenv().Howl.Aimbot.TargetPart].Position
                    if game.PlaceId == 2788229376 or game.PlaceId == 7213786345 or game.PlaceId == 16033173781 or game.PlaceId == 16158576873 then 
                        mainevent:FireServer("UpdateMousePosI", Position + ((Plr.Character.HumanoidRootPart.Velocity) * getgenv().Howl.Aimbot.Prediction))
                    else
                        mainevent:FireServer("UpdateMousePos", Position + ((Plr.Character.Humanoid.MoveDirection * Plr.Character.Humanoid.WalkSpeed) * getgenv().Howl.Aimbot.Prediction))
                    end
                end
            end)
        end
    end)
end)

game:GetService("RunService").RenderStepped:Connect(function()
    if Plr ~= nil and Plr.Character then
        local Position = Plr.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall and Plr.Character[getgenv().Howl.Aimbot.TargetPart].Position + Vector3.new(0, getgenv().Howl.Aimbot.JumpOffset, 0) or Plr.Character[getgenv().Howl.Aimbot.TargetPart].Position
        if not CheckAnti(Plr) then
            local Main = CFrame.new(workspace.CurrentCamera.CFrame.p, Position + ((Plr.Character.HumanoidRootPart.Velocity) * getgenv().Howl.Aimbot.AimBotSkid) + GetShakedVector3(getgenv().Howl.Aimbot.Shake))
            workspace.CurrentCamera.CFrame = workspace.CurrentCamera.CFrame:Lerp(Main, getgenv().Howl.Aimbot.Amount, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut)
        else
            local Main = CFrame.new(workspace.CurrentCamera.CFrame.p, Position + ((Plr.Character.Humanoid.MoveDirection * Plr.Character.Humanoid.WalkSpeed) * getgenv().Howl.Aimbot.AimBotSkid) + GetShakedVector3(getgenv().Howl.Aimbot.CameraShake))
            workspace.CurrentCamera.CFrame = workspace.CurrentCamera.CFrame:Lerp(Main, getgenv().Howl.Aimbot.Amount, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut)
        end
    end
    if getgenv().Howl.Checks.PlayerDeath == true and Plr and Plr.Character then
        local KOd = Plr.Character:WaitForChild("BodyEffects")["K.O"].Value
        local Grabbed = Plr.Character:FindFirstChild("GRABBING_CONSTRAINT") ~= nil
        if Plr.Character.Humanoid.Health < 1 or KOd or Grabbed then
            if Locking == true then
                Plr = nil
                Locking = false
            end
        end
    end
    if getgenv().Howl.Checks.TargetDeath == true and Plr and Plr.Character:FindFirstChild("Humanoid") then
        if Plr.Character.Humanoid.health < 1 then
            if Locking == true then
                Plr = nil
                Locking = false
            end
        end
    end
    if getgenv().Howl.Checks.PlayerDeath  == true and Client.Character and Client.Character:FindFirstChild("Humanoid") and Client.Character.Humanoid.health < 1 then
        if Locking == true then
            Plr = nil
            Locking = false
        end
    end
    if getgenv().Howl.Safety.AntiGroundShots == true and Plr.Character.Humanoid.Jump == true and Plr.Character.Humanoid.FloorMaterial == Enum.Material.Air then
        pcall(function()
            local TargetVelv5 = Plr.Character.HumanoidRootPart
    TargetVelv5.Velocity = Vector3.new(TargetVelv5.Velocity.X, math.abs(TargetVelv5.Velocity.Y * 0.36),
     TargetVelv5.Velocity.Z)
            TargetVelv5.AssemblyLinearVelocity = Vector3.new(TargetVelv5.Velocity.X, math.abs(TargetVelv5.Velocity.Y * 0.36), TargetVelv5.Velocity.Z)
        end)
    end
end)

if getgenv().Howl.Spin.Enabled == true then
    
    local Players = game:GetService("Players")
    local UserInputService = game:GetService("UserInputService")
    local RunService = game:GetService("RunService")
    local Camera = workspace.CurrentCamera
    local Toggle = getgenv().Howl.Spin.Enabled
    local RotationSpeed = getgenv().Howl.Spin.SpinSpeed
    local Keybind = getgenv().Howl.Spin.Keybind
    
    local function OnKeyPress(Input, GameProcessedEvent)
        if Input.KeyCode == Keybind and not GameProcessedEvent then 
            Toggle = not Toggle
        end
    end
    
    UserInputService.InputBegan:Connect(OnKeyPress)
    
    local LastRenderTime = 0
    local TotalRotation = 0
    
    local function RotateCamera()
        if Toggle then
            local CurrentTime = tick()
            local TimeDelta = math.min(CurrentTime - LastRenderTime, 0.01)
            LastRenderTime = CurrentTime
    
            local RotationAngle = RotationSpeed * TimeDelta
            local Rotation = CFrame.fromAxisAngle(Vector3.new(0, 1, 0), math.rad(RotationAngle))
            Camera.CFrame = Camera.CFrame * Rotation
    
            TotalRotation = TotalRotation + RotationAngle
            if TotalRotation >= getgenv().Howl.Spin.Degrees then 
                Toggle = false
                TotalRotation = 0
            end
        end
    end
    
    RunService.RenderStepped:Connect(RotateCamera)
    end

getgenv().Loaded = true -- end of the script
else
    game:GetService("StarterGui"):SetCore("SendNotification", {
        Title = "Howl",
        Text = "Updated Table",
        Duration = 0.001
    })
end
end)

local section = tab:Section("Azure Modded")

section:Button("Button", function()--[[
############################################################################
#     _     ______   _ ____  _____   __  __  ___  ____  ____  _____ ____   #
#    / \   |__  / | | |  _ \| ____| |  \/  |/ _ \|  _ \|  _ \| ____|  _ \  #
#   / _ \    / /| | | | |_) |  _|   | |\/| | | | | | | | | | |  _| | | | | #
#  / ___ \  / /_| |_| |  _ <| |___  | |  | | |_| | |_| | |_| | |___| |_| | #
# /_/   \_\/____|\___/|_| \_\_____| |_|  |_|\___/|____/|____/|_____|____/  #
#                                                                          #
#  _                   _        _                                          #
# | |__  _   _        / \   ___| |_ _   _ _ __ _ __                        #
# | '_ \| | | |      / _ \ / __| __| | | | '__| '_ \                       #
# | |_) | |_| |     / ___ \ (__| |_| |_| | |  | | | |                      #
# |_.__/ \__, |    /_/   \_\___|\__|\__, |_|  |_| |_|                      #
#        |___/                      |___/                                  #
############################################################################

Actyrn or discord.gg/azuremodded or discord.gg/hUvujCnGMb
Original script credits go to Elegant and Weda

--]]
loadstring(game:HttpGet("https://raw.githubusercontent.com/Actyrn/Scripts/main/AzureModded"))()
   
end)

local section = tab:Section("Cyber Lock")

section:Button("Button", function() -- MADE BY disabledacctah on discord/ Cyber-Roblox on YT          



game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "Cyber-Roblox",
		Text = "Loading . . .",
	}
)
wait(1)
game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "Cyber-Roblox",
		Text = "Authenticating..",
	}
)
wait(1)
game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "Cyber-Roblox",
		Text = "Setting Up...",
	}
)
wait(1)
game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "Cyber-Roblox",
		Text = "Done!",
	}
)
wait(0.5)
game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "Cyber-Roblox",
		Text = "made by disabledacctah on discord!",
	}
)    



local player = game.Players.LocalPlayer
local camera = game.Workspace.CurrentCamera
local runService = game:GetService("RunService")
local userInputService = game:GetService("UserInputService")

local aimSpeed = 0.1 -- Adjust this value for responsiveness
local isAimAssistEnabled = false
local predictionFactor = 5.4 -- Adjust this value for prediction accuracy
local currentTarget = nil
local smoothingFactor = 0.02 -- Adjust this value for smoother camera movement

local function predictTargetPosition(target, deltaTime)
    local targetPosition = target.UpperTorso.Position
    local targetVelocity = target:FindFirstChild("Humanoid") and target.HumanoidRootPart.Velocity or Vector3.new()

    local predictedPosition = targetPosition + targetVelocity * predictionFactor * deltaTime
    return predictedPosition
end

local function aimAtTarget()
    if currentTarget and currentTarget.Parent then
        local predictedPosition = predictTargetPosition(currentTarget, runService.RenderStepped:Wait())
        local lookVector = (predictedPosition - camera.CFrame.Position).Unit

        -- Smooth the camera movement
        local smoothedLookVector = (1 - smoothingFactor) * lookVector + smoothingFactor * (camera.CFrame.LookVector)

        local newCFrame = CFrame.new(camera.CFrame.Position, camera.CFrame.Position + aimSpeed * smoothedLookVector)
        camera.CFrame = newCFrame
    else
        currentTarget = nil
        isAimAssistEnabled = false
    end
end

local function findClosestPlayerToMouse()
    local mousePos = userInputService:GetMouseLocation()
    local closestPlayer = nil
    local shortestDistance = math.huge

    for _, object in pairs(game.Players:GetPlayers()) do
        if object ~= player and object.Character and object.Character:FindFirstChild("Humanoid") and object.Character:FindFirstChild("UpperTorso") then
            local targetScreenPos, onScreen = camera:WorldToScreenPoint(object.Character.UpperTorso.Position)

            if onScreen then
                local distance = (Vector2.new(targetScreenPos.X, targetScreenPos.Y) - mousePos).Magnitude

                if distance < shortestDistance then
                    closestPlayer = object.Character
                    shortestDistance = distance
                end
            end
        end
    end

    return closestPlayer
end

local function onKeyPress(input, gameProcessedEvent)
    if not gameProcessedEvent then
        if input.KeyCode == Enum.KeyCode.Q then
            isAimAssistEnabled = not isAimAssistEnabled
            if isAimAssistEnabled then
                currentTarget = findClosestPlayerToMouse()
            else
                currentTarget = nil
            end
            print("Aim Assist Toggled:", isAimAssistEnabled)
        end
    end
end

local function onCharacterAdded(character)
    character:WaitForChild("Humanoid").Died:Connect(function()
        if currentTarget == character then
            currentTarget = nil
        end
    end)
end

userInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    onKeyPress(input, gameProcessedEvent)
end)

player.CharacterAdded:Connect(onCharacterAdded)

runService.RenderStepped:Connect(function(deltaTime)
    if isAimAssistEnabled then
        aimAtTarget()
    end
end)
   
end)

local section = tab:Section("1yyz Free Gui")

section:Button("Button", function()game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "1yyz Free Gui",
		Text = "Loading . . .",
	}
)
wait(1)
game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "1yyz Free Gui",
		Text = "Authenticating..",
	}
)
wait(1)
game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "1yyz Free Gui",
		Text = "Setting Up...",
	}
)
wait(1)
game.StarterGui:SetCore(
	"SendNotification",
	{
		Title = "1yyz Free Gui",
		Text = "DM 1yyz FOR SUPPORT",
	}
)
wait(3)
 
 local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/slattisbabygirl/cattoware/main/Wcatto.lua"))()
 
 local NotifyLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/Dynissimo/main/Scripts/AkaliNotif.lua"))()
    local Notify = NotifyLibrary.Notify
    Library.theme.accentcolor = Color3.fromRGB(45, 205, 50)
    Library.theme.accentcolor2 = Color3.fromRGB(45, 205, 50)
 
 
    local Window = Library:CreateWindow("1yyz Free Gui", Vector2.new(492, 598), Enum.KeyCode.P)
 
     local AimingTab = Window:CreateTab("Aiming")
 
     local MiscTab = Window:CreateTab("Misc")
 
     local sector1 = AimingTab:CreateSector("Targeting", "left")
 
     sector1:AddButton("Target Aim", function()
     local Settings = {
    rewrittenmain = {
        Enabled = true,
        Key = "c",
        DOT = true,
        AIRSHOT = true,
        NOTIF = true,
        AUTOPRED = true,
        FOV = math.huge,
        RESOVLER = false
    }
}
 
local SelectedPart = "HumanoidRootPart"
local Prediction = true
local PredictionValue = 0.12642392
 
 
    local AnchorCount = 0
    local MaxAnchor = 50
 
    local CC = game:GetService"Workspace".CurrentCamera
    local Plr;
    local enabled = false
    local accomidationfactor = 0.15311221541002
    local mouse = game.Players.LocalPlayer:GetMouse()
    local placemarker = Instance.new("Part", game.Workspace)
 
    function makemarker(Parent, Adornee, Color, Size, Size2)
        local e = Instance.new("BillboardGui", Parent)
        e.Name = "PP"
        e.Adornee = Adornee
        e.Size = UDim2.new(Size, Size2, Size, Size2)
        e.AlwaysOnTop = Settings.rewrittenmain.DOT
        local a = Instance.new("Frame", e)
        if Settings.rewrittenmain.DOT == true then
        a.Size = UDim2.new(1, 0, 1, 0)
        else
        a.Size = UDim2.new(0, 0, 0, 0)
        end
        if Settings.rewrittenmain.DOT == true then
        a.Transparency = 0
        a.BackgroundTransparency = 0
        else
        a.Transparency = 1
        a.BackgroundTransparency = 1
        end
        a.BackgroundColor3 = Color
        local g = Instance.new("UICorner", a)
        if Settings.rewrittenmain.DOT == false then
        g.CornerRadius = UDim.new(0, 0)
        else
        g.CornerRadius = UDim.new(1, 1) 
        end
        return(e)
    end
 
 
    local data = game.Players:GetPlayers()
    function noob(player)
        local character
        repeat wait() until player.Character
        local handler = makemarker(guimain, player.Character:WaitForChild(SelectedPart), Color3.fromRGB(0, 0, 0), 0.5, 3)
        handler.Name = player.Name
        player.CharacterAdded:connect(function(Char) handler.Adornee = Char:WaitForChild(SelectedPart) end)
 
 
        spawn(function()
            while wait() do
                if player.Character then
                end
            end
        end)
    end
 
    for i = 1, #data do
        if data[i] ~= game.Players.LocalPlayer then
            noob(data[i])
        end
    end
 
    game.Players.PlayerAdded:connect(function(Player)
        noob(Player)
    end)
 
    spawn(function()
        placemarker.Anchored = true
        placemarker.CanCollide = false
        if Settings.rewrittenmain.DOT == true then
        placemarker.Size = Vector3.new(10, 10, 10)
        else
        placemarker.Size = Vector3.new(5, 5, 5)
        end
        placemarker.Transparency = 0.75
        if Settings.rewrittenmain.DOT then
        makemarker(placemarker, placemarker, Color3.fromRGB(4, 242, 107), 3, 0)
        end
    end)
 
    game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(k)
        if k == Settings.rewrittenmain.Key and Settings.rewrittenmain.Enabled then
            if enabled == true then
                enabled = false
                if Settings.rewrittenmain.NOTIF == true then
                    Plr = getClosestPlayerToCursor()
                game.StarterGui:SetCore("SendNotification", {
                    Title = "";
                    Text = "Unlocked!",
                    Duration = 1
                })
            end
            else
                Plr = getClosestPlayerToCursor()
                enabled = true
                if Settings.rewrittenmain.NOTIF == true then
 
                    game.StarterGui:SetCore("SendNotification", {
                        Title = "1yyz Owns You";
                        Text = "Target: "..tostring(Plr.Character.Humanoid.DisplayName),
                        Duration = 2
                    })
 
                end
            end
        end
    end)
 
 
 
    function getClosestPlayerToCursor()
        local closestPlayer
        local shortestDistance = Settings.rewrittenmain.FOV
 
        for i, v in pairs(game.Players:GetPlayers()) do
            if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then
                local pos = CC:WorldToViewportPoint(v.Character.PrimaryPart.Position)
                local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(mouse.X, mouse.Y)).magnitude
                if magnitude < shortestDistance then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end
        return closestPlayer
    end
 
    local pingvalue = nil;
    local split = nil;
    local ping = nil;
 
    game:GetService"RunService".Stepped:connect(function()
        if enabled and Plr.Character ~= nil and Plr.Character:FindFirstChild("HumanoidRootPart") then
            placemarker.CFrame = CFrame.new(Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor))
        else
            placemarker.CFrame = CFrame.new(0, 9999, 0)
        end
        if Settings.rewrittenmain.AUTOPRED == true then
             pingvalue = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
             split = string.split(pingvalue,'(')
             ping = tonumber(split[1])
                if ping < 130 then
                PredictionValue = 0.1518
            elseif ping < 125 then
                PredictionValue = 0.14988
            elseif ping < 110 then
                PredictionValue = 0.14553132132121255556666672
            elseif ping < 105 then
                PredictionValue = 0.1409340
            elseif ping < 90 then
                PredictionValue = 0.13623132
            elseif ping < 80 then
                PredictionValue = 0.131314253678192031927365421456789331
            elseif ping < 70 then
                PredictionValue = 0.1424567
            elseif ping < 60 then
                PredictionValue = 0.14132646
            elseif ping < 50 then
                PredictionValue = 0.118532
            elseif ping < 40 then
                PredictionValue = 0.12132
            elseif ping < 30 then
                PredictionValue = 0.14231
            elseif ping < 20 then
                PredictionValue = 0.13
            elseif ping < 10 then
                PredictionValue = 0.09
            end
        end
    end)
 
    local mt = getrawmetatable(game)
    local old = mt.__namecall
    setreadonly(mt, false)
    mt.__namecall = newcclosure(function(...)
        local args = {...}
        if enabled and getnamecallmethod() == "FireServer" and args[2] == "UpdateMousePos" and Settings.rewrittenmain.Enabled and Plr.Character ~= nil then
 
            -- args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor)
            --[[
            if Settings.rewrittenmain.AIRSHOT == true then
                if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
 
                    --// Airshot
                    args[3] = Plr.Character.LeftFoot.Position+(Plr.Character.LeftFoot.Velocity*PredictionValue)
 
                else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)
 
                end
            else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)
            end
            ]]
            if Prediction == true then
 
            args[3] = Plr.Character[SelectedPart].Position+(Plr.Character[SelectedPart].Velocity*PredictionValue)
 
            else
 
            args[3] = Plr.Character[SelectedPart].Position
 
            end
 
            return old(unpack(args))
        end
        return old(...)
    end)
 
    game:GetService("RunService").RenderStepped:Connect(function()
        if Settings.rewrittenmain.RESOVLER == true and Plr.Character ~= nil and enabled and Settings.rewrittenmain.Enabled then
        if Settings.rewrittenmain.AIRSHOT == true and enabled and Plr.Character ~= nil then
 
            if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
 
                --// Airshot
 
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "LeftFoot"
 
            else
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "HumanoidRootPart"
 
            end
            else
 
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "HumanoidRootPart"
            end
 
        else
                SelectedPart = "HumanoidRootPart"
        end
    end)
    end)
 
local sector1 = AimingTab:CreateSector("1yyz Camlock", "right")
 
sector1:AddButton("1yyz Free Camlock (Q)", function()
getgenv().OldAimPart = "Head"
getgenv().AimPart = "HumanoidRootPart" -- For R15 Games: {UpperTorso, LowerTorso, HumanoidRootPart, Head} | For R6 Games: {Head, Torso, HumanoidRootPart}  
    getgenv().AimlockKey = "q"
    getgenv().AimRadius = 100 -- How far away from someones character you want to lock on at
    getgenv().ThirdPerson = true 
    getgenv().FirstPerson = true
    getgenv().TeamCheck = false -- Check if Target is on your Team (True means it wont lock onto your teamates, false is vice versa) (Set it to false if there are no teams)
    getgenv().PredictMovement = true -- Predicts if they are moving in fast velocity (like jumping) so the aimbot will go a bit faster to match their speed 
    getgenv().PredictionVelocity = 7.8
    getgenv().CheckIfJumped = true
    getgenv().Smoothness = true
    getgenv().SmoothnessAmount = 0.5
 
    local Players, Uis, RService, SGui = game:GetService"Players", game:GetService"UserInputService", game:GetService"RunService", game:GetService"StarterGui";
    local Client, Mouse, Camera, CF, RNew, Vec3, Vec2 = Players.LocalPlayer, Players.LocalPlayer:GetMouse(), workspace.CurrentCamera, CFrame.new, Ray.new, Vector3.new, Vector2.new;
    local Aimlock, MousePressed, CanNotify = true, false, false;
    local AimlockTarget;
    local OldPre;
 
 
 
    getgenv().WorldToViewportPoint = function(P)
        return Camera:WorldToViewportPoint(P)
    end
 
    getgenv().WorldToScreenPoint = function(P)
        return Camera.WorldToScreenPoint(Camera, P)
    end
 
    getgenv().GetObscuringObjects = function(T)
        if T and T:FindFirstChild(getgenv().AimPart) and Client and Client.Character:FindFirstChild("Head") then 
            local RayPos = workspace:FindPartOnRay(RNew(
                T[getgenv().AimPart].Position, Client.Character.Head.Position)
            )
            if RayPos then return RayPos:IsDescendantOf(T) end
        end
    end
 
    getgenv().GetNearestTarget = function()
        -- Credits to whoever made this, i didnt make it, and my own mouse2plr function kinda sucks
        local players = {}
        local PLAYER_HOLD  = {}
        local DISTANCES = {}
        for i, v in pairs(Players:GetPlayers()) do
            if v ~= Client then
                table.insert(players, v)
            end
        end
        for i, v in pairs(players) do
            if v.Character ~= nil then
                local AIM = v.Character:FindFirstChild("Head")
                if getgenv().TeamCheck == true and v.Team ~= Client.Team then
                    local DISTANCE = (v.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
                    local RAY = Ray.new(game.Workspace.CurrentCamera.CFrame.p, (Mouse.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * DISTANCE)
                    local HIT,POS = game.Workspace:FindPartOnRay(RAY, game.Workspace)
                    local DIFF = math.floor((POS - AIM.Position).magnitude)
                    PLAYER_HOLD[v.Name .. i] = {}
                    PLAYER_HOLD[v.Name .. i].dist= DISTANCE
                    PLAYER_HOLD[v.Name .. i].plr = v
                    PLAYER_HOLD[v.Name .. i].diff = DIFF
                    table.insert(DISTANCES, DIFF)
                elseif getgenv().TeamCheck == false and v.Team == Client.Team then 
                    local DISTANCE = (v.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
                    local RAY = Ray.new(game.Workspace.CurrentCamera.CFrame.p, (Mouse.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * DISTANCE)
                    local HIT,POS = game.Workspace:FindPartOnRay(RAY, game.Workspace)
                    local DIFF = math.floor((POS - AIM.Position).magnitude)
                    PLAYER_HOLD[v.Name .. i] = {}
                    PLAYER_HOLD[v.Name .. i].dist= DISTANCE
                    PLAYER_HOLD[v.Name .. i].plr = v
                    PLAYER_HOLD[v.Name .. i].diff = DIFF
                    table.insert(DISTANCES, DIFF)
                end
            end
        end
 
        if unpack(DISTANCES) == nil then
            return nil
        end
 
        local L_DISTANCE = math.floor(math.min(unpack(DISTANCES)))
        if L_DISTANCE > getgenv().AimRadius then
            return nil
        end
 
        for i, v in pairs(PLAYER_HOLD) do
            if v.diff == L_DISTANCE then
                return v.plr
            end
        end
        return nil
    end
 
    Mouse.KeyDown:Connect(function(a)
        if not (Uis:GetFocusedTextBox()) then 
            if a == AimlockKey and AimlockTarget == nil then
                pcall(function()
                    if MousePressed ~= true then MousePressed = true end 
                    local Target;Target = GetNearestTarget()
                    if Target ~= nil then 
                        AimlockTarget = Target
                    end
                end)
            elseif a == AimlockKey and AimlockTarget ~= nil then
                if AimlockTarget ~= nil then AimlockTarget = nil end
                if MousePressed ~= false then 
                    MousePressed = false 
                end
            end
        end
    end)
 
    RService.RenderStepped:Connect(function()
        if getgenv().ThirdPerson == true and getgenv().FirstPerson == true then 
            if (Camera.Focus.p - Camera.CoordinateFrame.p).Magnitude > 1 or (Camera.Focus.p - Camera.CoordinateFrame.p).Magnitude <= 1 then 
                CanNotify = true 
            else 
                CanNotify = false 
            end
        elseif getgenv().ThirdPerson == true and getgenv().FirstPerson == false then 
            if (Camera.Focus.p - Camera.CoordinateFrame.p).Magnitude > 1 then 
                CanNotify = true 
            else 
                CanNotify = false 
            end
        elseif getgenv().ThirdPerson == false and getgenv().FirstPerson == true then 
            if (Camera.Focus.p - Camera.CoordinateFrame.p).Magnitude <= 1 then 
                CanNotify = true 
            else 
                CanNotify = false 
            end
        end
        if Aimlock == true and MousePressed == true then 
            if AimlockTarget and AimlockTarget.Character and AimlockTarget.Character:FindFirstChild(getgenv().AimPart) then 
                if getgenv().FirstPerson == true then
                    if CanNotify == true then
                        if getgenv().PredictMovement == true then
                            if getgenv().Smoothness == true then
                                --// The part we're going to lerp/smoothen \\--
                                local Main = CF(Camera.CFrame.p, AimlockTarget.Character[getgenv().AimPart].Position + AimlockTarget.Character[getgenv().AimPart].Velocity/PredictionVelocity)
 
                                --// Making it work \\--
                                Camera.CFrame = Camera.CFrame:Lerp(Main, getgenv().SmoothnessAmount, Enum.EasingStyle.Elastic, Enum.EasingDirection.InOut)
                            else
                                Camera.CFrame = CF(Camera.CFrame.p, AimlockTarget.Character[getgenv().AimPart].Position + AimlockTarget.Character[getgenv().AimPart].Velocity/PredictionVelocity)
                            end
                        elseif getgenv().PredictMovement == false then 
                            if getgenv().Smoothness == true then
                                --// The part we're going to lerp/smoothen \\--
                                local Main = CF(Camera.CFrame.p, AimlockTarget.Character[getgenv().AimPart].Position)
 
                                --// Making it work \\--
                                Camera.CFrame = Camera.CFrame:Lerp(Main, getgenv().SmoothnessAmount, Enum.EasingStyle.Elastic, Enum.EasingDirection.InOut)
                            else
                                Camera.CFrame = CF(Camera.CFrame.p, AimlockTarget.Character[getgenv().AimPart].Position)
                            end
                        end
                    end
                end
            end
        end
         if CheckIfJumped == true then
       if AimlockTarget.Character.HuDDDDDDDDDDWmanoid.FloorMaterial == Enum.Material.Air then
 
           getgenv().AimPart = "UpperTorso"
       else
         getgenv().AimPart = getgenv().OldAimPart
 
       end
    end
end)
end)
 
 
local sector8 = MiscTab:CreateSector("Misc Stuff", "left")
 
sector8:AddButton("Fly (X)", function()
local plr = game.Players.LocalPlayer
                local mouse = plr:GetMouse()
 
                localplayer = plr
 
                if workspace:FindFirstChild("Core") then
                workspace.Core:Destroy()
                end
 
                local Core = Instance.new("Part")
                Core.Name = "Core"
                Core.Size = Vector3.new(0.05, 0.05, 0.05)
 
                spawn(function()
                Core.Parent = workspace
                local Weld = Instance.new("Weld", Core)
                Weld.Part0 = Core
                Weld.Part1 = localplayer.Character.LowerTorso
                Weld.C0 = CFrame.new(0, 0, 0)
                end)
 
                workspace:WaitForChild("Core")
 
                local torso = workspace.Core
                flying = true
                local speed=10
                local keys={a=false,d=false,w=false,s=false}
                local e1
                local e2
                local function start()
                local pos = Instance.new("BodyPosition",torso)
                local gyro = Instance.new("BodyGyro",torso)
                pos.Name="EPIXPOS"
                pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
                pos.position = torso.Position
                gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
                gyro.cframe = torso.CFrame
                repeat
                wait()
                localplayer.Character.Humanoid.PlatformStand=true
                local new=gyro.cframe - gyro.cframe.p + pos.position
                if not keys.w and not keys.s and not keys.a and not keys.d then
                speed=5
                end
                if keys.w then
                new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                speed=speed+0
                end
                if keys.s then
                new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                speed=speed+0
                end
                if keys.d then
                new = new * CFrame.new(speed,0,0)
                speed=speed+0
                end
                if keys.a then
                new = new * CFrame.new(-speed,0,0)
                speed=speed+0
                end
                if speed>10 then
                speed=5
                end
                pos.position=new.p
                if keys.w then
                gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(-math.rad(speed*0),0,0)
                elseif keys.s then
                gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(math.rad(speed*0),0,0)
                else
                gyro.cframe = workspace.CurrentCamera.CoordinateFrame
                end
                until flying == false
                if gyro then gyro:Destroy() end
                if pos then pos:Destroy() end
                flying=false
                localplayer.Character.Humanoid.PlatformStand=false
                speed=10
                end
                e1=mouse.KeyDown:connect(function(key)
                if not torso or not torso.Parent then flying=false e1:disconnect() e2:disconnect() return end
                if key=="w" then
                keys.w=true
                elseif key=="s" then
                keys.s=true
                elseif key=="a" then
                keys.a=true
                elseif key=="d" then
                keys.d=true
                elseif key=="x" then
                if flying==true then
                flying=false
                else
                flying=true
                start()
                end
                end
                end)
                e2=mouse.KeyUp:connect(function(key)
                if key=="w" then
                keys.w=false
                elseif key=="s" then
                keys.s=false
                elseif key=="a" then
                keys.a=false
                elseif key=="d" then
                keys.d=false
                end
                end)
                start()
            end)
 
 
            local sector9 = MiscTab:CreateSector("RayX", "right")
 
            sector9:AddButton("RayX", function()
            loadstring(game:HttpGet('https://raw.githubusercontent.com/SpaceYes/Lua/Main/DaHood.Lua'))()
            end)
end)

local section = tab:Section("Peterhook.crack")

section:Button("Button", function()--[[

██████╗ ███████╗████████╗███████╗██████╗ ██╗  ██╗ ██████╗  ██████╗ ██╗  ██╗
██╔══██╗██╔════╝╚══██╔══╝██╔════╝██╔══██╗██║  ██║██╔═══██╗██╔═══██╗██║ ██╔╝
██████╔╝█████╗     ██║   █████╗  ██████╔╝███████║██║   ██║██║   ██║█████╔╝ 
██╔═══╝ ██╔══╝     ██║   ██╔══╝  ██╔══██╗██╔══██║██║   ██║██║   ██║██╔═██╗ 
██║     ███████╗   ██║   ███████╗██║  ██║██║  ██║╚██████╔╝╚██████╔╝██║  ██╗
╚═╝     ╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝  ╚═════╝ ╚═╝  ╚═╝
                                                                           
--]]







repeat wait() until game:IsLoaded()
loadstring(game:HttpGet("https://raw.githubusercontent.com/Ziheim51000/Peterhook/main/MonkeyVio"))()
end)

local tab = window:Tab("fisch")


local section = tab:Section("speed hub")

section:Button("Execute", function()loadstring(game:HttpGet("https://pastebin.com/raw/FYAJCkUL"))()
end)

local section = tab:Section("Fisch Auto Farm")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/rblxscriptsdotnet/roblox-scripts/refs/heads/main/rblxscriptsnet%20fisch%20autofarm"))()
end)

local section = tab:Section("Bonk Hub (Key)")

section:Button("Execute", function()loadstring(game:HttpGet("https://bonkhubloader.netlify.app",true))()
end)

local section = tab:Section("goombah hub (key)")

section:Button("Execute", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/JustLevel/goombahub/main/fisch.lua"))()
end)

local section = tab:Section("1yyz Fisch Hub old")

section:Button("Execute", function()local repo = 'https://raw.githubusercontent.com/KINGHUB01/Gui/main/'

local Library = loadstring(game:HttpGet(repo ..'Gui%20Lib%20%5BLibrary%5D'))()
local ThemeManager = loadstring(game:HttpGet(repo ..'Gui%20Lib%20%5BThemeManager%5D'))()
local SaveManager = loadstring(game:HttpGet(repo ..'Gui%20Lib%20%5BSaveManager%5D'))()

local Window = Library:CreateWindow({
    Title = '1yyz Fisch Hub',
    Center = true,
    AutoShow = true,
    TabPadding = 8,
    MenuFadeTime = 0.2
})

local FrameTimer = tick()
local FrameCounter = 0;
local FPS = 1000;

local WatermarkConnection = game:GetService('RunService').RenderStepped:Connect(function()
    FrameCounter += 1;

    if (tick() - FrameTimer) >= 1 then
        FPS = FrameCounter;
        FrameTimer = tick();
        FrameCounter = 0;
    end;

    Library:SetWatermark(('1yyz Hub | %s fps | %s ms'):format(
        math.floor(FPS),
        math.floor(game:GetService('Stats').Network.ServerStatsItem['Data Ping']:GetValue())
    ));
end);

-- Tabs

local Tabs = {
    AutoFarm = Window:AddTab('AutoFarm'),
    Teleports = Window:AddTab('Teleports'),
    Player = Window:AddTab('Player'),
    Settings = Window:AddTab('Settings')
}

-- Tables

local teleportSpots = {
    altar = CFrame.new(1296.320068359375, -808.5519409179688, -298.93817138671875),
    arch = CFrame.new(998.966796875, 126.6849365234375, -1237.1434326171875),
    birch = CFrame.new(1742.3203125, 138.25787353515625, -2502.23779296875),
    enchant = CFrame.new(1296.320068359375, -808.5519409179688, -298.93817138671875),
    executive = CFrame.new(-29.836761474609375, -250.48486328125, 199.11614990234375),
    keepers = CFrame.new(1296.320068359375, -808.5519409179688, -298.93817138671875),
    mod_house = CFrame.new(-30.205902099609375, -249.40594482421875, 204.0529022216797),
    moosewood = CFrame.new(383.10113525390625, 131.2406005859375, 243.93385314941406),
    mushgrove = CFrame.new(2501.48583984375, 127.7583236694336, -720.699462890625),
    roslit = CFrame.new(-1476.511474609375, 130.16842651367188, 671.685302734375),
    snow = CFrame.new(2648.67578125, 139.06605529785156, 2521.29736328125),
    snowcap = CFrame.new(2648.67578125, 139.06605529785156, 2521.29736328125),
    spike = CFrame.new(-1254.800537109375, 133.88555908203125, 1554.2021484375),
    statue = CFrame.new(72.8836669921875, 138.6964874267578, -1028.4193115234375),
    sunstone = CFrame.new(-933.259705, 128.143951, -1119.52063, -0.342042685, 0, -0.939684391, 0, 1, 0, 0.939684391, 0, -0.342042685),
    swamp = CFrame.new(2501.48583984375, 127.7583236694336, -720.699462890625),
    terrapin = CFrame.new(-143.875244140625, 141.1676025390625, 1909.6070556640625),
    vertigo = CFrame.new(-112.007278, -492.901093, 1040.32788, -1, 0, 0, 0, 1, 0, 0, 0, -1),
    volcano = CFrame.new(-1888.52319, 163.847565, 329.238281, 1, 0, 0, 0, 1, 0, 0, 0, 1),
    wilson = CFrame.new(2938.80591, 277.474762, 2567.13379, 0.4648332, 0, 0.885398269, 0, 1, 0, -0.885398269, 0, 0.4648332),
    wilsons_rod = CFrame.new(2879.2085, 135.07663, 2723.64233, 0.970463336, -0.168695927, -0.172460333, 0.141582936, -0.180552125, 0.973321974, -0.195333466, -0.968990743, -0.151334763),
    desolatepocket = CFrame.new(-1659.6, -214.2, -2853.1),
    GammaGrotto = CFrame.new(2238.1, -804.2, 1044.2),
    brinepool = CFrame.new(-1787.6, -142.7, -3384.5)
}

local racistPeople = {
    Witch = CFrame.new(409.368713, 135.712708, 312.134338, -0.93826592, -0.0479123928, 0.342580646, -9.64477658e-06, 0.99036473, 0.138483301, -0.345914871, 0.129930869, -0.929225981),
    Merchant = CFrame.new(416.690521, 130.302628, 342.765289, -0.249025017, -0.0326484665, 0.967946589, -0.0040341015, 0.999457955, 0.0326734781, -0.968488574, 0.00423171744, -0.249021754),
    Synph = CFrame.new(566.36499, 151.671799, 353.993896, -0.753522575, 0.00614984334, -0.657393873, -0.00677706953, 0.999830484, 0.0171213746, 0.657387733, 0.0173565373, -0.753353059),
    Pierre = CFrame.new(391.38855, 136.82576, 196.710144, -1, 0, 0, 0, 0.999927282, 0.012056686, 0, 0.012056686, -0.999927282),
    Phineas = CFrame.new(469.901093, 152.136032, 277.97641, 0.886104584, -0.00747075537, -0.46342513, 0, 0.999870062, -0.0161186438, 0.46348536, 0.014282804, 0.885989428),
    Shipwright = CFrame.new(357.972595, 135.112106, 258.154541, -0.0243720412, 0, -0.99970293, 0, 1, 0, 0.99970293, 0, -0.0243720412),
    Angler = CFrame.new(480.102478, 151.963333, 302.226898, 1, 0, 0, 0, 1, 0, 0, 0, 1),
    Mod_Keeper = CFrame.new(-39.0905838, -245.141144, 195.837891, -0.948549569, -0.0898146331, -0.303623199, -0.197293222, 0.91766715, 0.34490931, 0.247647122, 0.387066364, -0.888172567),
    Marc = CFrame.new(466.060913, 152.480682, 224.723465, -0.995860994, -0.0430678315, -0.0800375119, -0.0437603444, 0.999018013, 0.00691775233, 0.0796609744, 0.0103915781, -0.996767819),
    Lucas = CFrame.new(449.09433, 181.516205, 180.772995, 0.256410182, -0.0536140576, 0.965079963, 0.176032364, 0.984352529, 0.00791505724, -0.950403333, 0.167855799, 0.261835814),
    Roslit_Keeper = CFrame.new(-1512.37891, 134.500031, 631.24353, 0.738236904, 0, -0.674541533, 0, 1, 0, 0.674541533, 0, 0.738236904),
    Inn_Keeper = CFrame.new(487.458466, 152.300034, 231.498932, -0.564704418, 0, -0.825293183, 0, 1, 0, 0.825293183, 0, -0.564704418),
    FishingNpc_1 = CFrame.new(-1429.04138, 134.371552, 686.034424, 0, 0.0168599077, -0.999857903, 0, 0.999857903, 0.0168599077, 1, 0, 0),
    FishingNpc_2 = CFrame.new(-1778.55408, 149.791779, 648.097107, 0.183140755, 0.0223737024, -0.982832015, 0, 0.999741018, 0.0227586292, 0.983086705, -0.00416803267, 0.183093324),
    FishingNpc_3 = CFrame.new(-1778.26807, 147.83165, 653.258606, -0.129575253, 0.501478612, 0.855411887, -2.44146213e-05, 0.862683058, -0.505744994, -0.991569638, -0.0655529201, -0.111770131),
    Ashe = CFrame.new(-1709.94055, 149.862411, 729.399536, -0.92290163, 0.0273250472, -0.384064913, 0, 0.997478604, 0.0709675401, 0.385035753, 0.0654960647, -0.920574605),
    Alfredrickus = CFrame.new(-1520.60632, 142.923264, 764.522034, 0.301733732, 0.390740901, -0.869642735, 0.0273988936, 0.908225596, 0.417582989, 0.952998459, -0.149826124, 0.26333645),
    Daisy = CFrame.new(581.550049, 166.974594, 213.499969, -0.951949298, 0, -0.306255639, 0, 1, 0, 0.306255639, 0, -0.951949298),
    Appraiser = CFrame.new(453.003967, 151.970993, 206.907928, 0.0983118787, -0.24595812, 0.964281857, 0.0232069641, 0.969278991, 0.244866714, -0.994885027, -0.00169523992, 0.100999579)
}

local itemSpots = {
    Bait_Crate = CFrame.new(384.57513427734375, 135.3519287109375, 337.5340270996094),
    Carbon_Rod = CFrame.new(454.083618, 150.590073, 225.328827, 0.985374212, -0.170404434, 1.41561031e-07, 1.41561031e-07, 1.7285347e-06, 1, -0.170404434, -0.985374212, 1.7285347e-06),
    Crab_Cage = CFrame.new(474.803589, 149.664566, 229.49469, -0.721874595, 0, 0.692023814, 0, 1, 0, -0.692023814, 0, -0.721874595),
    Fast_Rod = CFrame.new(447.183563, 148.225739, 220.187454, 0.981104493, 1.26492232e-05, 0.193478703, -0.0522461236, 0.962867677, 0.264870107, -0.186291039, -0.269973755, 0.944674432),
    Flimsy_Rod = CFrame.new(471.107697, 148.36171, 229.642441, 0.841614008, 0.0774728209, -0.534493923, 0.00678436086, 0.988063335, 0.153898612, 0.540036798, -0.13314943, 0.831042409),
    GPS = CFrame.new(517.896729, 149.217636, 284.856842, 7.39097595e-06, -0.719539165, -0.694451928, -1, -7.39097595e-06, -3.01003456e-06, -3.01003456e-06, 0.694451928, -0.719539165),
    Long_Rod = CFrame.new(485.695038, 171.656326, 145.746109, -0.630167365, -0.776459217, -5.33461571e-06, 5.33461571e-06, -1.12056732e-05, 1, -0.776459217, 0.630167365, 1.12056732e-05),
    Lucky_Rod = CFrame.new(446.085999, 148.253006, 222.160004, 0.974526405, -0.22305499, 0.0233404674, 0.196993902, 0.901088715, 0.386306256, -0.107199371, -0.371867687, 0.922075212),
    Plastic_Rod = CFrame.new(454.425385, 148.169739, 229.172424, 0.951755166, 0.0709736273, -0.298537821, -3.42726707e-07, 0.972884834, 0.231290117, 0.306858391, -0.220131472, 0.925948203),
    Training_Rod = CFrame.new(457.693848, 148.357529, 230.414307, 1, -0, 0, 0, 0.975410998, 0.220393807, -0, -0.220393807, 0.975410998),
    King_Rod = CFrame.new(1377.6, -807.5, -301.8),
    trident_Rod = CFrame.new(-1484.4, -223.5, -2194.7)
}

-- Services

local VirtualInputManager = game:GetService("VirtualInputManager")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local Players = game:GetService("Players")

-- Locals

local LocalPlayer = Players.LocalPlayer
local LocalCharacter = LocalPlayer.Character
local HumanoidRootPart = LocalCharacter:FindFirstChild("HumanoidRootPart")
local ActiveFolder = Workspace:FindFirstChild("active")

local PlayerGUI = LocalPlayer:FindFirstChildOfClass("PlayerGui")

-- Varbiables

local autoShake = false
local autoShakeDelay = 0.1
local autoReel = false
local AutoCast = false
local Noclip = false
local AntiDrown = false

-- Rest

PlayerGUI.ChildAdded:Connect(function(GUI)
    if GUI:IsA("ScreenGui") and GUI.Name == "shakeui" then
        if GUI:FindFirstChild("safezone") ~= nil then
            GUI.safezone.ChildAdded:Connect(function(child)
                if child:IsA("ImageButton") and child.Name == "button" then
                    if autoShake == true then
                        task.wait(autoShakeDelay)
                        if child.Visible == true then
                            local pos = child.AbsolutePosition
                            local size = child.AbsoluteSize
                            VirtualInputManager:SendMouseButtonEvent(pos.X + size.X / 2, pos.Y + size.Y / 2, 0, true, LocalPlayer, 0)
                            VirtualInputManager:SendMouseButtonEvent(pos.X + size.X / 2, pos.Y + size.Y / 2, 0, false, LocalPlayer, 0)
                        end
                    end
                end
            end)
        end
    end
    if GUI:IsA("ScreenGui") and GUI.Name == "reel" then
        if autoReel == true then
            if ReplicatedStorage:WaitForChild("events"):WaitForChild("reelfinished") ~= nil then
                repeat task.wait(2) ReplicatedStorage.events.reelfinished:FireServer(100, false) until GUI == nil
            end
        end
    end
end)

PlayerGUI.ChildRemoved:Connect(function(GUI)
    if GUI.Name == "reel" then
        if AutoCast == true then
            task.wait(2)
            if LocalCharacter:FindFirstChildOfClass("Tool") ~= nil then
                local Tool = LocalCharacter:FindFirstChildOfClass("Tool")
                Tool.events.cast:FireServer(100)
            end
        end
    end
end)

LocalCharacter.ChildAdded:Connect(function(child)
    if child:IsA("Tool") then
        if AutoCast == true then
            task.wait(2)
            if LocalCharacter:FindFirstChildOfClass("Tool") ~= nil then
                local Tool = LocalCharacter:FindFirstChildOfClass("Tool")
                if Tool:FindFirstChild("events"):WaitForChild("cast") ~= nil then
                    Tool.events.cast:FireServer(100)
                end                
            end
        end
    end
end)

NoclipConnection = RunService.Stepped:Connect(function()
    if Noclip == true then
        if LocalCharacter ~= nil then
            for i, v in pairs(LocalCharacter:GetDescendants()) do
                if v:IsA("BasePart") and v.CanCollide == true then
                    v.CanCollide = false
                end
            end
        end
    end
end)

-- Farm

local AutoFarmGroup = Tabs.AutoFarm:AddLeftGroupbox('AutoFarm')
local SellGroup = Tabs.AutoFarm:AddRightGroupbox('Sell')
local EventGroup = Tabs.AutoFarm:AddRightGroupbox('Event')
local discordGroup = Tabs.AutoFarm:AddRightGroupbox('Join To Discord Server')

AutoFarmGroup:AddToggle('AutoShake', {
    Text = 'Auto Shake (laggy)',
    Default = false,
    Tooltip = 'Automatically clicks the shake button for you',
    Callback = function(Value)
        autoShake = Value
    end
})

AutoFarmGroup:AddInput('AutoShakeDelay', {
    Default = 0.1,
    Numeric = true,
    Finished = false,

    Text = 'AutoShake Delay',
    Tooltip = 'Change the delay between every shake',

    Placeholder = '0.1 is the most stable value',

    Callback = function(Value)
        autoShakeDelay = Value
    end
})


AutoFarmGroup:AddToggle('AutoReel', {
    Text = 'Auto Reel',
    Default = false,
    Tooltip = 'Automatically reels in the fishing rod',
    Callback = function(Value)
        autoReel = Value
    end
})

AutoFarmGroup:AddToggle('AutoCast', {
    Text = 'Auto Cast (NOT WORK FOR MOBILE)',
    Default = false,
    Tooltip = 'Automatically throws the rod',
    Callback = function(Value)
        AutoCast = Value
        if Value == true and LocalCharacter:FindFirstChildOfClass("Tool") ~= nil then
            local Tool = LocalCharacter:FindFirstChildOfClass("Tool")
            if Tool:FindFirstChild("events"):WaitForChild("cast") ~= nil then
                Tool.events.cast:FireServer(100)
            end
        end
        HumanoidRootPart.Anchored = Value
    end
})

local SellButton = SellGroup:AddButton({
    Text = 'Sell fish (go in moosewood)',
    Func = function()
        workspace:WaitForChild("world"):WaitForChild("npcs"):WaitForChild("Marc Merchant"):WaitForChild("merchant"):WaitForChild("sell"):InvokeServer()
    end,
    DoubleClick = true,
    Tooltip = 'Sells the fish (YOU HAVE TO HOLD AN FISH)'
})

local SellButton2 = SellGroup:AddButton({
  Text = 'Sell All fish (go in moosewood)',
  Func = function()
     workspace:WaitForChild("world"):WaitForChild("npcs"):WaitForChild("Marc Merchant"):WaitForChild("merchant"):WaitForChild("sellall"):InvokeServer()
 end,
    DoubleClick = true,
    Tooltip = 'Sells all fish'
})
local SellButton3 = SellGroup:AddButton({
  Text = 'Buy Random Lantern (go in Mod house)',
  Func = function()
     workspace:WaitForChild("world"):WaitForChild("npcs"):WaitForChild("Mods Latern Keeper"):WaitForChild("mods lantern"):WaitForChild("purchase"):InvokeServer()
 end,
    DoubleClick = true,
    Tooltip = 'Auto Buy Lantern'
})
local SellButton4 = SellGroup:AddButton({
  Text = 'Appraiser Fisch (go in MooseWood)',
  Func = function()
     workspace:WaitForChild("world"):WaitForChild("npcs"):WaitForChild("Appraiser"):WaitForChild("appraiser"):WaitForChild("appraise"):InvokeServer()
 end,
  DoubleClick = true,
    Tooltip = 'Auto appraise Fisch'
})
local SellButton5 = discordGroup:AddButton({
    Text = 'Copy Discord link',
    Func = function()
        setclipboard('1yyz username')
    end,
    DoubleClick = false,
    Tooltip = 'Join our discord!'
})
EventGroup:AddDropdown('Event', {
    Text = 'Grab Events Items',
    Tooltip = 'Grabs the Event Item',
    Values = {'Gaint Mushroom', 'Spiders Eye', 'Strange Root', 'Candy Corn', 'Dark Art Skull'},
    Default = '',
  
    Callback = function(Value)
        if HumanoidRootPart ~= nil and ActiveFolder ~= nil then
            local oldpos = HumanoidRootPart.CFrame
            local EventItem = ActiveFolder:FindFirstChild(Value)

            if EventItem ~= nil and EventItem:FindFirstChild("PickupPrompt") ~= nil then
                HumanoidRootPart.CFrame = EventItem:FindFirstChildOfClass("MeshPart").CFrame + Vector3.new(3, 2, 0)
                Noclip = true
                task.wait(0.05)
                HumanoidRootPart.Anchored = true
                task.wait(0.5)
                fireproximityprompt(EventItem.PickupPrompt)
                task.wait(1)
                if Toggles.Noclip.Value == false then
                    Noclip = false
                else
                    Noclip = true
                end
                HumanoidRootPart.Anchored = false
                HumanoidRootPart.CFrame = oldpos
            else
                Library:Notify(string.format('There is no "%s" in workspace', Value))
            end
        end
    end
})

-- Teleports

local TeleportsGroup = Tabs.Teleports:AddLeftGroupbox('Teleports')

TeleportsGroup:AddDropdown('PlaceTeleport', {
    Text = 'Place teleport',
    Tooltip = 'Teleport to a place',
    Values = {"altar", "arch", "birch", "enchant", "keepers", "mod_house", "moosewood", "mushgrove", "roslit", "snow", "snowcap", "spike", "statue", "sunstone", "swamp", "terrapin", "vertigo", "volcano", "wilson", "wilsons_rod", "desolatepocket", "GammaGrotto", "brinepool"},
    Default = '',
  
    Callback = function(Value)
        if teleportSpots ~= nil and HumanoidRootPart ~= nil then
            HumanoidRootPart.CFrame = teleportSpots[Value]
        end
    end
})

TeleportsGroup:AddDropdown('NPCTeleport', {
    Text = 'Teleport to Npc',
    Tooltip = 'Teleport to a Npc',
    Values = {"Witch", "Merchant", "Synph", "Pierre", "Phineas", "Shipwright", "Angler", "Mod_Keeper", "Marc", "Lucas", "Roslit_Keeper", "Inn_Keeper", "FishingNpc_1", "FishingNpc_2", "FishingNpc_3", "Ashe", "Alfredrickus", "Daisy", "Appraiser"},
    Default = '',
  
    Callback = function(Value)
        if racistPeople ~= nil and HumanoidRootPart ~= nil then
            HumanoidRootPart.CFrame = racistPeople[Value]
        end
    end
})

TeleportsGroup:AddDropdown('ItemTeleport', {
    Text = 'Teleport to item',
    Tooltip = 'Teleport to a rod',
    Values = {"Bait_Crate", "Carbon_Rod", "Crab_Cage", "Fast_Rod", "Flimsy_Rod", "GPS", "Long_Rod", "Lucky_Rod", "Plastic_Rod", "Training_Rod", "King_Rod","trident_Rod"},
    Default = '',
  
    Callback = function(Value)
        if itemSpots ~= nil and HumanoidRootPart ~= nil then
            HumanoidRootPart.CFrame = itemSpots[Value]
        end
    end
})
-- LocalPlayer
local LocalPlayerGroup = Tabs.Player:AddLeftGroupbox('Player')

LocalPlayerGroup:AddToggle('Noclip', {
    Text = 'Noclip',
    Default = false,
    Tooltip = 'Allows you to go through walls',
    Callback = function(Value)
        Noclip = Value
    end
})

LocalPlayerGroup:AddToggle('AntiDrown', {
    Text = 'Disable Oxygen',
    Default = false,
    Tooltip = 'Allows you to stay in water infinitely',
    Callback = function(Value)
        AntiDrown = Value
        if Value == true then
            if LocalCharacter ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen") ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen").Enabled == true then	
                LocalCharacter.client.oxygen.Enabled = false	
            end	
            CharAddedAntiDrownCon = LocalPlayer.CharacterAdded:Connect(function()	
                if LocalCharacter ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen") ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen").Enabled == true and AntiDrown == true then	
                    LocalCharacter.client.oxygen.Enabled = false	
                end	
            end)
        else	
            if LocalCharacter ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen") ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen").Enabled == false then	
                LocalCharacter.client.oxygen.Enabled = true	
            end	
        end
    end
})

-- Settings

local SettingsGroup = Tabs.Settings:AddLeftGroupbox('Settings')

SettingsGroup:AddButton('Unload', function() Library:Unload() end)

Library:OnUnload(function()
	Library.Unloaded = true
    if autoReel == true then
        autoReel = false
    end
    if autoShake == true then
        autoShake = false
    end
    if AntiDrown == true then
        if LocalCharacter ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen") ~= nil and LocalCharacter:FindFirstChild("client"):WaitForChild("oxygen").Enabled == false then
            LocalCharacter.client.oxygen.Enabled = true
            CharAddedAntiDrownCon:Disconnect()
            AntiDrown = false
        end
    end
    if Noclip == true then
        Noclip = false
    end
    if AutoCast == true then
        AutoCast = false
    end
    if HumanoidRootPart.Anchored == true then
        HumanoidRootPart.Anchored = false
    end
    WatermarkConnection:Disconnect()
    NoclipConnection:Disconnect()
end)

SettingsGroup:AddLabel('Menu bind'):AddKeyPicker('MenuKeybind', { Default = 'Home', NoUI = true, Text = 'Menu keybind' })

Library.ToggleKeybind = Options.MenuKeybind

ThemeManager:SetLibrary(Library)

SaveManager:SetLibrary(Library)

SaveManager:IgnoreThemeSettings()

SaveManager:SetIgnoreIndexes({ 'MenuKeybind' })

ThemeManager:SetFolder('RinnsHub')

SaveManager:SetFolder('RinnsHub/Fisch')

SaveManager:BuildConfigSection(Tabs.Settings)

ThemeManager:ApplyToTab(Tabs.Settings)

SaveManager:LoadAutoloadConfig()
end)

local tab = window:Tab("Arsenal")

local section = tab:Section("leg hub")

section:Button("Button", function()loadstring(game:HttpGet("https://pastebin.com/raw/G6Ubkkuv"))()
end)

local section = tab:Section("Quotas Hub")

section:Button("Button", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Insertl/QuotasHub/main/BETAv1.3"))()
end)

local section = tab:Section("Tbao Hub")

section:Button("Button", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/tbao143/thaibao/main/TbaoHubArsenal"))()
end)

local tab = window:Tab("Rivals")

local section = tab:Section("God Hub")

section:Button("Button", function()loadstring(game:HttpGet("https://raw.githubusercontent.com/cracklua/cracks/m/SilentRivals"))()
end)

local tab = window:Tab("Combat Warriors")

local section = tab:Section("Stratos Hub")

section:Button("Button", function()loadstring(game:HttpGet("https://pastefy.app/50B4Z9UK/raw"))()
end)
