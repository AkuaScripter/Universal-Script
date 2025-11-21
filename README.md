local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
    Name = " Universal Script ",
    LoadingTitle = "Vulcano Hub",
    LoadingSubtitle = "by Bacon_manden167",
    ConfigurationSaving = {
        Enabled = false,
        FolderName = nil,
        FileName = "VulcanoHub"
    },
    Discord = {
        Enabled = true,
        Invite = "BdgpWkCBuW",
        RememberJoins = true
    },
    KeySystem = true,
    KeySettings = {
        Title = "Universal Script | key",
        Subtitle = "Link In Discord Server",
        Note = "Join our Discord to get the weekly key:\nhttps://discord.gg/BdgpWkCBuW",
        FileName = "vulcan0hubkey",
        SaveKey = false, -- Don't save key locally, so every account can use a fresh key
        GrabKeyFromSite = true,
        Key = {"https://raw.githubusercontent.com/AkuaScripter/Universel-Key/refs/heads/main/Universel%20Key"}
    }
})

-- Notification for Discord invite
Rayfield:Notify({
    Title = "Discord Required",
    Content = "You need to join our Discord to get the key!",
    Duration = 10,
    Actions = {
        Okay = {
            Name = "Okay",
            Callback = function()
                local function copyToClipboard(text)
                    if setclipboard then
                        setclipboard(text)
                    elseif write_clipboard then
                        write_clipboard(text)
                    elseif toclipboard then
                        toclipboard(text)
                    else
                        warn("Clipboard not supported in this executor")
                    end
                end
                copyToClipboard("https://discord.gg/BdgpWkCBuW")
                Rayfield:Notify({
                    Title = "Copied!",
                    Content = "Discord invite copied to clipboard.",
                    Duration = 3
                })
            end
        },
        No = {
            Name = "No",
            Callback = function()
                -- Close notification
            end
        }
    }
})

-- Main Tab
local MainTab = Window:CreateTab("Main", nil)
local MainSection = MainTab:CreateSection("Main")

-- Infinite Jump Button
MainTab:CreateButton({
   Name = "Infinite Jump",
   Callback = function()
       _G.infinjump = not _G.infinjump

       if _G.infinJumpStarted == nil then
           _G.infinJumpStarted = true

           game.StarterGui:SetCore("SendNotification", {
               Title = "Youtube Hub";
               Text = "Infinite Jump Activated!";
               Duration = 5,
           })

           local plr = game:GetService("Players").LocalPlayer
           local m = plr:GetMouse()

           m.KeyDown:Connect(function(k)
               if _G.infinjump and k:byte() == 32 then
                   local humanoid = plr.Character:FindFirstChildOfClass("Humanoid")
                   if humanoid then
                       humanoid:ChangeState("Jumping")
                       wait()
                       humanoid:ChangeState("Seated")
                   end
               end
           end)
       end
   end,
})
