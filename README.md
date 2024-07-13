loadstring(game:HttpGet("https://raw.githubusercontent.com/deeeity/mercury-lib/master/src.lua"))()
local Mercury = loadstring(game:HttpGet("https://raw.githubusercontent.com/deeeity/mercury-lib/master/src.lua"))()

local GUI = Mercury:Create{
    Name = "MOUSETRAP",
    Size = UDim2.fromOffset(600, 400),
    Theme = Mercury.Themes.Dark,
    Link = nil
}

GUI:Notification{
	Title = "MOUSETRAP - ~ i h !",
	Text = "Welcome to MOUSETRAP a Universal script for almost any game made by ~ i h !",
	Duration = 8,
	Callback = function() end
}


local Main = GUI:Tab{
	Name = "Main",
	Icon = "rbxassetid://8569322835"
}


local FUN = GUI:Tab{
	Name = "Fun R6/R15",
	Icon = "rbxassetid://8569322835"
}


local OtherHubs = GUI:Tab{
	Name = "OtherHubs",
	Icon = "rbxassetid://8569322835"
}

Main:Keybind{
    Name = "Toggle Menu",
    Keybind = Enum.KeyCode.LeftAlt, 
    Description = "Toggle the main menu",
    Callback = function()
     
        GUI:Toggle()
    end
}
Main:Button{
	Name = "IY Admin",
	Description = nil,
	Callback = function() 
       loadstring(game:HttpGet(('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'),true))()
    end
}

Main:Textbox{
	Name = "Player",
	Callback = function(text) end
}

Main:Textbox{
	Name = "Visuals",
	Callback = function(text) end
}

FUN:Button{
	Name = "Spidorman",
	Description = nil,
	Callback = function() 
 loadstring(game:HttpGet(('https://pastebin.com/raw/zXk4Rq2r'),true))()
    end
}
FUN:Button{
	Name = "Backflip",
	Description = nil,
	Callback = function() 
 loadstring(game:HttpGet(('https://pastebin.com/raw/7wDcPtLk'),true))()
    end
}

OtherHubs:Button{
	Name = "Blade Ball",
	Description = nil,
	Callback = function() 
loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/5ebefab5c68bfa67271dcbf6430d3c7d.lua"))()
    end
}

OtherHubs:Button{
	Name = "Blox Fruits",
	Description = nil,
	Callback = function() 
 loadstring(game:HttpGet(('https://raw.githubusercontent.com/Yatsuraa/Yuri/main/Winterhub_V2.lua'),true))()
    end
}

OtherHubs:Button{
	Name = "Owl Hub",
	Description = nil,
	Callback = function() 
 loadstring(game:HttpGet(('https://raw.githubusercontent.com/CriShoux/OwlHub/master/OwlHub.txt'),true))()
    end
}

OtherHubs:Button{
	Name = "M-V-S GUI",
	Description = nil,
	Callback = function() 
  loadstring(game:HttpGet(('https://raw.githubusercontent.com/JST1BRA/mvs-skyze/main/README.md'),true))()
    end
}

OtherHubs:Button{
	Name = "Da Hood [Vortex]",
	Description = nil,
	Callback = function() 
loadstring(game:HttpGet(('https://raw.githubusercontent.com/ImagineProUser/vortexdahood/main/vortex'),true))()
    end
}

OtherHubs:Button{
	Name = "Hood Modded [Chariotsware]",
	Description = nil,
	Callback = function() 
 loadstring(game:HttpGet(('https://raw.githubusercontent.com/Rippeed/DaHoodinary/main/chariotsware'),true))()
    end
}
