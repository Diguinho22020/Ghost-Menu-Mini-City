--Config do Script
local Window = OrionLib:MakeWindow({Name = "👾 Ghost Menu Roleplay/Eb 👾", HidePremium = false, SaveConfig = true, IntroEnabled = false})
local Player = game.Players.LocalPlayer

OrionLib:MakeNotification({
    Name = "Bem-vindo no Ghost Menu!",
    Content = "Dirvita-se usando Ghost Menu. Bem-Vindo."..Player.Name.." ",
    Image = "rbxassetid://7733715400",
    Time = 5
})

--Valores _G. Para desativar ou desativar ou parte da key/texto
_G.Aimbot = true
_G.Loop = true
_G.Key = "KeyPedroxz"
_G.KeyInput = "string"

--Funcao do anti algema
function Algema()
	while _G.Algema == true do
				local event = game:GetService("ReplicatedStorage").Arrest
		local distance = 10
		 
		 
		event.OnServerEvent:Connect(function(policeman, arrested) -- when the event gets fired, the server will do the following commands:
			if(arrested.Team ~= game.Teams.Police) then --if the player's team is not police then
				if(policeman:DistanceFromCharacter(arrested.Character:WaitForChild("HumanoidRootPart").Position) > distance) then
					return nil
				end
				if(arrested.BadArea.Value == true and arrested.Team == game.Teams.Prisoners) then --If he is a prisoner in the area he is not allowed to.
					arrested.Character:WaitForChild("Humanoid").WalkSpeed = 0 --Set the arrested person walk speed to 0
					arrested.Character:WaitForChild("Humanoid").JumpPower = 0 --Set the arrested person jump power to 0
					local clone1 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made
					local clone2 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made again
					clone1.Parent = arrested.Character --Set it's parent to the character
					clone2.Parent = arrested.Character --Set it's parent to the character
					local motor = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d and set it's parent to the character
					local motor2 = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d again and set it's parent to the character
					motor.Part0 = arrested.Character.LeftHand --The part0 of the motor 6d is the leftHand
					motor.Part1 = clone1 --The part0 of the motor 6d is the handcuff clone 1
					motor2.Part0 = arrested.Character.RightHand --The part0 of the motor 6d 2 is the rightHand
					motor2.Part1 = clone2 --The part0 of the motor 6d 3 is the handcuff clone 2
					local chain = Instance.new("RopeConstraint", arrested.Character) --Create a new rope constraint inside the character
					local atta1 = Instance.new("Attachment", clone1) --Create a new attachment inside the clone1
					local atta2 = Instance.new("Attachment", clone2)--Create a new attachment inside the clone2
					chain.Length = 1 --Set the rope's length to 1
					chain.Thickness = 0.2 --Set the rope's thickness to 0.2
					chain.Attachment0 = atta1 --The rope's attachment 1 is the atta1 attachment
					chain.Attachment1 = atta2 --The rope's attachment 2 is the atta2 attachment
					chain.Color = BrickColor.new("Light stone grey") --Set the rope color to gray
					chain.Visible = true --Make it visible
					arrested.BadArea.Value = false
					game.ReplicatedStorage.ArrestAnim:FireClient(arrested) --Fire the client fromthe event we created
					wait(6) --Cooldown between arresting and playing animation
					arrested.Team = game.Teams.Prisoners --change the team of the player to prisoner
					arrested:LoadCharacter() --respawn him
				elseif(arrested.Team == game.Teams.Criminals) then  --If he is a criminal, the area he is inside does not matter, he will get arrested
					arrested.Character:WaitForChild("Humanoid").WalkSpeed = 0 --Set the arrested person walk speed to 0
					arrested.Character:WaitForChild("Humanoid").JumpPower = 0 --Set the arrested person jump power to 0
					local clone1 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made
					local clone2 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made again
					clone1.Parent = arrested.Character --Set it's parent to the character
					clone2.Parent = arrested.Character --Set it's parent to the character
					local motor = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d and set it's parent to the character
					local motor2 = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d again and set it's parent to the character
					motor.Part0 = arrested.Character.LeftHand --The part0 of the motor 6d is the leftHand
					motor.Part1 = clone1 --The part0 of the motor 6d is the handcuff clone 1
					motor2.Part0 = arrested.Character.RightHand --The part0 of the motor 6d 2 is the rightHand
					motor2.Part1 = clone2 --The part0 of the motor 6d 3 is the handcuff clone 2
					local chain = Instance.new("RopeConstraint", arrested.Character) --Create a new rope constraint inside the character
					local atta1 = Instance.new("Attachment", clone1) --Create a new attachment inside teh clone1
					local atta2 = Instance.new("Attachment", clone2)--Create a new attachment inside teh clone2
					chain.Length = 1 --Set the rope's length to 1
					chain.Thickness = 0.2 --Set the rope's thickness to 0.2
					chain.Attachment0 = atta1 --The rope's attachment 1 is the atta1 attachment
					chain.Attachment1 = atta2 --The rope's attachment 2 is the atta2 attachment
					chain.Color = BrickColor.new("Light stone grey") --Set the rope color to gray
					chain.Visible = true --Make it visible
					game.ReplicatedStorage.ArrestAnim:FireClient(arrested) --Fire the client fromthe event we created
					arrested.BadArea.Value = false
					wait(6) --Cooldown between arresting and playing animation
					arrested.Team = game.Teams.Prisoners --change the team of the player to prisoner
					arrested:LoadCharacter() --respawn him
				end
			end
		end)
	end
	end

--Funcao do Control tp 
function ControlTP()
	while _G.ControlTP == true do
		local UIS = game:GetService("UserInputService")
