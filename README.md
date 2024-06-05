local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("MOUSETRAP - Skyze", "Synapse")
    -- MAIN
    local Main = Window:NewTab("Main")
    local MainSection = Main:NewSection("Main")


    
  MainSection:NewButton("Fly [X]", "Make's You Fly", function()
        loadstring(game:HttpGet(('https://raw.githubusercontent.com/JST1BRA/dhfly/main/README.md'),true))()
    end)

    MainSection:NewButton("No-clip [B]", "Make's you clip through objects", function()
   loadstring(game:HttpGet(('https://pastebin.com/raw/XgxXzw5s'),true))()
  end)


  MainSection:NewButton("Melee Reach [Bad For Now]", "Melee Reach", function()
        loadstring(game:HttpGet(('https://pastebin.com/raw/bKCGkuai'),true))()
    end)

    local Aim = Window:NewTab("Aim")
    local Aim = Aim:NewSection("Aim")
    Aim:NewButton("Aimlock [Q]", "Aimlock[indev] ", function()
      loadstring(game:HttpGet(('https://raw.githubusercontent.com/RapperDeluxe/scripts/main/Silent%20Aimlock%20Da%20Hood'),true))()
  end)

  local Hubs = Window:NewTab("Other Hubs")
    local Hubstxt = Hubs:NewSection("Other Hubs")

    Hubstxt:NewButton("Vortex", "Vortex", function()
      loadstring(game:HttpGet(('https://raw.githubusercontent.com/ImagineProUser/vortexdahood/main/vortex'),true))()
  end)


  Hubstxt:NewButton("ChariotsWare", "ChariotsWare", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/Rippeed/DaHoodinary/main/chariotsware'),true))()
end)

Hubstxt:NewButton("Soon", "Soon", function()
  --loadstring(game:HttpGet(('https://raw.githubusercontent.com/Rippeed/DaHoodinary/main/chariotsware'),true))()
end)



    
