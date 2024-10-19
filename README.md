local Library = loadstring(game:HttpGet('https://raw.githubusercontent.com/Loco-CTO/UI-Library/main/VisionLibV2/source.lua'))()

Window = Library:Create({
	Name = "Axafy FREE Gui",
	Footer = "by 1yyz",
	ToggleKey = Enum.KeyCode.RightShift,
	LoadedCallback = function()
		Window:TaskBarOnly(true)
	end,
	KeySystem = true,
	Key = "1",
	MaxAttempts = 5,
	DiscordLink = nil,
	ToggledRelativeYOffset = 0
})

local AkaliNotif = loadstring(game:HttpGet("https://raw.githubusercontent.com/juywvm/ui-libs/main/Akali_Notify_Library/AkaliNotifyLibrary"))();

local Notify = AkaliNotif.Notify;

Notify({
    Description = "  FOR KEY ";
    Title = " 1yyz is discord";
    Duration = 5;
    });
    
Window:ChangeTogglekey(Enum.KeyCode.RightShift)

local Tab = Window:Tab({
	Name = "Blade Ball",
	Icon = "rbxassetid://108726009951043",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "Plutonium Gui"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/PawsThePaw/Plutonium.AA/main/Plutonium.Loader.lua", true))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Baka Hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/bankboi001fr/bankboi001fr/main/BakaHubBB.lua"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "zyphranis hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/bankboi001fr/bankboi001fr/refs/heads/main/Loader",true))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Pulu"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://github.com/Stang001/pulawat/blob/main/BladeBall.lua?raw=true"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "unknown-hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Mc4121ban/Source/refs/heads/main/Nurysium.lua"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Lunax Hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Alexisisback/Universall/refs/heads/main/Testblade.lua", true))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Fade Hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Akirascripts/Lunar/refs/heads/main/LuanrOnTop"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Tab = Window:Tab({
	Name = "Da Hood",
	Icon = "rbxassetid://14134686133",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "Omen Hub key (codersocks.xyz)"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/mezzopera/Omen-Hub/main/omen_hub.lua"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Azure Modded"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Actyrn/Scripts/main/AzureModded"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Camlock (OP)"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://pastebin.com/raw/saz1c3k8"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Legit Blatant Cam (C)"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()getgenv().Howl = {
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
        Prediction = 0.116,
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

		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})


local Section1 = Tab:Section({
	Name = "sets ( THE DROPDOWN WONT AFFECT ANYTHING ITS THE SETS FOR YOUR PING)"
})

local Dropdown = Section1:Dropdown({
	Name = "Sets",
	Items = { "20 ping = 0.11", "40 ping = 0.11640 0.125 0.10070 0.10645 0.10734 0.10734 0.10734 0.10734 0.10734 0.10898 0.10929 0.10481 0.11152", "50-70 = 0.12337 0.12533 0.11243 0.11137", "80 ping = 0.165", "70-90 = 0.134379 0.14333 0.1433431 0.134143 0.1357", "140-170 ping = 0.16 0.15 0.1223333 0.125333 0.16779123 0.165455312399999", "200-300 ping = 0.1746 0.1567 0.1654 0.18321 0.1456 0.165561 0.12194 0.1651"},
	Callback = function(item)
		print(typeof(item))
		print(item)
	end
})

local Tab = Window:Tab({
	Name = "Arsenal",
	Icon = "rbxassetid://92153084773282",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "Leg Hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://pastebin.com/raw/G6Ubkkuv"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Quotas Hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/Insertl/QuotasHub/main/BETAv1.3"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "Tbao Hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/tbao143/thaibao/main/TbaoHubArsenal"))("https://t.me/KrutoySuslik")
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})


