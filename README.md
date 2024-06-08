local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("MOUSETRAP - UNIVERSAL SCRIPT", "Synapse")
    -- MAIN
    local Main = Window:NewTab("Main")
    local MainSection = Main:NewSection("Main")

   MainSection:NewButton("Sword Reach [Equip Sword First!]", "AZLDFBIPAsKHOFALEJDS", function()
   loadstring(game:HttpGet(('https://raw.githubusercontent.com/Severitylol/Universal-Sword-Reach/main/swordreach.lua'),true))()
  end)




    local Aim = Main:NewSection("FunStuff")
   

  local plrss = Window:NewTab("Player")
    local plrsss = plrss:NewSection("Main")

  plrsss:NewButton("Fly [X] [v1.0]", "Make's You Fly", function()
        loadstring(game:HttpGet(('https://raw.githubusercontent.com/JST1BRA/dhfly/main/README.md'),true))()
    end)

    plrsss:NewButton("No-clip [B] [v1.0]", "Make's you clip through objects", function()
   loadstring(game:HttpGet(('https://pastebin.com/raw/XgxXzw5s'),true))()
  end)

 plrsss:NewButton("Infinite Jump", "NIGGA NINJA", function()
loadstring(game:HttpGet(('https://cdn.wearedevs.net/scripts/Infinite%20Jump.txt'),true))()
end)
  local plrssss = plrss:NewSection("Modifier's")

 plrssss:NewSlider("Walkspeed", "SPEED!!", 500, 16, function(s)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
    end)

    plrssss:NewSlider("Jumppower", "JUMP HIGH!!", 350, 50, function(s)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
    end)

    plrssss:NewButton("Reset WS/JP", "Resets walkspeed / jumpspower back", function()
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = 50
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
    end)


--Visuals/Aim
    local VisualsAim1 = Window:NewTab("Visuals/Aim")
    local VisualsAim2 = VisualsAim1:NewSection("Aim")
    local coreGui = game:GetService("CoreGui")
local drawing = coreGui.Drawing


 local aimbotLoaded = false
local toggle = VisualsAim2:NewToggle("Aimbot", "Right Clicking Locks Aim", function(state)
    if state then
        if not aimbotLoaded then
            loadstring(game:HttpGet(('https://pastebin.com/raw/ygp8Enye'), true))()
            aimbotLoaded = true
                 _G.CircleTransparency = 1
        end
        _G.AimbotEnabled = true
        _G.CircleTransparency = 1
    else
        _G.AimbotEnabled = false
        _G.CircleTransparency = 0
    end
end)

   
    
  
  VisualsAim2:NewToggle("TeamCheck", "TeamChecks The Aimbot aimpart Detection", function(state2)
    if state2 then
        _G.TeamCheck = true
    else
        _G.TeamCheck = false
    end
end)

VisualsAim2:NewSlider("AimSmth", "Aim Smoothing", 09, 0, function(as)
    _G.Sensitivity = as
end)







