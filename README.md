local Library = loadstring(game:HttpGet('https://raw.githubusercontent.com/Loco-CTO/UI-Library/main/VisionLibV2/source.lua'))()

Window = Library:Create({
	Name = "Axafy Gui",
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

local Tab = Window:Tab({
	Name = "Da Hood",
	Icon = "rbxassetid://92153084773282",
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


local Tab = Window:Tab({
	Name = "Main",
	Icon = "rbxassetid://11396131982",
	Color = Color3.new(1, 0, 0)
})

local Section1 = Tab:Section({
	Name = "Basic controls"
})

local Button = Section1:Button({
	Name = "Button",
	Callback = function()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Toggle = Section1:Toggle({
	Name = "Toggle",
	Default = false,
	Callback = function(Bool) 
		Library:Notify({
			Name = "Toggle",
			Text = tostring(Bool),
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})


local Section1 = Tab:Section({
	Name = "Basic controls"
})

local Button = Section1:Button({
	Name = "Button",
	Callback = function()
		Library:Notify({
			Name = "Button",
			Text = "Clicked",
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Toggle = Section1:Toggle({
	Name = "Toggle",
	Default = false,
	Callback = function(Bool) 
		Library:Notify({
			Name = "Toggle",
			Text = tostring(Bool),
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Section2 = Tab:Section({
	Name = "Advance controls"
})

local Slider = Section2:Slider({
	Name = "Slider",
	Max = 50,
	Min = 0,
	Default = 25,
	Callback = function(Number)
		Library:Notify({
			Name = "Slider",
			Text = tostring(Number),
			Icon = "rbxassetid://11401835376",
			Duration = 3
		})
	end
})

local Keybind = Section2:Keybind({
	Name = "Keybind",
	Default = Enum.KeyCode.Return,
	Callback = function()
		Library:Notify({
			Name = "Keybind pressed",
			Text = "Idk sth here",
			Icon = "rbxassetid://11401835376",
			Duration = 3,
		})
	end,
	UpdateKeyCallback = function(Key)
		Library:Notify({
			Name = "Keybind updated",
			Text = tostring(Key),
			Icon = "rbxassetid://11401835376",
			Duration = 3,
		})
	end
})

local SmallTextbox = Section2:SmallTextbox({
	Name = "Small Textbox",
	Default = "Default Text",
	Callback = function(Text)
		Library:Notify({
			Name = "Small Textbox updated",
			Text = Text,
			Icon = "rbxassetid://11401835376",
			Duration = 3,
		})
	end
})

local Dropdown = Section2:Dropdown({
	Name = "Dropdown",
	Items = {1, 2, 3, 4, "XD"},
	Callback = function(item)
		print(typeof(item))
		print(item)
	end
})

local Button = Section2:Button({
	Name = "Clear dropdown",
	Callback = function()
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