local Tab = Window:Tab({
	Name = "Blox Fruits",
	Icon = "rbxassetid://92153084773282",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "Gui"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://gitlab.com/littlekiller2927/deltacore/-/raw/main/deltabf.lua"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "mama hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/MAMAhub1/Mmahub/main/README.md"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Tab = Window:Tab({
	Name = "Rivals",
	Icon = "rbxassetid://92029816021311",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "25ms"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/cracklua/cracks/m/SilentRivals"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "God Hub (BEST WORKING not mine)"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://scriptblox.com/raw/UPD-RIVALS-OP-UPDATE-God-Hub-Silent-Aim-Chams-Undetected-Best-Script-17850"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Tab = Window:Tab({
	Name = "Combat Warriors",
	Icon = "rbxassetid://10012196756",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "Stratos Hub"
})

local Button = Section1:Button({
	Name = "Execute",
	Callback = function()loadstring(game:HttpGet("https://pastefy.app/50B4Z9UK/raw"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Tab = Window:Tab({
	Name = "Main",
	Icon = "rbxassetid://11396131982",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "General"
})

local Button = Section1:Button({
	Name = "Trash Talk (y)",
	Callback = function()local words = {
    'ur bad',
    'seed',
    'im not locking ur just bad',
    'kid im not locking XDXDXDXD ur just bad',
    'sad',
    'sonned',
    'how did u fail to get me',
}

local player = game.Players.LocalPlayer
local keybind = 'y'

local event = game.ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest

player:GetMouse().KeyDown:connect(function(key)
    if key == keybind then
        event:FireServer(words[math.random(#words)], "All")
    end
end)
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Button = Section1:Button({
	Name = "Fake Lim (V)",
	Callback = function()loadstring(game:HttpGet("https://raw.githubusercontent.com/y10ko/Niggaless/main/FE%20Headless%20%26%20Korblox",true))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section1 = Tab:Section({
	Name = "ESP"
})

local Button = Section1:Button({
	Name = "Esp Tracer",
	Callback = function()loadstring(game:HttpGet("https://pastebin.com/raw/c4FNAXCW"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Button = Section1:Button({
	Name = "Esp Box",
	Callback = function()loadstring(game:HttpGet("https://pastebin.com/raw/Cx4B9rNd"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Button = Section1:Button({
	Name = "Esp Health",
	Callback = function()loadstring(game:HttpGet("https://pastebin.com/raw/nq27eCVX"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Button = Section1:Button({
	Name = "Esp Name",
	Callback = function()loadstring(game:HttpGet("https://pastebin.com/raw/Nj4dG8CZ"))()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section2 = Tab:Section({
	Name = "More General"
})

local Button = Section2:Button({
	Name = "Anti Fling",
	Callback = function()local localPlayer = game:GetService('Players').LocalPlayer;
                local localCharacter = localPlayer.Character;
                localCharacter:FindFirstChildOfClass('Humanoid').Health = 0;
                local newCharacter = localPlayer.CharacterAdded:Wait();
                local spoofFolder = Instance.new('Folder');
                spoofFolder.Name = 'FULLY_LOADED_CHAR';
                spoofFolder.Parent = newCharacter;
                newCharacter:WaitForChild('RagdollConstraints'):Destroy();
                local spoofValue = Instance.new('BoolValue', newCharacter);
                spoofValue.Name = 'RagdollConstraints';
                local name = game.Players.LocalPlayer.Name
                local lol =    game.Workspace:WaitForChild(name)
                local money = Instance.new("Folder",game.Players.LocalPlayer.Character);money.Name = "FULLY_LOADED_CHAR"
                lol.Parent = game.Workspace.Players
                game.Players.LocalPlayer.Character:WaitForChild("BodyEffects")
                game.Players.LocalPlayer.Character.BodyEffects.BreakingParts:Destroy()
		Dropdown:Clear()
	end
})

local Button = Section2:Button({
	Name = "Rainbow Character",
	Callback = function()for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
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
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

Library:Notify({
	Name = "Test",
	Text = "This is just a test",
	Icon = "rbxassetid://11401835376",
	Duration = 3,
	Callback = function()
		Library:Notify({
			Name = "Em",
			Text = "Notify Callback",
			Icon = "rbxassetid://11401835376",
			Duration = 3,
		})
	end
})

local Tab = Window:Tab({
	Name = "Others",
	Icon = "rbxassetid://11476626403",
	Color = Color3.new(0.474509, 0.474509, 0.474509)
})

local Section = Tab:Section({
	Name = "Miscs"
})

local Button = Section:Button({
	Name = "Destroy library",
	Callback = function()
		Library:Destroy()
	end
})

local Button = Section:Button({
	Name = "Hide UI",
	Callback = function()
		Window:Toggled(false)
		
		task.wait(3)
		
		Window:Toggled(true)
	end
})

local Button = Section:Button({
	Name = "Task Bar Only",
	Callback = function()
		Window:TaskBarOnly(true)

		task.wait(3)

		Window:TaskBarOnly(false)
	end
})

local Keybind = Section:Keybind({
    Name = "Toggle keybind",
    Default = Enum.KeyCode.Return,
    Callback = function() return end,
    UpdateKeyCallback = function(Key)
		task.wait(0.1)
        Window:ChangeTogglekey(Key)
    end
})
