local Player = game.Players.LocalPlayer
local UserIDs = {1154089477, 1389731546}  -- Apenas os UserIDs específicos
local Names = {"Gdseilano", "Comical983"}  -- Apenas os nomes específicos

if not (table.find(UserIDs, Player.UserId) or table.find(Names, Player.Name)) then
    game.Players.LocalPlayer.Backpack.ServerTraits.ChatAdvance:FireServer("Yes")
    task.wait(.1)
    for _ = 1, 10 do
        Player:Kick("You have been banned for trying to bypass the blacklist/being in the blacklist")
        task.wait(.3)
    end
end

local ka = Instance.new("Part")
ka.Name = "b"
ka.Parent = game.Workspace

game.Players.LocalPlayer.Chatted:Connect(function(cht)
    if string.lower(cht) == "-god" or string.find(string.lower(cht), "-god") then
        game:GetService("ReplicatedStorage").ResetChar:FireServer()
        for i = 1, 20, 1 do
            game.Players.LocalPlayer.Backpack.ServerTraits.Input:FireServer({"decrease"}, true)
        end
        task.wait(.350)
        if game.Players.LocalPlayer.character:FindFirstChild("Killed") and game.Players.LocalPlayer.character:FindFirstChild("Action") then
            game.Players.LocalPlayer.character.Killed:Destroy()
            game.Players.LocalPlayer.character.Action:Destroy()
        end
        game.Players.LocalPlayer.Backpack.ServerTraits.Transform:FireServer("h")
        for i = 1, 20, 1 do
            game.Players.LocalPlayer.Backpack.ServerTraits.Input:FireServer({"increase"}, true)
        end
    end
end)
coroutine.resume(b)