VisualsAim2:NewDropdown("Aimpart", "DropdownInf", {"Head", "Torso", "Right Leg", "Left Leg"}, function(aimpart)
_G.AimPart = aimpart
end)

  local VisualsAim3 = VisualsAim1:NewSection("Visuals")
  

       VisualsAim3:NewButton("ESP", "BEST ESP OUT THERE BY ME!", function()
       
 
		local function API_Check()
    if Drawing == nil then
        return "No"
    else
        return "Yes"
    end
end

local Find_Required = API_Check()

if Find_Required == "No" then
    game:GetService("StarterGui"):SetCore("SendNotification",{
        Title = "JSTESP";
        Text = "ESP script could not be loaded because your exploit is unsupported.";
        Duration = math.huge;
        Button1 = "OK"
    })

    return
end

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local Camera = workspace.CurrentCamera

local Typing = false

_G.SendNotifications = true   -- If set to true then the script would notify you frequently on any changes applied and when loaded / errored. (If a game can detect this, it is recommended to set it to false)
_G.DefaultSettings = false   -- If set to true then the ESP script would run with default settings regardless of any changes you made.

_G.TeamChecks = false   -- If set to true then the script would create ESP only for the enemy team members.

_G.ESPVisible = true   -- If set to true then the ESP will be visible and vice versa.
_G.TextColor = Color3.fromRGB(255, 255, 255)   -- The color that the boxes would appear as.
_G.TextSize = 14   -- The size of the text.
_G.Center = true   -- If set to true then the script would be located at the center of the label.
_G.Outline = true   -- If set to true then the text would have an outline.
_G.OutlineColor = Color3.fromRGB(0, 0, 0)   -- The outline color of the text.
_G.TextTransparency = 0.7   -- The transparency of the text.
_G.TextFont = Drawing.Fonts.UI   -- The font of the text. (UI, System, Plex, Monospace) 

_G.DisableKey = Enum.KeyCode.Q   -- The key that disables / enables the ESP.

local function CreateESP()
    for _, v in next, Players:GetPlayers() do
        if v.Name ~= Players.LocalPlayer.Name then
            local ESP = Drawing.new("Text")

            RunService.RenderStepped:Connect(function()
                if workspace:FindFirstChild(v.Name) ~= nil and workspace[v.Name]:FindFirstChild("HumanoidRootPart") ~= nil then
                    local Vector, OnScreen = Camera:WorldToViewportPoint(workspace[v.Name]:WaitForChild("Head", math.huge).Position)

                    ESP.Size = _G.TextSize
                    ESP.Center = _G.Center
                    ESP.Outline = _G.Outline
                    ESP.OutlineColor = _G.OutlineColor
                    ESP.Color = _G.TextColor
                    ESP.Transparency = _G.TextTransparency
                    ESP.Font = _G.TextFont

                    if OnScreen == true then
                        local Part1 = workspace:WaitForChild(v.Name, math.huge):WaitForChild("HumanoidRootPart", math.huge).Position
                        local Part2 = workspace:WaitForChild(Players.LocalPlayer.Name, math.huge):WaitForChild("HumanoidRootPart", math.huge).Position or 0
                        local Dist = (Part1 - Part2).Magnitude
                        ESP.Position = Vector2.new(Vector.X, Vector.Y - 25)
                        ESP.Text = ("("..tostring(math.floor(tonumber(Dist)))..") "..v.Name.." ["..workspace[v.Name].Humanoid.Health.."]")
                        if _G.TeamChecks == true then 
                            if Players.LocalPlayer.Team ~= v.Team then
                                ESP.Visible = _G.ESPVisible
                            else
                                ESP.Visible = false
                            end
                        else
                            ESP.Visible = _G.ESPVisible
                        end
                    else
                        ESP.Visible = false
                    end
                else
                    ESP.Visible = false
                end
            end)

            Players.PlayerRemoving:Connect(function()
                ESP.Visible = false
            end)
        end
    end

    Players.PlayerAdded:Connect(function(Player)
        Player.CharacterAdded:Connect(function(v)
            if v.Name ~= Players.LocalPlayer.Name then 
                local ESP = Drawing.new("Text")
    
                RunService.RenderStepped:Connect(function()
                    if workspace:FindFirstChild(v.Name) ~= nil and workspace[v.Name]:FindFirstChild("HumanoidRootPart") ~= nil then
                        local Vector, OnScreen = Camera:WorldToViewportPoint(workspace[v.Name]:WaitForChild("Head", math.huge).Position)
    
                        ESP.Size = _G.TextSize
                        ESP.Center = _G.Center
                        ESP.Outline = _G.Outline
                        ESP.OutlineColor = _G.OutlineColor
                        ESP.Color = _G.TextColor
                        ESP.Transparency = _G.TextTransparency
    
                        if OnScreen == true then
                            local Part1 = workspace:WaitForChild(v.Name, math.huge):WaitForChild("HumanoidRootPart", math.huge).Position
                        local Part2 = workspace:WaitForChild(Players.LocalPlayer.Name, math.huge):WaitForChild("HumanoidRootPart", math.huge).Position or 0
                            local Dist = (Part1 - Part2).Magnitude
                            ESP.Position = Vector2.new(Vector.X, Vector.Y - 25)
                            ESP.Text = ("("..tostring(math.floor(tonumber(Dist)))..") "..v.Name.." ["..workspace[v.Name].Humanoid.Health.."]")
                            if _G.TeamCheck == true then 
                                if Players.LocalPlayer.Team ~= Player.Team then
                                    ESP.Visible = _G.ESPVisible
                                else
                                    ESP.Visible = false
                                end
                            else
                                ESP.Visible = _G.ESPVisible
                            end
                        else
                            ESP.Visible = false
                        end
                    else
                        ESP.Visible = false
                    end
                end)
    
                Players.PlayerRemoving:Connect(function()
                    ESP.Visible = false
                end)
            end
        end)
    end)
end

if _G.DefaultSettings == true then
    _G.TeamChecks = false
    _G.ESPVisible = true
    _G.TextColor = Color3.fromRGB(255, 255, 255)
    _G.TextSize = 14
    _G.Center = true
    _G.Outline = false
    _G.OutlineColor = Color3.fromRGB(0, 0, 0)
    _G.DisableKey = Enum.KeyCode.Q
    _G.TextTransparency = 0.75
end

UserInputService.TextBoxFocused:Connect(function()
    Typing = true
end)

UserInputService.TextBoxFocusReleased:Connect(function()
    Typing = false
end)

UserInputService.InputBegan:Connect(function(Input)
    if Input.KeyCode == _G.DisableKey and Typing == false then
        _G.ESPVisible = not _G.ESPVisible
        
        if _G.SendNotifications == true then
            game:GetService("StarterGui"):SetCore("SendNotification",{
                Title = "Ibra the shit Developer";
                Text = "The ESP's visibility is now set to "..tostring(_G.ESPVisible)..".";
                Duration = 5;
            })
        end
    end
end)

local Success, Errored = pcall(function()
    CreateESP()
end)

if Success and not Errored then
    if _G.SendNotifications == true then
        game:GetService("StarterGui"):SetCore("SendNotification",{
            Title = "Ibra the shit Developer";
            Text = "ESP script has successfully loaded.";
            Duration = 5;
        })
    end
elseif Errored and not Success then
    if _G.SendNotifications == true then
        game:GetService("StarterGui"):SetCore("SendNotification",{
            Title = "Ibra the shit Developer";
            Text = "ESP script has errored while loading, please check the developer console! (F9)";
            Duration = 5;
        })
    end
    TestService:Message("The ESP script has errored, please notify Ibra the shit dev with the following information :")
    warn(Errored)
    print("!! IF THE ERROR IS A FALSE POSITIVE (says that a player cannot be found) THEN DO NOT BOTHER !!")
end
		local FillColor = Color3.fromRGB(175,25,255)
		local DepthMode = "AlwaysOnTop"
		local FillTransparency = 0.5
		local OutlineColor = Color3.fromRGB(255,255,255)
		local OutlineTransparency = 0
 
		local CoreGui = game:FindService("CoreGui")
		local Players = game:FindService("Players")
		local lp = Players.LocalPlayer
		local connections = {}
 
		local Storage = Instance.new("Folder")
		Storage.Parent = CoreGui
		Storage.Name = "Highlight_Storage"
 
		local function Highlight(plr)
			local Highlight = Instance.new("Highlight")
			Highlight.Name = plr.Name
			Highlight.FillColor = FillColor
			Highlight.DepthMode = DepthMode
			Highlight.FillTransparency = FillTransparency
			Highlight.OutlineColor = OutlineColor
			Highlight.OutlineTransparency = 0
			Highlight.Parent = Storage
 
			local plrchar = plr.Character
			if plrchar then
				Highlight.Adornee = plrchar
			end
 
			connections[plr] = plr.CharacterAdded:Connect(function(char)
				Highlight.Adornee = char
			end)
		end
 
		Players.PlayerAdded:Connect(Highlight)
		for i,v in next, Players:GetPlayers() do
			Highlight(v)
		end
 
		Players.PlayerRemoving:Connect(function(plr)
			local plrname = plr.Name
			if Storage[plrname] then
				Storage[plrname]:Destroy()
			end
			if connections[plr] then
				connections[plr]:Disconnect()
			end
		end)
 
 

end)

 VisualsAim3:NewSlider("Fov Size", "Change The Fov Circle Size From 500 to 23", 500, 23, function(fovsiza)
       _G.CircleRadius = fovsiza
    end)





  local Hubs = Window:NewTab("Other Hubs")
    local Hubstxt = Hubs:NewSection("Other Hubs")






    Hubstxt:NewButton("Vortex [da hood]", "Vortex", function()
      loadstring(game:HttpGet(('https://raw.githubusercontent.com/ImagineProUser/vortexdahood/main/vortex'),true))()
  end)


  Hubstxt:NewButton("ChariotsWare[hood mooded]", "ChariotsWare", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/Rippeed/DaHoodinary/main/chariotsware'),true))()
end)


  Hubstxt:NewButton("Winter Hub v2[Bloxfruit]", "bwoxfowuwts", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/Yatsuraa/Yuri/main/Winterhub_V2.lua'),true))()
end)

