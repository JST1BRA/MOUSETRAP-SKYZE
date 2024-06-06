local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("MOUSETRAP - UNIVERSAL SCRIPT FOR SKYZE", "Synapse")
    -- MAIN
    local Main = Window:NewTab("Da Hood")
    local MainSection = Main:NewSection("Da Hood")


    
  MainSection:NewButton("Fly [X]", "Make's You Fly", function()
        loadstring(game:HttpGet(('https://raw.githubusercontent.com/JST1BRA/dhfly/main/README.md'),true))()
    end)

    MainSection:NewButton("No-clip [B]", "Make's you clip through objects", function()
   loadstring(game:HttpGet(('https://pastebin.com/raw/XgxXzw5s'),true))()
  end)


  MainSection:NewButton("Melee Reach [Bad For Now]", "Melee Reach", function()
        loadstring(game:HttpGet(('https://pastebin.com/raw/bKCGkuai'),true))()
    end)

    local Aim = Main:NewSection("Aim")
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

Hubstxt:NewButton("Owl Hub", "For Aimbot/ Esp", function()
  loadstring(game:HttpGet(('https://raw.githubusercontent.com/CriShoux/OwlHub/master/OwlHub.txt'),true))()
end)



Hubstxt:NewButton("IY Admin", "Universal Admin", function()
  loadstring(game:HttpGet(('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'),true))()
end)

 local FE = Window:NewTab("FE Fun [R6 / R15]")
    local FES = FE:NewSection("Other Hubs")
    
   FES:NewButton("Backflip [X]", "Keybinded With [X]", function()
  loadstring(game:HttpGet(('https://pastebin.com/raw/7wDcPtLk'),true))()
end)

    FES:NewButton("[Failed PROJECT]Anti Tag [USE ON ALT MAY BAN!]", "USE ON ALT!", function()
  loadstring(game:HttpGet(('https://raw.githubusercontent.com/Synergy-Networks/products/main/BetterBypasser/loader.lua'),true))()
end)
