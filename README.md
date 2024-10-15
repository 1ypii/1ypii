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
	Icon = "rbxassetid://91824404097371",
	Color = Color3.new(1, 0, 0)
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
	Name = "Main",
	Icon = "rbxassetid://11396131982",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "General"
})

local Button = Section1:Button({
	Name = "Trash Talk",
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
	Name = "Update dropdown",
	Callback = function()
		Dropdown:UpdateList({
			Items = {"bruh", 1, 2, 3},
			Replace = true
		})
	end
})

local Button = Section2:Button({
	Name = "Additem",
	Callback = function()
		Dropdown:AddItem("Item")
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