Hubstxt:NewButton("Owl Hub", "For Aimbot/ Esp", function()
  loadstring(game:HttpGet(('https://raw.githubusercontent.com/CriShoux/OwlHub/master/OwlHub.txt'),true))()
end)



Hubstxt:NewButton("IY Admin", "Universal Admin", function()
  loadstring(game:HttpGet(('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'),true))()
end)

Hubstxt:NewButton("M-V-S Gui", "MVSD", function()
  loadstring(game:HttpGet(('https://raw.githubusercontent.com/JST1BRA/mvs-skyze/main/README.md'),true))()
end)

 local FE = Window:NewTab("FE Fun [R6 / R15]")
    local FES = FE:NewSection("FE Fun [R6 / R15]")
    
   FES:NewButton("Backflip [X]", "Keybinded With [X]", function()
  loadstring(game:HttpGet(('https://pastebin.com/raw/7wDcPtLk'),true))()
end)

    FES:NewButton("Walk ON WALLS AND ROOF?", "SPIDOR MAM", function()
  loadstring(game:HttpGet(('https://pastebin.com/raw/zXk4Rq2r'),true))()
end)

   FES:NewButton("CHAT ADMIN!", "TROLL", function()
local a=Instance.new("ScreenGui")local b=Instance.new("Frame")local c=Instance.new("UICorner")local d=Instance.new("Frame")local e=Instance.new("UICorner")local f=Instance.new("Frame")local g=Instance.new("TextLabel")local h=Instance.new("TextButton")local i=Instance.new("UICorner")local j=Instance.new("TextLabel")local k=Instance.new("Frame")local l=Instance.new("UICorner")local m=Instance.new("Frame")local n=Instance.new("TextButton")local o=Instance.new("TextLabel")local p=Instance.new("ImageLabel")local q=Instance.new("UICorner")local r=Instance.new("TextLabel")local s=Instance.new("Frame")local t=Instance.new("UIListLayout")local u=Instance.new("TextButton")local v=Instance.new("UICorner")local w=Instance.new("UIPadding")local x=Instance.new("TextButton")local y=Instance.new("Frame")local z=Instance.new("UICorner")local A=Instance.new("TextBox")local B=Instance.new("Frame")local C=Instance.new("UICorner")local D=Instance.new("TextBox")local E=Instance.new("Frame")local F=Instance.new("TextButton")local G=Instance.new("ImageLabel")local H=Instance.new("UICorner")local I=Instance.new("Frame")local J=Instance.new("TextButton")local K=Instance.new("ImageLabel")local L=Instance.new("UICorner")local M=Instance.new("Frame")local N=Instance.new("UICorner")local O=Instance.new("Frame")local P=Instance.new("UICorner")local Q=Instance.new("Frame")local R=Instance.new("TextLabel")local S=Instance.new("Frame")local T=Instance.new("UICorner")local U=Instance.new("ScrollingFrame")local V=Instance.new("UIListLayout")local W=Instance.new("UIPadding")a.Name="ChatTroll"a.Parent=game:GetService("CoreGui")a.ZIndexBehavior=Enum.ZIndexBehavior.Sibling;a.DisplayOrder=67;a.ResetOnSpawn=false;b.Name="Main"b.Parent=a;b.BackgroundColor3=Color3.fromRGB(40,40,40)b.BorderSizePixel=0;b.ClipsDescendants=true;b.Position=UDim2.new(0.714853048,0,0.322327048,0)b.Size=UDim2.new(0,300,0,225)c.CornerRadius=UDim.new(0,12)c.Parent=b;d.Name="Top"d.Parent=b;d.BackgroundColor3=Color3.fromRGB(25,25,25)d.Size=UDim2.new(1,0,0,44)e.CornerRadius=UDim.new(0,12)e.Parent=d;f.Parent=d;f.BackgroundColor3=Color3.fromRGB(25,25,25)f.BorderSizePixel=0;f.Position=UDim2.new(0,0,1,-16)f.Size=UDim2.new(1,0,0,16)g.Name="Title"g.Parent=d;g.BackgroundColor3=Color3.fromRGB(255,255,255)g.BackgroundTransparency=1.000;g.BorderSizePixel=0;g.Position=UDim2.new(0,16,0.150000006,0)g.Size=UDim2.new(0,200,0.699999988,0)g.Font=Enum.Font.Gotham;g.Text="Chat Admin"g.TextColor3=Color3.fromRGB(255,255,255)g.TextScaled=true;g.TextSize=14.000;g.TextWrapped=true;g.TextXAlignment=Enum.TextXAlignment.Left;h.Name="Exit"h.Parent=d;h.BackgroundColor3=Color3.fromRGB(255,82,82)h.BorderSizePixel=0;h.Position=UDim2.new(0,270,0.5,-4)h.Size=UDim2.new(0,8,0,8)h.Font=Enum.Font.SourceSans;h.Text=""h.TextColor3=Color3.fromRGB(0,0,0)h.TextSize=14.000;i.CornerRadius=UDim.new(0,64)i.Parent=h;j.Name="Credits"j.Parent=b;j.BackgroundColor3=Color3.fromRGB(255,255,255)j.BackgroundTransparency=1.000;j.BorderSizePixel=0;j.Position=UDim2.new(0,0,1,-14)j.Size=UDim2.new(1,0,0,12)j.Font=Enum.Font.Gotham;j.Text="  "j.TextColor3=Color3.fromRGB(170,170,170)j.TextScaled=true;j.TextSize=14.000;j.TextWrapped=true;k.Name="Chat"k.Parent=b;k.BackgroundColor3=Color3.fromRGB(50,50,50)k.Position=UDim2.new(0,16,0,54)k.Size=UDim2.new(1,-32,0,150)l.Parent=k;m.Name="Dropdown"m.Parent=k;m.BackgroundColor3=Color3.fromRGB(30,30,30)m.BackgroundTransparency=1.000;m.Position=UDim2.new(0,8,0,8)m.Size=UDim2.new(1,-16,0,32)m.ZIndex=2;n.Name="Btn"n.Parent=m;n.BackgroundColor3=Color3.fromRGB(30,30,30)n.Size=UDim2.new(1,0,0,24)n.ZIndex=3;n.AutoButtonColor=false;n.Font=Enum.Font.SourceSans;n.Text=""n.TextColor3=Color3.fromRGB(0,0,0)n.TextSize=14.000;o.Name="Title"o.Parent=n;o.BackgroundColor3=Color3.fromRGB(255,255,255)o.BackgroundTransparency=1.000;o.Position=UDim2.new(0,10,0,0)o.Selectable=true;o.Size=UDim2.new(0,1,1,0)o.ZIndex=3;o.Font=Enum.Font.Gotham;o.Text="Chat System"o.TextColor3=Color3.fromRGB(255,255,255)o.TextSize=14.000;o.TextXAlignment=Enum.TextXAlignment.Left;p.Name="Ico"p.Parent=n;p.AnchorPoint=Vector2.new(1,0.5)p.BackgroundColor3=Color3.fromRGB(255,255,255)p.BackgroundTransparency=1.000;p.Position=UDim2.new(1,-10,0.5,0)p.Size=UDim2.new(0,20,0,20)p.ZIndex=3;p.Image="http://www.roblox.com/asset/?id=6034818379"p.ImageTransparency=0.400;q.CornerRadius=UDim.new(0,5)q.Parent=n;r.Name="Value"r.Parent=n;r.AnchorPoint=Vector2.new(1,0.5)r.BackgroundColor3=Color3.fromRGB(255,255,255)r.BackgroundTransparency=1.000;r.Position=UDim2.new(1,-35,0.5,0)r.Selectable=true;r.Size=UDim2.new(0,1,0,32)r.ZIndex=3;r.Font=Enum.Font.Gotham;r.Text="Dropdown"r.TextColor3=Color3.fromRGB(255,255,255)r.TextSize=14.000;r.TextTransparency=0.400;r.TextXAlignment=Enum.TextXAlignment.Right;s.Name="Holder"s.Parent=m;s.BackgroundColor3=Color3.fromRGB(36,36,36)s.BackgroundTransparency=1.000;s.ClipsDescendants=true;s.Position=UDim2.new(0,0,0,19)s.Size=UDim2.new(1,0,0,5)s.ZIndex=2;t.Name="Layout"t.Parent=s;t.SortOrder=Enum.SortOrder.LayoutOrder;u.Name="Legacy"u.Parent=s;u.BackgroundColor3=Color3.fromRGB(255,255,255)u.BackgroundTransparency=1.000;u.BorderColor3=Color3.fromRGB(27,42,53)u.BorderSizePixel=0;u.Size=UDim2.new(1,0,0,32)u.ZIndex=2;u.Font=Enum.Font.Gotham;u.Text="Legacy"u.TextColor3=Color3.fromRGB(255,255,255)u.TextSize=14.000;u.TextTransparency=0.400;v.CornerRadius=UDim.new(0,5)v.Parent=s;w.Parent=s;w.PaddingTop=UDim.new(0,5)x.Name="New"x.Parent=s;x.BackgroundColor3=Color3.fromRGB(255,255,255)x.BackgroundTransparency=1.000;x.BorderColor3=Color3.fromRGB(27,42,53)x.BorderSizePixel=0;x.Size=UDim2.new(1,0,0,32)x.ZIndex=2;x.Font=Enum.Font.Gotham;x.Text="New"x.TextColor3=Color3.fromRGB(255,255,255)x.TextSize=14.000;x.TextTransparency=0.400;y.Name="Real"y.Parent=k;y.BackgroundColor3=Color3.fromRGB(30,30,30)y.Position=UDim2.new(0,8,0,40)y.Size=UDim2.new(1,-16,0,24)z.CornerRadius=UDim.new(0,5)z.Parent=y;A.Parent=y;A.BackgroundColor3=Color3.fromRGB(255,255,255)A.BackgroundTransparency=1.000;A.BorderSizePixel=0;A.Position=UDim2.new(0,8,1,-19)A.Size=UDim2.new(1,-14,0,14)A.ClearTextOnFocus=false;A.Font=Enum.Font.Gotham;A.PlaceholderColor3=Color3.fromRGB(178,178,178)A.PlaceholderText="Put your disguise here"A.Text=""A.TextColor3=Color3.fromRGB(255,255,255)A.TextSize=14.000;A.TextWrapped=true;A.TextXAlignment=Enum.TextXAlignment.Left;B.Name="Fake"B.Parent=k;B.BackgroundColor3=Color3.fromRGB(30,30,30)B.Position=UDim2.new(0,8,0,71)B.Size=UDim2.new(1,-16,0,24)C.CornerRadius=UDim.new(0,5)C.Parent=B;D.Parent=B;D.BackgroundColor3=Color3.fromRGB(255,255,255)D.BackgroundTransparency=1.000;D.BorderSizePixel=0;D.Position=UDim2.new(0,8,1,-19)D.Size=UDim2.new(1,-16,0,14)D.ClearTextOnFocus=false;D.Font=Enum.Font.Gotham;D.MultiLine=true;D.PlaceholderText="Put the \"fake\" message here"D.Text=""D.TextColor3=Color3.fromRGB(255,255,255)D.TextScaled=true;D.TextSize=14.000;D.TextWrapped=true;D.TextXAlignment=Enum.TextXAlignment.Left;E.Name="Send"E.Parent=k;E.BackgroundColor3=Color3.fromRGB(30,30,30)E.BorderSizePixel=0;E.Position=UDim2.new(0,8,0,110)E.Size=UDim2.new(0.694029868,-16,0,32)F.Name="Btn"F.Parent=E;F.BackgroundColor3=Color3.fromRGB(30,30,30)F.BackgroundTransparency=1.000;F.Size=UDim2.new(1,0,1,0)F.Font=Enum.Font.Gotham;F.Text="Send"F.TextColor3=Color3.fromRGB(255,255,255)F.TextSize=14.000;H.CornerRadius=UDim.new(0,5)H.Parent=E;I.Name="Presets"I.Parent=k;I.BackgroundColor3=Color3.fromRGB(30,30,30)I.BorderSizePixel=0;I.Position=UDim2.new(0,185,0,110)I.Size=UDim2.new(0.339552253,-16,0,32)J.Name="Btn"J.Parent=I;J.BackgroundColor3=Color3.fromRGB(30,30,30)J.BackgroundTransparency=1.000;J.Size=UDim2.new(1,0,1,0)J.Font=Enum.Font.Gotham;J.Text="Presets"J.TextColor3=Color3.fromRGB(255,255,255)J.TextSize=14.000;L.CornerRadius=UDim.new(0,5)L.Parent=I;M.Name="Presets"M.Parent=a;M.BackgroundColor3=Color3.fromRGB(40,40,40)M.BorderSizePixel=0;M.ClipsDescendants=true;M.Position=UDim2.new(0.0452739783,0,0.322327048,0)M.Size=UDim2.new(0,174,0,225)N.CornerRadius=UDim.new(0,12)N.Parent=M;O.Name="Top"O.Parent=M;O.BackgroundColor3=Color3.fromRGB(25,25,25)O.Size=UDim2.new(1,0,0,44)P.CornerRadius=UDim.new(0,12)P.Parent=O;Q.Parent=O;Q.BackgroundColor3=Color3.fromRGB(25,25,25)Q.BorderSizePixel=0;Q.Position=UDim2.new(0,0,1,-16)Q.Size=UDim2.new(1,0,0,16)R.Name="Title"R.Parent=O;R.BackgroundColor3=Color3.fromRGB(255,255,255)R.BackgroundTransparency=1.000;R.BorderSizePixel=0;R.Position=UDim2.new(0,16,0.150000006,0)R.Size=UDim2.new(0,200,0.699999988,0)R.Font=Enum.Font.Gotham;R.Text="Presets"R.TextColor3=Color3.fromRGB(255,255,255)R.TextScaled=true;R.TextSize=14.000;R.TextWrapped=true;R.TextXAlignment=Enum.TextXAlignment.Left;S.Name="List"S.Parent=M;S.BackgroundColor3=Color3.fromRGB(50,50,50)S.Position=UDim2.new(0,16,0,58)S.Size=UDim2.new(1,-32,0,150)T.Parent=S;U.Parent=S;U.Active=true;U.BackgroundColor3=Color3.fromRGB(255,255,255)U.BackgroundTransparency=1.000;U.BorderSizePixel=0;U.Size=UDim2.new(1,-4,1,0)U.ScrollBarThickness=6;V.Parent=U;V.SortOrder=Enum.SortOrder.LayoutOrder;V.Padding=UDim.new(0,5)W.Parent=U;W.PaddingTop=UDim.new(0,5)local function X()local Y=Instance.new('LocalScript',b)local Z=game:GetService("UserInputService")local _=game:GetService("RunService")local a0=Y.Parent;local a1;local a2;local a3;local a4;function Lerp(a5,a6,a7)return a5+(a6-a5)*a7 end;local a8;local a9;local aa=8;function Update(ab)if not a4 then return end;if not a1 and a9 then a0.Position=UDim2.new(a4.X.Scale,Lerp(a0.Position.X.Offset,a9.X.Offset,ab*aa),a4.Y.Scale,Lerp(a0.Position.Y.Offset,a9.Y.Offset,ab*aa))return end;local ac=a8-Z:GetMouseLocation()local ad=a4.X.Offset-ac.X;local ae=a4.Y.Offset-ac.Y;a9=UDim2.new(a4.X.Scale,ad,a4.Y.Scale,ae)a0.Position=UDim2.new(a4.X.Scale,Lerp(a0.Position.X.Offset,ad,ab*aa),a4.Y.Scale,Lerp(a0.Position.Y.Offset,ae,ab*aa))end;a0.InputBegan:Connect(function(af)if af.UserInputType==Enum.UserInputType.MouseButton1 or af.UserInputType==Enum.UserInputType.Touch then a1=true;a3=af.Position;a4=a0.Position;a8=Z:GetMouseLocation()af.Changed:Connect(function()if af.UserInputState==Enum.UserInputState.End then a1=false end end)end end)a0.InputChanged:Connect(function(af)if af.UserInputType==Enum.UserInputType.MouseMovement or af.UserInputType==Enum.UserInputType.Touch then a2=af end end)_.Heartbeat:Connect(Update)end;coroutine.wrap(X)()local function ag()local Y=Instance.new('LocalScript',h)local ah=false;Y.Parent.MouseButton1Down:Connect(function()if ah==true then return end;ah=true;Y.Parent.Parent.Parent:TweenPosition(UDim2.new(.2,0,-1,-36))wait(1)Y.Parent.Parent.Parent.Parent:Destroy()end)end;coroutine.wrap(ag)()local function ai()local Y=Instance.new('LocalScript',F)local aj=game.Players.LocalPlayer:GetMouse()local function ak(al,am,an)coroutine.resume(coroutine.create(function()al.ClipsDescendants=true;local G=Y:WaitForChild("Circle"):Clone()G.Parent=al;local ao=am-G.AbsolutePosition.X;local ap=an-G.AbsolutePosition.Y;G.Position=UDim2.new(0,ao,0,ap)local aq=0;if al.AbsoluteSize.X>al.AbsoluteSize.Y then aq=al.AbsoluteSize.X*1.5 elseif al.AbsoluteSize.X<al.AbsoluteSize.Y then aq=al.AbsoluteSize.Y*1.5 elseif al.AbsoluteSize.X==al.AbsoluteSize.Y then aq=al.AbsoluteSize.X*1.5 end;local ar=0.5;G:TweenSizeAndPosition(UDim2.new(0,aq,0,aq),UDim2.new(0.5,-aq/2,0.5,-aq/2),"Out","Quad",ar,false,nil)for as=0.8,1,0.01 do G.ImageTransparency=as;wait(ar/10)end;G:Destroy()end))end;Y.Parent.MouseButton1Down:connect(function()ak(Y.Parent,aj.X,aj.Y)end)end;coroutine.wrap(ai)()local function at()local Y=Instance.new('LocalScript',k)local au;local function av(ah)Y.Parent.Dropdown.Btn.Value.Text=ah.Text;au=ah.Name;if au=="Legacy"then Y.Parent.Fake.TextBox.MultiLine=false elseif au=="New"then Y.Parent.Fake.TextBox.MultiLine=true end end;if game:GetService("TextChatService").ChatVersion==Enum.ChatVersion.TextChatService then av(Y.Parent.Dropdown.Holder.New)else av(Y.Parent.Dropdown.Holder.Legacy)end;local aw=false;local ax=false;Y.Parent.Dropdown.Btn.MouseButton1Down:Connect(function()if ax==true then return end;ax=true;if aw==false then Y.Parent.Dropdown.Holder.Transparency=0;coroutine.wrap(function()for as=0,180,10 do Y.Parent.Dropdown.Btn.Ico.Rotation=as;wait()end end)()local ay=0;for as,ah in pairs(Y.Parent.Dropdown.Holder:GetChildren())do if ah:IsA("TextButton")then ay=ay+1 end end;Y.Parent.Dropdown.Holder:TweenSize(UDim2.new(1,0,0,10+32*ay))wait(1)else coroutine.wrap(function()for as=180,0,-10 do Y.Parent.Dropdown.Btn.Ico.Rotation=as;wait()end end)()Y.Parent.Dropdown.Holder:TweenSize(UDim2.new(1,0,0,5))wait(1)Y.Parent.Dropdown.Holder.Transparency=1 end;aw=not aw;ax=false end)for as,ah in pairs(Y.Parent.Dropdown.Holder:GetChildren())do if ah:IsA("TextButton")then ah.MouseButton1Down:Connect(function()av(ah)end)end end;Y.Parent.Send.Btn.MouseButton1Down:Connect(function()local az=Y.Parent.Real.TextBox.Text;local aA=Y.Parent.Fake.TextBox.Text;if au=="New"then aA=string.gsub(aA,"\n","\r")game:GetService("TextChatService").TextChannels.RBXGeneral:SendAsync(az..'\r'..aA)elseif au=="Legacy"then game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(az..string.sub("                                                                                                                                                           ",#az)..aA,"All")end end)Y.Parent.Parent.Parent.Presets.Visible=false;Y.Parent.Presets.Btn.MouseButton1Down:Connect(function()Y.Parent.Parent.Parent.Presets.Visible=not Y.Parent.Parent.Parent.Presets.Visible end)end;coroutine.wrap(at)()local function aB()local Y=Instance.new('LocalScript',J)local aj=game.Players.LocalPlayer:GetMouse()local function ak(al,am,an)coroutine.resume(coroutine.create(function()al.ClipsDescendants=true;local G=Y:WaitForChild("Circle"):Clone()G.Parent=al;local ao=am-G.AbsolutePosition.X;local ap=an-G.AbsolutePosition.Y;G.Position=UDim2.new(0,ao,0,ap)local aq=0;if al.AbsoluteSize.X>al.AbsoluteSize.Y then aq=al.AbsoluteSize.X*1.5 elseif al.AbsoluteSize.X<al.AbsoluteSize.Y then aq=al.AbsoluteSize.Y*1.5 elseif al.AbsoluteSize.X==al.AbsoluteSize.Y then aq=al.AbsoluteSize.X*1.5 end;local ar=0.5;G:TweenSizeAndPosition(UDim2.new(0,aq,0,aq),UDim2.new(0.5,-aq/2,0.5,-aq/2),"Out","Quad",ar,false,nil)for as=0.8,1,0.01 do G.ImageTransparency=as;wait(ar/10)end;G:Destroy()end))end;Y.Parent.MouseButton1Down:connect(function()ak(Y.Parent,aj.X,aj.Y)end)end;coroutine.wrap(aB)()local function aC()local Y=Instance.new('LocalScript',M)local Z=game:GetService("UserInputService")local _=game:GetService("RunService")local a0=Y.Parent;local a1;local a2;local a3;local a4;function Lerp(a5,a6,a7)return a5+(a6-a5)*a7 end;local a8;local a9;local aa=8;function Update(ab)if not a4 then return end;if not a1 and a9 then a0.Position=UDim2.new(a4.X.Scale,Lerp(a0.Position.X.Offset,a9.X.Offset,ab*aa),a4.Y.Scale,Lerp(a0.Position.Y.Offset,a9.Y.Offset,ab*aa))return end;local ac=a8-Z:GetMouseLocation()local ad=a4.X.Offset-ac.X;local ae=a4.Y.Offset-ac.Y;a9=UDim2.new(a4.X.Scale,ad,a4.Y.Scale,ae)a0.Position=UDim2.new(a4.X.Scale,Lerp(a0.Position.X.Offset,ad,ab*aa),a4.Y.Scale,Lerp(a0.Position.Y.Offset,ae,ab*aa))end;a0.InputBegan:Connect(function(af)if af.UserInputType==Enum.UserInputType.MouseButton1 or af.UserInputType==Enum.UserInputType.Touch then a1=true;a3=af.Position;a4=a0.Position;a8=Z:GetMouseLocation()af.Changed:Connect(function()if af.UserInputState==Enum.UserInputState.End then a1=false end end)end end)a0.InputChanged:Connect(function(af)if af.UserInputType==Enum.UserInputType.MouseMovement or af.UserInputType==Enum.UserInputType.Touch then a2=af end end)_.Heartbeat:Connect(Update)end;coroutine.wrap(aC)()G.Name="Circle"G.Parent=J:WaitForChild("LocalScript")G.BackgroundColor3=Color3.fromRGB(255,255,255)G.BackgroundTransparency=1.000;G.ZIndex=10;G.Image="rbxassetid://266543268"G.ImageColor3=Color3.fromRGB(0,0,0)G.ImageTransparency=0.800;K.Name="Circle"K.Parent=F:WaitForChild("LocalScript")K.BackgroundColor3=Color3.fromRGB(255,255,255)K.BackgroundTransparency=1.000;K.ZIndex=10;K.Image="rbxassetid://266543268"K.ImageColor3=Color3.fromRGB(0,0,0)K.ImageTransparency=0.800;local aD=Instance.new("TextButton")aD.Parent=U;aD.BackgroundColor3=Color3.fromRGB(255,255,255)aD.BackgroundTransparency=1.000;aD.BorderSizePixel=0;aD.Size=UDim2.new(1,-10,0,12)aD.Font=Enum.Font.Gotham;aD.Text="Fake admin all"aD.TextColor3=Color3.fromRGB(255,255,255)aD.TextScaled=true;aD.TextSize=14.000;aD.TextWrapped=true;aD.MouseButton1Down:Connect(function()y.TextBox.Text=";admin all"B.TextBox.Text="{Team} You are now on the 'Admins' team."end)local aD=Instance.new("TextButton")aD.Parent=U;aD.BackgroundColor3=Color3.fromRGB(255,255,255)aD.BackgroundTransparency=1.000;aD.BorderSizePixel=0;aD.Size=UDim2.new(1,-10,0,12)aD.Font=Enum.Font.Gotham;aD.Text="Fake shutdown"aD.TextColor3=Color3.fromRGB(255,255,255)aD.TextScaled=true;aD.TextSize=14.000;aD.TextWrapped=true;aD.MouseButton1Down:Connect(function()y.TextBox.Text=";shutdown"B.TextBox.Text="[Server]: Shutting down in 60 seconds"end)local aD=Instance.new("TextButton")aD.Parent=U;aD.BackgroundColor3=Color3.fromRGB(255,255,255)aD.BackgroundTransparency=1.000;aD.BorderSizePixel=0;aD.Size=UDim2.new(1,-10,0,12)aD.Font=Enum.Font.Gotham;aD.Text="Team join"aD.TextColor3=Color3.fromRGB(255,255,255)aD.TextScaled=true;aD.TextSize=14.000;aD.TextWrapped=true;aD.MouseButton1Down:Connect(function()y.TextBox.Text=""B.TextBox.Text="{Team} You are now on the 'put anything here' team."end)local aD=Instance.new("TextButton")aD.Parent=U;aD.BackgroundColor3=Color3.fromRGB(255,255,255)aD.BackgroundTransparency=1.000;aD.BorderSizePixel=0;aD.Size=UDim2.new(1,-10,0,12)aD.Font=Enum.Font.Gotham;aD.Text="System message"aD.TextColor3=Color3.fromRGB(255,255,255)aD.TextScaled=true;aD.TextSize=14.000;aD.TextWrapped=true;aD.MouseButton1Down:Connect(function()y.TextBox.Text=""B.TextBox.Text="[Server]: "end)
end)

 local cred = Window:NewTab("Credits")
    local creds = cred:NewSection("Credits")
    creds:NewLabel("Scripiter: JST1bra_ [Discord]")   
     creds:NewLabel("Idea / Made For: skyzeeeeee [Discord]")

 




