game:GetService("StarterGui"):SetCore("SendNotification",{
	Title = "Loading"
	Text = "Loading", -- Required
	Icon = "rbxthumb://type=Asset&id=829639164&w=150&h=150" -- Optional
})
wait(2)
game:GetService("StarterGui"):SetCore("SendNotification",{
	Title = "Loading", -- Required
	Text = "Loading Data...", -- Required
	Icon = "rbxthumb://type=Asset&id=829639164&w=150&h=150" -- Optional
})
wait(2)
game:GetService("StarterGui"):SetCore("SendNotification",{
	Title = "Game Found", -- Required
	Text = "Da Hood", -- Required
	Icon = "rbxthumb://type=Asset&id=829639164&w=150&h=150" -- Optional
})
wait(1)
local StarterGui = game:GetService("StarterGui") -- not sure why you used CoreGui
local bindable1 = Instance.new("BindableFunction")
local bindable2 = Instance.new("BindableFunction")

function bindable1.OnInvoke(response)
setclipboard('https://discord.gg/yAgPmXDruY')
end

function bindable2.OnInvoke(response)
print("-- Made By ALT1LR")
end

StarterGui:SetCore("SendNotification", {
	Title = "Discord",
	Text = "Join Discord",
	Duration = 999999,
	Callback = bindable1,
	Button1 = "Sure!",
	Callback = bindable2,
	Button2 = "No Thanks",
})
wait(3)
L_1_ = "t"
local L_2_ = game.Players.LocalPlayer:GetMouse()
L_2_.KeyDown:Connect(function(L_22_arg0)
	if L_22_arg0 == L_1_ then
		if DaHoodSettings.SilentAim == true then
			DaHoodSettings.SilentAim = false
		else
			DaHoodSettings.SilentAim = true
		end
	end
end)

game:GetService("RunService").RenderStepped:Connect(
    function()
	for L_23_forvar0, L_24_forvar1 in pairs(game.CoreGui:GetChildren()) do
		if L_24_forvar1.Name == "PostmansAutoRob" then
			L_24_forvar1:Destroy()
		end
	end
	for L_25_forvar0, L_26_forvar1 in pairs(game.CoreGui:GetChildren()) do
		if L_26_forvar1.Name == "WarningGUI" then
			L_26_forvar1:Destroy()
		end
	end
end)

wait(3)
local Library = loadstring(game:HttpGet("https://pastebin.com/raw/vff1bQ9F"))()
local Window = Library.CreateLib("FireHood", "Serpent")

local Tab1 = Window:NewTab("Main")
local Tab1Section = Tab1:NewSection("Main Script")

Tab1Section:NewToggle("Spam Call", "Spam Call Everyone", function(state)
    if state then
getgenv().SpamCall = true

local plrs = game:GetService("Players")
local phone = game:GetService("ReplicatedStorage").MainEvent
local RunService = game:GetService("RunService")

if getgenv().SpamCall then
    local deez = RunService.RenderStepped:Connect(function()
        if getgenv().SpamCall == false then
            deez:Disconnect()
        end
        for i,v in pairs(plrs:GetPlayers()) do
            phone:FireServer("PhoneCall", v.Name)
        end
    end)
end
    else
getgenv().SpamCall = false

local plrs = game:GetService("Players")
local phone = game:GetService("ReplicatedStorage").MainEvent
local RunService = game:GetService("RunService")

if getgenv().SpamCall then
    local deez = RunService.RenderStepped:Connect(function()
        if getgenv().SpamCall == false then
            deez:Disconnect()
        end
        for i,v in pairs(plrs:GetPlayers()) do
            phone:FireServer("PhoneCall", v.Name)
        end
    end)
end
    end
end)

Tab1Section:NewButton("Reset", "Reset", function()
loadstring(game:HttpGet('https://pastebin.com/raw/Zr25UEXi'))()
end)

Tab1Section:NewButton("No Slow", "Anti Slow", function()
local lplayer = game.Players.LocalPlayer

game:GetService('RunService').Stepped:Connect(function()
   pcall(function()
       lplayer.Character.BodyEffects.Movement:ClearAllChildren()
   end)
end)
end)

Tab1Section:NewButton("Fly [Q]", "Fly Pc", function()
local plr = game.Players.LocalPlayer
local mouse = plr:GetMouse()

localplayer = plr

if workspace:FindFirstChild("Core") then
workspace.Core:Destroy()
end

local Core = Instance.new("Part")
Core.Name = "Core"
Core.Size = Vector3.new(0.05, 0.05, 0.05)

spawn(function()
Core.Parent = workspace
local Weld = Instance.new("Weld", Core)
Weld.Part0 = Core
Weld.Part1 = localplayer.Character.LowerTorso
Weld.C0 = CFrame.new(0, 0, 0)
end)

workspace:WaitForChild("Core")

local torso = workspace.Core
flying = true
local speed=10
local keys={a=false,d=false,w=false,s=false}
local e1
local e2
local function start()
local pos = Instance.new("BodyPosition",torso)
local gyro = Instance.new("BodyGyro",torso)
pos.Name="EPIXPOS"
pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
pos.position = torso.Position
gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
gyro.cframe = torso.CFrame
repeat
wait()
localplayer.Character.Humanoid.PlatformStand=true
local new=gyro.cframe - gyro.cframe.p + pos.position
if not keys.w and not keys.s and not keys.a and not keys.d then
speed=5
end
if keys.w then
new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
speed=speed+0
end
if keys.s then
new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
speed=speed+0
end
if keys.d then
new = new * CFrame.new(speed,0,0)
speed=speed+0
end
if keys.a then
new = new * CFrame.new(-speed,0,0)
speed=speed+0
end
if speed>10 then
speed=5
end
pos.position=new.p
if keys.w then
gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(-math.rad(speed*0),0,0)
elseif keys.s then
gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(math.rad(speed*0),0,0)
else
gyro.cframe = workspace.CurrentCamera.CoordinateFrame
end
until flying == false
if gyro then gyro:Destroy() end
if pos then pos:Destroy() end
flying=false
localplayer.Character.Humanoid.PlatformStand=false
speed=10
end
e1=mouse.KeyDown:connect(function(key)
if not torso or not torso.Parent then flying=false e1:disconnect() e2:disconnect() return end
if key=="w" then
keys.w=true
elseif key=="s" then
keys.s=true
elseif key=="a" then
keys.a=true
elseif key=="d" then
keys.d=true
elseif key=="q" then
if flying==true then
flying=false
else
flying=true
start()
end
end
end)
e2=mouse.KeyUp:connect(function(key)
if key=="w" then
keys.w=false
elseif key=="s" then
keys.s=false
elseif key=="a" then
keys.a=false
elseif key=="d" then
keys.d=false
end
end)
start()
end)

Tab1Section:NewButton("Fly V2", "Fly Gui", function()
-- Gui to Lua
-- Version: 3.2

-- Instances:

local main = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local up = Instance.new("TextButton")
local down = Instance.new("TextButton")
local onof = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")
local plus = Instance.new("TextButton")
local speed = Instance.new("TextLabel")
local mine = Instance.new("TextButton")

--Properties:

main.Name = "main"
main.Parent = game.CoreGui
main.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = main
Frame.BackgroundColor3 = Color3.fromRGB(163, 255, 137)
Frame.BorderColor3 = Color3.fromRGB(103, 221, 213)
Frame.Position = UDim2.new(0.100320168, 0, 0.379746825, 0)
Frame.Size = UDim2.new(0, 190, 0, 57)

up.Name = "up"
up.Parent = Frame
up.BackgroundColor3 = Color3.fromRGB(79, 255, 152)
up.Size = UDim2.new(0, 44, 0, 28)
up.Font = Enum.Font.SourceSans
up.Text = "UP"
up.TextColor3 = Color3.fromRGB(0, 0, 0)
up.TextSize = 14.000

down.Name = "down"
down.Parent = Frame
down.BackgroundColor3 = Color3.fromRGB(215, 255, 121)
down.Position = UDim2.new(0, 0, 0.491228074, 0)
down.Size = UDim2.new(0, 44, 0, 28)
down.Font = Enum.Font.SourceSans
down.Text = "DOWN"
down.TextColor3 = Color3.fromRGB(0, 0, 0)
down.TextSize = 14.000

onof.Name = "onof"
onof.Parent = Frame
onof.BackgroundColor3 = Color3.fromRGB(255, 249, 74)
onof.Position = UDim2.new(0.702823281, 0, 0.491228074, 0)
onof.Size = UDim2.new(0, 56, 0, 28)
onof.Font = Enum.Font.SourceSans
onof.Text = "fly"
onof.TextColor3 = Color3.fromRGB(0, 0, 0)
onof.TextSize = 14.000

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(242, 60, 255)
TextLabel.Position = UDim2.new(0.469327301, 0, 0, 0)
TextLabel.Size = UDim2.new(0, 100, 0, 28)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "FireHood"
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextScaled = true
TextLabel.TextSize = 12.000
TextLabel.TextWrapped = true

plus.Name = "plus"
plus.Parent = Frame
plus.BackgroundColor3 = Color3.fromRGB(133, 145, 255)
plus.Position = UDim2.new(0.231578946, 0, 0, 0)
plus.Size = UDim2.new(0, 45, 0, 28)
plus.Font = Enum.Font.SourceSans
plus.Text = "+"
plus.TextColor3 = Color3.fromRGB(0, 0, 0)
plus.TextScaled = true
plus.TextSize = 14.000
plus.TextWrapped = true

speed.Name = "speed"
speed.Parent = Frame
speed.BackgroundColor3 = Color3.fromRGB(255, 85, 0)
speed.Position = UDim2.new(0.468421042, 0, 0.491228074, 0)
speed.Size = UDim2.new(0, 44, 0, 28)
speed.Font = Enum.Font.SourceSans
speed.Text = "1"
speed.TextColor3 = Color3.fromRGB(0, 0, 0)
speed.TextScaled = true
speed.TextSize = 14.000
speed.TextWrapped = true

mine.Name = "mine"
mine.Parent = Frame
mine.BackgroundColor3 = Color3.fromRGB(123, 255, 247)
mine.Position = UDim2.new(0.231578946, 0, 0.491228074, 0)
mine.Size = UDim2.new(0, 45, 0, 29)
mine.Font = Enum.Font.SourceSans
mine.Text = "-"
mine.TextColor3 = Color3.fromRGB(0, 0, 0)
mine.TextScaled = true
mine.TextSize = 14.000
mine.TextWrapped = true

speeds = 1

local speaker = game:GetService("Players").LocalPlayer

local chr = game.Players.LocalPlayer.Character
local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")

nowe = false

Frame.Active = true -- main = gui
Frame.Draggable = true

onof.MouseButton1Down:connect(function()

	if nowe == true then
		nowe = false

		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Climbing,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Flying,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Landed,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Running,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics,true)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Swimming,true)
		speaker.Character.Humanoid:ChangeState(Enum.HumanoidStateType.RunningNoPhysics)
	else 
		nowe = true



		for i = 1, speeds do
			spawn(function()

				local hb = game:GetService("RunService").Heartbeat	


				tpwalking = true
				local chr = game.Players.LocalPlayer.Character
				local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
				while tpwalking and hb:Wait() and chr and hum and hum.Parent do
					if hum.MoveDirection.Magnitude > 0 then
						chr:TranslateBy(hum.MoveDirection)
					end
				end

			end)
		end
		game.Players.LocalPlayer.Character.Animate.Disabled = true
		local Char = game.Players.LocalPlayer.Character
		local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

		for i,v in next, Hum:GetPlayingAnimationTracks() do
			v:AdjustSpeed(0)
		end
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Climbing,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Flying,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Landed,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Running,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics,false)
		speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Swimming,false)
		speaker.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Swimming)
	end




	
		local plr = game.Players.LocalPlayer
		local UpperTorso = plr.Character.LowerTorso
		local flying = true
		local deb = true
		local ctrl = {f = 0, b = 0, l = 0, r = 0}
		local lastctrl = {f = 0, b = 0, l = 0, r = 0}
		local maxspeed = 50
		local speed = 0


		local bg = Instance.new("BodyGyro", UpperTorso)
		bg.P = 9e4
		bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
		bg.cframe = UpperTorso.CFrame
		local bv = Instance.new("BodyVelocity", UpperTorso)
		bv.velocity = Vector3.new(0,0.1,0)
		bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
		if nowe == true then
			plr.Character.Humanoid.PlatformStand = true
		end
		while nowe == true or game:GetService("Players").LocalPlayer.Character.Humanoid.Health == 0 do
			wait()

			if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then
				speed = speed+.5+(speed/maxspeed)
				if speed > maxspeed then
					speed = maxspeed
				end
			elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then
				speed = speed-1
				if speed < 0 then
					speed = 0
				end
			end
			if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
				lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r}
			elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
			else
				bv.velocity = Vector3.new(0,0,0)
			end

			bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0)
		end
		ctrl = {f = 0, b = 0, l = 0, r = 0}
		lastctrl = {f = 0, b = 0, l = 0, r = 0}
		speed = 0
		bg:Destroy()
		bv:Destroy()
		plr.Character.Humanoid.PlatformStand = false
		game.Players.LocalPlayer.Character.Animate.Disabled = false
		tpwalking = false



	





end)


up.MouseButton1Down:connect(function()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,2,0)
	
end)


down.MouseButton1Down:connect(function()

	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,-2,0)

end)


game:GetService("Players").LocalPlayer.CharacterAdded:Connect(function(char)
	wait(0.7)
	game.Players.LocalPlayer.Character.Humanoid.PlatformStand = false
	game.Players.LocalPlayer.Character.Animate.Disabled = false

end)


plus.MouseButton1Down:connect(function()
	speeds = speeds + 1
	speed.Text = speeds
	if nowe == true then
		

	tpwalking = false
	for i = 1, speeds do
		spawn(function()

			local hb = game:GetService("RunService").Heartbeat	


			tpwalking = true
			local chr = game.Players.LocalPlayer.Character
			local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
			while tpwalking and hb:Wait() and chr and hum and hum.Parent do
				if hum.MoveDirection.Magnitude > 0 then
					chr:TranslateBy(hum.MoveDirection)
				end
			end

		end)
		end
		end
end)
mine.MouseButton1Down:connect(function()
	if speeds == 1 then
		speed.Text = 'can not be less than 1'
		wait(1)
		speed.Text = speeds
	else
	speeds = speeds - 1
		speed.Text = speeds
		if nowe == true then
	tpwalking = false
	for i = 1, speeds do
		spawn(function()

			local hb = game:GetService("RunService").Heartbeat	


			tpwalking = true
			local chr = game.Players.LocalPlayer.Character
			local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
			while tpwalking and hb:Wait() and chr and hum and hum.Parent do
				if hum.MoveDirection.Magnitude > 0 then
					chr:TranslateBy(hum.MoveDirection)
				end
			end

		end)
		end
		end
		end
end)
end)

Tab1Section:NewTextBox("Shazam Fly [X]", "Shazam Fly", function(txt)
_G.ShazamFlySpeed = txt
loadstring(game:HttpGet(("https://raw.githubusercontent.com/Raycodex/Exploiting/main/Roblox/DaHoodShazamFly"), true))()
end)

local Tab1Section = Tab1:NewSection("Other")

Tab1Section:NewButton("Inf Zoom", "Inf Zoom", function()
game.Players.LocalPlayer.CameraMaxZoomDistance = (9999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999)
end)

Tab1Section:NewButton("Click Tp [E]", "Press Q To Tp Where Your Cursur At ", function()
plr = game.Players.LocalPlayer

hum = plr.Character.HumanoidRootPart

mouse = plr:GetMouse()



mouse.KeyDown:connect(function(key)

if key == "e" then

if mouse.Target then

hum.CFrame = CFrame.new(mouse.Hit.x, mouse.Hit.y + 5, mouse.Hit.z)

end

end
end)
end)

Tab1Section:NewButton("Headless Visual/Not Fe/People Cant See", "Headless", function()
game.Players.LocalPlayer.Character.Head.Transparency = 1
for i,v in pairs(game.Players.LocalPlayer.Character.Head:GetChildren()) do
if (v:IsA("Decal")) then
v:Destroy()
end
end
end)

Tab1Section:NewButton("Korblox Visual/Not Fe/Peoe Cant See", "Korblox", function()
local ply = game.Players.LocalPlayer
        local chr = ply.Character
        chr.RightLowerLeg.MeshId = "902942093"
        chr.RightLowerLeg.Transparency = "1"
        chr.RightUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
        chr.RightUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
        chr.RightFoot.MeshId = "902942089"
        chr.RightFoot.Transparency = "1"
end)

Tab1Section:NewButton("Rejoin", "Rejoim", function()
game:GetService'TeleportService':TeleportToPlaceInstance(game.PlaceId,game.JobId,game:GetService'Players'.LocalPlayer)
end)

Tab1Section:NewButton("Chat Spy", "Can See All Chat", function()
loadstring(game:HttpGet('https://pastebin.com/raw/TBRu2TW5'))()
end)

Tab1Section:NewButton("Anti Lag", "Anti Lag", function()
loadstring(game:HttpGet('https://pastebin.com/raw/Av2rdcUp'))()
end)

Tab1Section:NewButton("No Fogs", "Remove Night And Fogs", function()
loadstring(game:HttpGet("https://pastebin.com/raw/06iG6YkU", true))()
end)

Tab1Section:NewButton("Animation Pack", "Animation Packs", function()
     -- // clone
            for _, v in next, game:GetService("CoreGui"):GetChildren() do
                if (v.Name:match("FreeAnimationPack")) then
                    v:Destroy()
                end
            end
        
            -- // Instances
            local FreeAnimationPack = Instance.new("ScreenGui")
            local AnimationPack = Instance.new("TextButton")
            local Animations = Instance.new("ScrollingFrame")
            local UIListLayout = Instance.new("UIListLayout")
            local Lean = Instance.new("TextButton")
            local Lay = Instance.new("TextButton")
            local Dance1 = Instance.new("TextButton")
            local Dance2 = Instance.new("TextButton")
            local Greet = Instance.new("TextButton")
            local ChestPump = Instance.new("TextButton")
            local Praying = Instance.new("TextButton")
            local Stop = Instance.new("TextButton")
            local UniversalAnimation = Instance.new("Animation")
        
            -- // Utility
            function stopTracks()
                for _, v in next, game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):GetPlayingAnimationTracks() do
                    if (v.Animation.AnimationId:match("rbxassetid")) then
                        v:Stop()
                    end
                end
            end
        
            function loadAnimation(id)
                if UniversalAnimation.AnimationId == id then
                    stopTracks()
                    UniversalAnimation.AnimationId = "1"
                else
                    UniversalAnimation.AnimationId = id
                    local animationTrack = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):LoadAnimation(UniversalAnimation)
                    animationTrack:Play()
                end
            end
        

            FreeAnimationPack.Name = "FreeAnimationPack"
            FreeAnimationPack.Parent = game.CoreGui
            FreeAnimationPack.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
        
            AnimationPack.Name = "AnimationPack"
            AnimationPack.Parent = FreeAnimationPack
            AnimationPack.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            AnimationPack.BorderSizePixel = 0
            AnimationPack.Position = UDim2.new(0, 0, 0.388007045, 0)
            AnimationPack.Size = UDim2.new(0, 100, 0, 20)
            AnimationPack.Font = Enum.Font.SourceSansBold
            AnimationPack.Text = "Animations"
            AnimationPack.TextColor3 = Color3.fromRGB(0, 0, 0)
            AnimationPack.TextSize = 18.000
            AnimationPack.MouseButton1Click:Connect(function()
                if (Animations.Visible == false) then
                    Animations.Visible = true
                end
            end)
        
            Animations.Name = "Animations"
            Animations.Parent = AnimationPack
            Animations.Active = true
            Animations.BackgroundColor3 = Color3.fromRGB(102, 102, 102)
            Animations.Position = UDim2.new(-0.104712225, 0, -1.54173493, 0)
            Animations.Size = UDim2.new(0, 120, 0, 195)
            Animations.Visible = false
            Animations.CanvasPosition = Vector2.new(0, 60.0000305)
            Animations.CanvasSize = UDim2.new(0, 0, 1, 235)
        
            UIListLayout.Parent = Animations
            UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
            UIListLayout.Padding = UDim.new(0, 2)
        
            Lean.Name = "Lean"
            Lean.Parent = Animations
            Lean.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            Lean.Size = UDim2.new(1, 0, 0, 30)
            Lean.Font = Enum.Font.SourceSansBold
            Lean.Text = "Lean"
            Lean.TextColor3 = Color3.fromRGB(0, 0, 0)
            Lean.TextSize = 14.000
            Lean.MouseButton1Click:Connect(function()
                stopTracks()
                loadAnimation("rbxassetid://3152375249")
            end)
        
            Lay.Name = "Lay"
            Lay.Parent = Animations
            Lay.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            Lay.Size = UDim2.new(1, 0, 0, 30)
            Lay.Font = Enum.Font.SourceSansBold
            Lay.Text = "Lay"
            Lay.TextColor3 = Color3.fromRGB(0, 0, 0)
            Lay.TextSize = 14.000
            Lay.MouseButton1Click:Connect(function()
                stopTracks()
                loadAnimation("rbxassetid://3152378852")
            end)
        
            Dance1.Name = "Dance1"
            Dance1.Parent = Animations
            Dance1.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            Dance1.Size = UDim2.new(1, 0, 0, 30)
            Dance1.Font = Enum.Font.SourceSansBold
            Dance1.Text = "Dance1"
            Dance1.TextColor3 = Color3.fromRGB(0, 0, 0)
            Dance1.TextSize = 14.000
            Dance1.MouseButton1Click:Connect(function()
                stopTracks()
                loadAnimation("rbxassetid://3189773368")
            end)
        
            Dance2.Name = "Dance2"
            Dance2.Parent = Animations
            Dance2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            Dance2.Size = UDim2.new(1, 0, 0, 30)
            Dance2.Font = Enum.Font.SourceSansBold
            Dance2.Text = "Dance2"
            Dance2.TextColor3 = Color3.fromRGB(0, 0, 0)
            Dance2.TextSize = 14.000
            Dance2.MouseButton1Click:Connect(function()
                stopTracks()
                loadAnimation("rbxassetid://3189776546")
            end)
        
            Greet.Name = "Greet"
            Greet.Parent = Animations
            Greet.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            Greet.Size = UDim2.new(1, 0, 0, 30)
            Greet.Font = Enum.Font.SourceSansBold
            Greet.Text = "Greet"
            Greet.TextColor3 = Color3.fromRGB(0, 0, 0)
            Greet.TextSize = 14.000
            Greet.MouseButton1Click:Connect(function()
                stopTracks()
                loadAnimation("rbxassetid://3189777795")
            end)
        
            ChestPump.Name = "ChestPump"
            ChestPump.Parent = Animations
            ChestPump.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            ChestPump.Size = UDim2.new(1, 0, 0, 30)
            ChestPump.Font = Enum.Font.SourceSansBold
            ChestPump.Text = "Chest Pump"
            ChestPump.TextColor3 = Color3.fromRGB(0, 0, 0)
            ChestPump.TextSize = 14.000
            ChestPump.MouseButton1Click:Connect(function()
                stopTracks()
                loadAnimation("rbxassetid://3189779152")
            end)
        
            Praying.Name = "Praying"
            Praying.Parent = Animations
            Praying.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            Praying.Size = UDim2.new(1, 0, 0, 30)
            Praying.Font = Enum.Font.SourceSansBold
            Praying.Text = "Praying"
            Praying.TextColor3 = Color3.fromRGB(0, 0, 0)
            Praying.TextSize = 14.000
            Praying.MouseButton1Click:Connect(function()
                stopTracks()
                loadAnimation("rbxassetid://3487719500")
            end)
        
            Stop.Name = "Stop"
            Stop.Parent = Animations
            Stop.BackgroundColor3 = Color3.fromRGB(255, 112, 112)
            Stop.Size = UDim2.new(1, 0, 0, 30)
            Stop.Font = Enum.Font.SourceSansBold
            Stop.Text = "Stop Animation"
            Stop.TextColor3 = Color3.fromRGB(0, 0, 0)
            Stop.TextSize = 14.000
            Stop.MouseButton1Click:Connect(function()
                stopTracks()
            end)
            --close gui
            local plr = game.Players.LocalPlayer
        
            plr:GetMouse().KeyDown:Connect(function(K)
                if K == "p" then
                    Animations.Visible = false
                end
            end)
        warn("loaded")
end)

local Tab2 = Window:NewTab("Teleport")
local Tab2Section = Tab2:NewSection("Safe Zone")

Tab2Section:NewButton("Safe Zone", "ButtonInfo", function()
Instance.new('Part',workspace)
Local = game:GetService('Players').LocalPlayer
Char  = Local.Character
touched,tpdback = false, false
Local.CharacterAdded:connect(function(char)
   if script.Disabled ~= true then
       wait(.25)
       loc = Char.HumanoidRootPart.Position
       Char:MoveTo(box.Position + Vector3.new(0,.5,0))
   end
end)
game:GetService('UserInputService').InputBegan:connect(function(key)
   if key.KeyCode == Enum.KeyCode.Equals then
       if script.Disabled ~= true then
           script.Disabled = true
           print'you may re-execute'
       end
   end
end)
box = Instance.new('Part',workspace)
box.Anchored = true
box.CanCollide = true
box.Size = Vector3.new(180,1,180)
box.Position = Vector3.new(-5018,0909761,180)

game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-5018,0909761,180)
end)

local Tab2Section = Tab2:NewSection("Teleport")

Tab2Section:NewButton("Club", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-264.688, 48.4979, -464.715)
end)

Tab2Section:NewButton("Shop", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-210.014, 21.7262, -822.8)
end)

Tab2Section:NewButton("Casino", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-904.107, 21.2262, -175.944)
end)

Tab2Section:NewButton("Bank", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-424, 23, -284)
end)

Tab2Section:NewButton("Admin Base", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-871, -38.428, -589)
end)

Tab2Section:NewButton("Subway 1", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-422, -2, -33)
end)

Tab2Section:NewButton("Subway 2", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(598, 47, -114)
end)

Tab2Section:NewButton("UFO", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(77, 138.971, -670)
end)

Tab2Section:NewButton("FoodShop 1", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-343, 23, -298)
end)

Tab2Section:NewButton("FoodShop 2", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(300, 49, -609)
end)

Tab2Section:NewButton("Gunshop 1", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-578, 8, -737)
end)

Tab2Section:NewButton("GunShop 2", "Teleport", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(481, 48, -620)
end)

Tab2Section:NewButton("PlayGround", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-259.516907, 22.1498718, -762.971558, 0.992310345, 0, 0.12377467, 0, 1, 0, -0.12377467, 0, 0.992310345)
end)

Tab2Section:NewButton("Rev", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-611.63, 19.451, -94.571)
end)

Tab2Section:NewButton("Bat", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(380.932, 44.318, -284.746)
end)

Tab2Section:NewButton("Gas Station", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(591.6807250976562, 48.9980583190918, -256.81829833984375)
end)

Tab2Section:NewButton("Unknow Base", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-117.2702865600586, -58.702049255371094, 146.5360870361328)
end)

Tab2Section:NewButton("All Gun [1]", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-797.5016479492188, -39.651187896728516, -908.5286254882812)
end)

Tab2Section:NewButton("All Gun [2]", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-872.4907836914062, -38.401187896728516, -549.1875610351562)
end)

Tab2Section:NewButton("Admin Base Entrance", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-438.9405212402344, 7.3987932205200195, -884.9732055664062)
end)

Tab2Section:NewButton("Meeting Room {Admin Base}", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1013.4916381835938, -51.15618896484375, -1014.1583862304688)
end)

Tab2Section:NewButton("Furniture", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-490.1666564941406, 21.74802017211914, -125.82877349853516)
end)

Tab2Section:NewButton("Trailor", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-951.6024780273438, -4.776987552642822, 450.8782653808594)
end)

Tab2Section:NewButton("Key", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-271.0005798339844, 21.74802017211914, -246.9978790283203)
end)

Tab2Section:NewButton("Taco", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(546.946533203125, 51.05942153930664, -493.3235168457031)
end)

Tab2Section:NewButton("Park", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(360.9668884277344, 48.49801254272461, -522.9868774414062)
end)

Tab2Section:NewButton("Skate Park", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-825.6868286132812, 21.99785041809082, -549.29345703125)
end)

Tab2Section:NewButton("Circus", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(142.00022888183594, 24.753023147583008, -988.0001220703125)
end)

Tab2Section:NewButton("Casino", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-879.2764282226562, 21.25301742553711, -190.19729614257812)
end)

Tab2Section:NewButton("Theate", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1004.6754150390625, 24.52411460876465, -159.90626525878906)
end)

Tab2Section:NewButton("High Scool", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-652, 21.748016357421875, 255)
end)

Tab2Section:NewButton("Grave Yard", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(195.79640197753906, 21.748022079467773, 26.965106964111328)
end)

Tab2Section:NewButton("Basket Ball", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-931.841064453125, 22.097841262817383, -483.786376953125)
end)

Tab2Section:NewButton("Admin Base Outside", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-415.55523681640625, 8.261791229248047, -881.5380859375)
end)

Tab2Section:NewButton("Cave Entrance", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-270.5617980957031, 21.99802017211914, 36.32166290283203)
end)

Tab2Section:NewButton("Jail 1", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-309.0919494628906, 21.797962188720703, -68.69635009765625)
end)

Tab2Section:NewButton("Jail 2", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-310.9031066894531, 21.797962188720703, -111.92225646972656)
end)

Tab2Section:NewButton("High Medium Armor", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-934.2291259765625, -28.501983642578125, 566.6146240234375)
end)

Tab2Section:NewButton("Medium 1", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-604.1194458007812, 10.347713470458984, -788.4752197265625)
end)

Tab2Section:NewButton("Medium 2", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(534.0569458007812, 50.3223991394043, -637.0626220703125)
end)

Tab2Section:NewButton("Hospital", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(89.29714965820312, 21.753023147583008, -485.1397399902344)
end)

Tab2Section:NewButton("Sewer Entrance 2", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-59.28953170776367, -25.732601165771484, -317.2185363769531)
end)

Tab2Section:NewButton("FireWorks", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-836.8599853515625, 21.798032760620117, -297.0146484375)
end)

Tab2Section:NewButton("Barber Shop", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(13.999297142028809, 21.74802017211914, -117.76170349121094)
end)

Tab2Section:NewButton("Phone Store", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-136.20201110839844, 21.753023147583008, -870.7710571289062)
end)

Tab2Section:NewButton("Hood Fitness", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-76.01471710205078, 21.753023147583008, -602.6604614257812)
end)

Tab2Section:NewButton("Da Hood Boxing Clubs", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-216.01211547851562, 21.753023147583008, -1120.3731689453125)
end)

Tab2Section:NewButton("Flame Thrower", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-153.95590209960938, 53.80862808227539, -97.92117309570312)
end)

local Tab2Section = Tab2:NewSection("Recomended Tp")

Tab2Section:NewButton("Church", "Tp", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(205, 21.74802017211914, -82)
end)

Tab2Section:NewDropdown("Teleports", "Teleports", {"Church", "Flame Thrower", "Boxing Clubs", "Hood Fitness", "Phone Store", "Barber Shop", "FireWorks", "Sewer Entrance 2", "Hospital", "Medium Armor 2", "Medium Armor 2", "High Medium Armor", }, function(currentOption)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(205, 21.74802017211914, -82)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-153.95590209960938, 53.80862808227539, -97.92117309570312)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-216.01211547851562, 21.753023147583008, -1120.3731689453125)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-76.01471710205078, 21.753023147583008, -602.6604614257812)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-136.20201110839844, 21.753023147583008, -870.7710571289062)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(13.999297142028809, 21.74802017211914, -117.76170349121094)






end)


local Tab3 = Window:NewTab("Animation")
local Tab3Section = Tab3:NewSection("Animation")

Tab3Section:NewButton("Astronaut", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=891621366"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=891633237"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=891667138"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=891636393"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=891627522"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=891609353"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=891617961"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Bubbly", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=910004836"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=910009958"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=910034870"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=910025107"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=910016857"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=910001910"
Animate.swimidle.SwimIdle.AnimationId = "http://www.roblox.com/asset/?id=910030921"
Animate.swim.Swim.AnimationId = "http://www.roblox.com/asset/?id=910028158"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Cartoony", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
 Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=742637544"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=742638445"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=742640026"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=742638842"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=742637942"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=742636889"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=742637151"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Elder", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=845400520"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=845403856"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=845386501"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=845398858"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=845392038"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=845396048"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end) 


Tab3Section:NewButton("Knight", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616006778"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616008087"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616013216"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616010382"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616008936"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616003713"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616005863"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Levitation", "Animation", function()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=750781874"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=750782770"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=750785693"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=750783738"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=750782230"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=750779899"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=750780242"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Mage", "Animation", function()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=707742142"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=707855907"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=707897309"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=707861613"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=707853694"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=707826056"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=707829716"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Ninja", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=656117400"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=656118341"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=656121766"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=656118852"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=656117878"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=656114359"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=656115606"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Pirate", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=750781874"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=750782770"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=750785693"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=750783738"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=750782230"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=750779899"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=750780242"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Robot", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616088211"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616089559"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616095330"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616091570"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616090535"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616086039"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616087089"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Stylish", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616136790"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616138447"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616146177"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616140816"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616139451"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616133594"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616134815"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("SuperHero", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616111295"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616113536"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616122287"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616117076"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616115533"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616104706"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616108001"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Toy", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=782841498"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=782845736"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=782843345"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=782842708"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=782847020"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=782843869"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=782846423"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Vampire", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=1083445855"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=1083450166"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=1083473930"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=1083462077"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=1083455352"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=1083439238"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=1083443587"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Werewolf", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=1083195517"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=1083214717"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=1083178339"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=1083216690"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=1083218792"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=1083182000"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=1083189019"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Zombie", "Animation", function()
	while true do
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616158929"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616160636"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616168032"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616163682"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616161997"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616156119"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616157476"
game.Players.LocalPlayer.Character.Humanoid.Jump = false
wait(1)
end
end)

Tab3Section:NewButton("Levitation", "Animation", function()
loadstring(game:HttpGet('https://pastebin.com/raw/AryTwN4z'))()
end)

local Tab3Section = Tab3:NewSection("Other")

Tab3Section:NewButton("Anthro", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=2510196951"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=2510197257"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=2510202577"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=2510198475"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=2510197830"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=2510192778"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=2510195892"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

local Tab3Section = Tab3:NewSection("Special")

Tab3Section:NewButton("Patrol", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=1149612882"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=1150842221"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=1151231493"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=1150967949"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=1148811837"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=1148811837"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=1148863382"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Confident", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=1069977950"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=1069987858"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=1070017263"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=1070001516"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=1069984524"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=1069946257"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=1069973677"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Ghost", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616006778"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616008087"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616013216"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616013216"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616008936"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616005863"
Animate.swimidle.SwimIdle.AnimationId = "http://www.roblox.com/asset/?id=616012453"
Animate.swim.Swim.AnimationId = "http://www.roblox.com/asset/?id=616011509"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Sneaky", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616006778"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616008087"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616013216"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616013216"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616008936"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616005863"
Animate.swimidle.SwimIdle.AnimationId = "http://www.roblox.com/asset/?id=616012453"
Animate.swim.Swim.AnimationId = "http://www.roblox.com/asset/?id=616011509"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("Princess", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=941003647"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=941013098"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=941028902"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=941015281"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=941008832"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=940996062"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=941000007"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

Tab3Section:NewButton("None", "Animation", function()
	wait()
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=0"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=0"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
Animate.swimidle.SwimIdle.AnimationId = "http://www.roblox.com/asset/?id=0"
Animate.swim.Swim.AnimationId = "http://www.roblox.com/asset/?id=0"
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
end)

local Tab4 = Window:NewTab("Gun")
local Tab4Section = Tab4:NewSection("Remove Your Gun Sound")

Tab4Section:NewButton("SMG", " ", function()
wait()
		repeat wait() until plr.Character:FindFirstChild('[SMG]')
		local SMG = plr.Character:FindFirstChild('[SMG]')
		SMG.Handle.ShootSound.Volume = 0
		SMG.Handle.ShootSound.Volume = 0
end)

Tab4Section:NewButton("AR", "Silent Gun", function()
wait()
		repeat wait() until plr.Character:FindFirstChild('[AR]')
		local SMG = plr.Character:FindFirstChild('[AR]')
		SMG.Handle.ShootSound.Volume = 0
		SMG.Handle.ShootSound.Volume = 0
end)

Tab4Section:NewButton("Shotgun", "Silent Gun", function()
wait()
		repeat wait() until plr.Character:FindFirstChild('[Shotgun]')
		local SMG = plr.Character:FindFirstChild('[Shotgun]')
		SMG.Handle.ShootSound.Volume = 0
		SMG.Handle.ShootSound.Volume = 0
end)

Tab4Section:NewButton("Silencer", "Silent Gun", function()
wait()
		repeat wait() until plr.Character:FindFirstChild('[Silencer]')
		local SMG = plr.Character:FindFirstChild('[Silencer]')
		SMG.Handle.ShootSound.Volume = 0
		SMG.Handle.ShootSound.Volume = 0
end)

Tab4Section:NewButton("P90", "Silent Gun", function()
wait()
		repeat wait() until plr.Character:FindFirstChild('[P90]')
		local SMG = plr.Character:FindFirstChild('[P90]')
		SMG.Handle.ShootSound.Volume = 0
		SMG.Handle.ShootSound.Volume = 0
end)

Tab4Section:NewButton("Glock", "Silent Gun", function()
wait()
		repeat wait() until plr.Character:FindFirstChild('[Glock]')
		local SMG = plr.Character:FindFirstChild('[Glock]')
		SMG.Handle.ShootSound.Volume = 0
		SMG.Handle.ShootSound.Volume = 0
end)

local Tab5 = Window:NewTab("Stands")
local Tab5Section = Tab5:NewSection("Stands")

Tab5Section:NewButton("Bat Man", "Bat Man Stand", function()
assert(getrawmetatable)
grm = getrawmetatable(game)
setreadonly(grm, false)
old = grm.__namecall
grm.__namecall = newcclosure(function(self, ...)
    local args = {...}
    if tostring(args[1]) == "TeleportDetect" then
        return
    elseif tostring(args[1]) == "CHECKER_1" then
        return
    elseif tostring(args[1]) == "CHECKER" then
        return
    elseif tostring(args[1]) == "GUI_CHECK" then
        return
    elseif tostring(args[1]) == "OneMoreTime" then
        return
    elseif tostring(args[1]) == "checkingSPEED" then
        return
    elseif tostring(args[1]) == "BANREMOTE" then
        return
    elseif tostring(args[1]) == "PERMAIDBAN" then
        return
    elseif tostring(args[1]) == "KICKREMOTE" then
        return
    elseif tostring(args[1]) == "BR_KICKPC" then
        return
    elseif tostring(args[1]) == "BR_KICKMOBILE" then
        return
    end
    return old(self, ...)
end)

--// main functions
local OriginalKeyUpValue = 0
local LocalPlayer = game:GetService("Players").LocalPlayer

local OldChar = LocalPlayer.Character

function StopAudio()
    OldChar.LowerTorso.BOOMBOXSOUND:Stop()
end

function stop(ID, Key)
    local cor = coroutine.wrap(function()
        wait(OldChar.LowerTorso.BOOMBOXSOUND.TimeLength-0.1)
        if OldChar.LowerTorso.BOOMBOXSOUND.SoundId == "rbxassetid://"..ID and OriginalKeyUpValue == Key then
            StopAudio()
        end
    end)
    cor()
end

function play(ID, STOP, LMAO)
    if LocalPlayer.Backpack:FindFirstChild("[Boombox]") then
        local Tool = nil
        if OldChar:FindFirstChildOfClass("Tool") and LMAO == true then
            Tool = OldChar:FindFirstChildOfClass("Tool")
            OldChar:FindFirstChildOfClass("Tool").Parent = LocalPlayer.Backpack
        end
        LocalPlayer.Backpack["[Boombox]"].Parent =
            OldChar
        game.ReplicatedStorage.MainEvent:FireServer("Boombox", ID)
        OldChar["[Boombox]"].RequiresHandle = false
        if OldChar["[Boombox]"]:FindFirstChild("Handle") then
            OldChar["[Boombox]"].Handle:Destroy()
        end
        OldChar["[Boombox]"].Parent =
            LocalPlayer.Backpack
        LocalPlayer.PlayerGui.MainScreenGui.BoomboxFrame.Visible = false
        if Tool ~= true then
            if Tool then
                Tool.Parent = OldChar
            end
        end
        if STOP == true then
            OldChar.LowerTorso:WaitForChild("BOOMBOXSOUND")
            local cor = coroutine.wrap(function()
                repeat wait() until OldChar.LowerTorso.BOOMBOXSOUND.SoundId == "rbxassetid://"..ID and OldChar.LowerTorso.BOOMBOXSOUND.TimeLength > 0.01
                OriginalKeyUpValue = OriginalKeyUpValue+1
                stop(ID, OriginalKeyUpValue)
            end)
            cor()
        end
    end
end

-- // main tools create
local Batarang = Instance.new('Tool')
Batarang.Parent = game.Players.LocalPlayer.Backpack
Batarang.Name = "Batarang"
Batarang.RequiresHandle = false

--// Batman Outfit We use a model due to the part and stuff
local MaskOn = Instance.new("Animation", game.ReplicatedStorage.ClientAnimations)
MaskOn.AnimationId = "rbxassetid://3380627692"
local MaskOff = Instance.new("Animation", game.ReplicatedStorage.ClientAnimations)
MaskOff.AnimationId = "rbxassetid://3380629232"
local old2 = game.Players.LocalPlayer.Character:FindFirstChildOfClass('Shirt').ShirtTemplate
local old3 = game.Players.LocalPlayer.Character:FindFirstChildOfClass('Pants').PantsTemplate  
game:GetObjects("rbxassetid://8083348193")[1].Parent = game.Players.LocalPlayer.Backpack 
local BatManOutFitTool = game.Players.LocalPlayer.Backpack.BatmanOutfit
local OutFitOn = false
BatManOutFitTool.Activated:Connect(function()
    if OutFitOn == false then
        OutFitOn = true
        local lp = game:GetService("Players").LocalPlayer
        game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(MaskOn):Play()
        game.Players.LocalPlayer.Character.BatmanOutfit.Handle.Transparency = 1
        game.Players.LocalPlayer.Character.BatmanOutfit.Handle.Decal.Transparency = 1
        if game.Players.LocalPlayer.Character:FindFirstChildOfClass('ShirtGraphic') then
            game.Players.LocalPlayer.Character:FindFirstChildOfClass('ShirtGraphic'):Destroy()
        end
        if game.Players.LocalPlayer.Character:FindFirstChildOfClass('Shirt') then
            game.Players.LocalPlayer.Character:FindFirstChildOfClass('Shirt').ShirtTemplate = 'rbxassetid://164114181';
        else
            local Shirt = Instance.new('Shirt');
            Shirt.Parent = game.Players.LocalPlayer.Character;
            Shirt.ShirtTemplate = 'rbxassetid://164114181';
        end
        if game.Players.LocalPlayer.Character:FindFirstChild('Pants') then
            game.Players.LocalPlayer.Character:FindFirstChildOfClass('Pants').PantsTemplate = 'rbxassetid://164114198';
        else
            local Pants = Instance.new('Pants');
            Pants.Parent = game.Players.LocalPlayer.Character;
            Pants.PantsTemplate = 'rbxassetid://164114198';
        end;
    else
        OutFitOn = false
        game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(MaskOff):Play()
        game.Players.LocalPlayer.Character.BatmanOutfit.Handle.Transparency = 0
        game.Players.LocalPlayer.Character.BatmanOutfit.Handle.Decal.Transparency = 0
        game.Players.LocalPlayer.Character:FindFirstChildOfClass('Shirt').ShirtTemplate = old2
        game.Players.LocalPlayer.Character:FindFirstChildOfClass('Pants').PantsTemplate = old3
    end
end)

game:GetObjects("rbxassetid://8083438374")[1].Parent = game.Players.LocalPlayer.Backpack 
local GlideTool = game.Players.LocalPlayer.Backpack.Glide
local GlideAnim = Instance.new("Animation", game.ReplicatedStorage.ClientAnimations)
GlideAnim.AnimationId = "rbxassetid://3136090876"
local Gliding = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(GlideAnim)
function GlideToolActive()
    local player = game.Players.LocalPlayer
    repeat wait() until player.Character
    local humanoid = player.Character:WaitForChild('Humanoid')
    local bodyvelocity = game.Players.LocalPlayer.Backpack.Glide.Handle:WaitForChild("BodyVelocity")
    local jumpover = true
    function jump()
        jumpover = false
        wait(.3)
        jumpover = true
        local currenstate = humanoid:GetState()
        if currenstate == Enum.HumanoidStateType.Freefall and game.Players.LocalPlayer.Character:FindFirstChild("Glide") then
            bodyvelocity.MaxForce = Vector3.new(0,100000,0)
            play(1462718291, true, true)
            while wait() and game.Players.LocalPlayer.Character:FindFirstChild("Glide") and Enum.HumanoidStateType.Freefall do
                Gliding:Play()
            end
        end
    end
    humanoid.StateChanged:Connect(function(oldState, newState)
        if jumpover == true then
            if newState == Enum.HumanoidStateType.Jumping then
                bodyvelocity.MaxForce = Vector3.new(0,0,0)
                jump()
            elseif newState == Enum.HumanoidStateType.Freefall then
                bodyvelocity.MaxForce = Vector3.new(0,300000,0)
                play(1462718291, true, true)
                while wait() and game.Players.LocalPlayer.Character:FindFirstChild("Glide") and Enum.HumanoidStateType.Freefall do
                    Gliding:Play()
                end
            else
                Gliding:Stop()
                if game.Players.LocalPlayer.Character:FindFirstChild("Glide") then
                Gliding:Stop()
                play(2952274135, true, true)
            end 
                Gliding:Stop()
                if game.Players.LocalPlayer.Character:FindFirstChild("Glide") then
                    Gliding:Stop()
                    play(2952274135, true, true)
                end
                bodyvelocity.MaxForce = Vector3.new(0,0,0)
            end
        end
    end)
end

GlideTool.Equipped:Connect(GlideToolActive())

local GrappleHook = Instance.new('Tool')
GrappleHook.Parent = game.Players.LocalPlayer.Backpack
GrappleHook.Name = "GrappleHook"
GrappleHook.RequiresHandle = false
end)

Tab5Section:NewButton("Venom", "Venom Stands", function()
local OriginalKeyUpValue = 0;
local Cooldown = false;

function AddVelocity(Vel, Char)
	Char.HumanoidRootPart.Velocity = Char.HumanoidRootPart.Velocity+Vel
end

local Grapple = Instance.new('Animation');
Grapple.AnimationId = 'rbxassetid://3135389157';

local Swing = Instance.new('Animation');
Swing.AnimationId = 'rbxassetid://3135793091';

local Glide = Instance.new("Animation")
Glide.AnimationId = 'rbxassetid://3136090876';

function StopAudio()
	game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND'):Stop();
end;

function Stop(i, v)
	local w = coroutine.wrap(function()
		wait(game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').TimeLength-0.1)
		if game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').SoundId == 'rbxassetid://'..i and OriginalKeyUpValue == v then
			StopAudio();
		end;
	end);
	w();
end;

function Play(i, v, w)
	if game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack'):FindFirstChild('[Boombox]') then
		local Tool = nil;
		if game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool') and w == true then
			Tool = game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool')
			game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool').Parent = game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack');
		end;
		game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack'):FindFirstChild('[Boombox]').Parent = game:GetService('Players').LocalPlayer.Character;
		game:GetService('ReplicatedStorage'):FindFirstChild('MainEvent'):FireServer('Boombox', i);
		game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]').RequiresHandle = false;
		if game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]'):FindFirstChild('Handle') then
			game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]'):FindFirstChild('Handle'):Destroy();
		end
		game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]').Parent = game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack')
		if game:GetService('Players').LocalPlayer:FindFirstChildOfClass('PlayerGui'):FindFirstChild('MainScreenGui'):FindFirstChild('BoomboxFrame') then
			game:GetService('Players').LocalPlayer:FindFirstChildOfClass('PlayerGui'):FindFirstChild('MainScreenGui'):FindFirstChild('BoomboxFrame').Visible = false;
		end;
		if Tool ~= true then
			if Tool then
				Tool.Parent = game:GetService('Players').LocalPlayer.Character
			end;
		end;
		if v == true then
			game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):WaitForChild('BOOMBOXSOUND');
			local x = coroutine.wrap(function()
				repeat wait() until game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').SoundId == 'rbxassetid://'..i and game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').TimeLength > 0.01
				OriginalKeyUpValue = OriginalKeyUpValue + 1;
				Stop(i, OriginalKeyUpValue);
			end);
			x();
		end;
	end;
end;

function Tool()
	local Tool = Instance.new('Tool')
	Tool.Name = 'Swing';
	Tool.RequiresHandle = false;
	Tool.Activated:Connect(function()
		if game:GetService('Players').LocalPlayer:GetMouse().Target and Cooldown == false then
			Cooldown = true;
			game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Grapple):Play();
			Play(151733071, true, true)
			wait(0.25)
			local Rotation = game:GetService('Players').LocalPlayer.Character:FindFirstChild('HumanoidRootPart').CFrame - game:GetService('Players').LocalPlayer.Character:FindFirstChild('HumanoidRootPart').Position;
			local Tween = game:GetService('TweenService'):Create(game:GetService('Players').LocalPlayer.Character:FindFirstChild('HumanoidRootPart'), TweenInfo.new(.99, Enum.EasingStyle.Linear), {CFrame = CFrame.new(game:GetService('Players').LocalPlayer:GetMouse().Hit.X, game:GetService('Players').LocalPlayer:GetMouse().Hit.Y + 5, game:GetService('Players').LocalPlayer:GetMouse().Hit.Z) * Rotation})
			Tween:Play();
			game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Swing):Play();
			Tween.Completed:Wait();
			for _, v in pairs(game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):GetPlayingAnimationTracks()) do
				if v.Animation.AnimationId == Swing.AnimationId then
					v:Stop();
					wait(0.01)
					game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Glide):Play();
				    wait(.1)
				end;
			end;
			Cooldown = false;
			if not game:GetService('Players').LocalPlayer.Character:FindFirstChild(Tool) then
				Tool.Parent = game:GetService('Players').LocalPlayer.Character;
			end;
		end;
	end);
	Tool.Parent = game:GetService('Players').LocalPlayer:FindFirstChildWhichIsA('Backpack');
end;
game:GetService('Players').LocalPlayer.Character:WaitForChild('FULLY_LOADED_CHAR');
Tool();
game:GetService('Players').LocalPlayer.CharacterAdded:Connect(function(v)
	v:WaitForChild('FULLY_LOADED_CHAR');
	Tool();
end);

function Tool5()
    local Tool5 = Instance.new('Tool')
    Tool5.Name = 'Symbiote';
    Tool5.RequiresHandle = false;
    Tool5.Parent = game:GetService('Players').LocalPlayer:FindFirstChildWhichIsA('Backpack');
end;
game:GetService('Players').LocalPlayer.Character:WaitForChild('FULLY_LOADED_CHAR');
Tool5();
game:GetService('Players').LocalPlayer.CharacterAdded:Connect(function(v)
    v:WaitForChild('FULLY_LOADED_CHAR');
    Tool5();
end);
end)

Tab5Section:NewButton("Deadshot", "Deadshot", function()
pcall(function()
    local deadshot = false
    local MaskOn = Instance.new("Animation", game.ReplicatedStorage.ClientAnimations)
    MaskOn.AnimationId = "rbxassetid://3380627692"
    local MaskOff = Instance.new("Animation", game.ReplicatedStorage.ClientAnimations)
    MaskOff.AnimationId = "rbxassetid://3380629232"
    
    assert(getrawmetatable)
    grm = getrawmetatable(game)
    setreadonly(grm, false)
    old = grm.__namecall
    grm.__namecall = newcclosure(function(self, ...)
        local args = {...}
        if tostring(args[1]) == "TeleportDetect" then
            return
        elseif tostring(args[1]) == "CHECKER_1" then
            return
        elseif tostring(args[1]) == "CHECKER" then
            return
        elseif tostring(args[1]) == "GUI_CHECK" then
            return
        elseif tostring(args[1]) == "OneMoreTime" then
            return
        elseif tostring(args[1]) == "checkingSPEED" then
            return
        elseif tostring(args[1]) == "BANREMOTE" then
            return
        elseif tostring(args[1]) == "PERMAIDBAN" then
            return
        elseif tostring(args[1]) == "KICKREMOTE" then
            return
        elseif tostring(args[1]) == "BR_KICKPC" then
            return
        elseif tostring(args[1]) == "BR_KICKMOBILE" then
            return
        end
        return old(self, ...)
    end)
    
    local OriginalKeyUpValue = 0;
    
    function StopAudio()
        game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND'):Stop();
    end;
    
    function Stop(i, v)
        local w = coroutine.wrap(function()
            wait(game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').TimeLength-0.1)
            if game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').SoundId == 'rbxassetid://'..i and OriginalKeyUpValue == v then
                StopAudio();
            end;
        end);
        w();
    end;
    
    function Play(i, v, w)
        if game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack'):FindFirstChild('[Boombox]') then
            local Tool = nil;
            if game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool') and w == true then
                Tool = game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool')
                game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool').Parent = game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack');
            end;
            game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack'):FindFirstChild('[Boombox]').Parent = game:GetService('Players').LocalPlayer.Character;
            game:GetService('ReplicatedStorage'):FindFirstChild('MainEvent'):FireServer('Boombox', i);
            game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]').RequiresHandle = false;
            if game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]'):FindFirstChild('Handle') then
                game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]'):FindFirstChild('Handle'):Destroy();
            end
            game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]').Parent = game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack')
            if game:GetService('Players').LocalPlayer:FindFirstChildOfClass('PlayerGui'):FindFirstChild('MainScreenGui'):FindFirstChild('BoomboxFrame') then
                game:GetService('Players').LocalPlayer:FindFirstChildOfClass('PlayerGui'):FindFirstChild('MainScreenGui'):FindFirstChild('BoomboxFrame').Visible = false;
            end;
            if Tool ~= true then
                if Tool then
                    Tool.Parent = game:GetService('Players').LocalPlayer.Character
                end;
            end;
            if v == true then
                game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):WaitForChild('BOOMBOXSOUND');
                local x = coroutine.wrap(function()
                    repeat wait() until game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').SoundId == 'rbxassetid://'..i and game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').TimeLength > 0.01
                    OriginalKeyUpValue = OriginalKeyUpValue + 1;
                    Stop(i, OriginalKeyUpValue);
                end);
                x();
            end;
        end;
    end;
    
    function Play2(v)
        Play(v, true, true);
    end;
    
    local guiinvis = false
    game:GetService('Players').LocalPlayer.Chatted:Connect(function(v)
        if v == "_DEADSHOT" then
            if deadshot == false then
                deadshot = true
                Play2(7229541025)
                if guiinvis == true then
                    game.Workspace.stpart.left.SurfaceGui.Enabled = true
                    game.Workspace.stpart.right.SurfaceGui.Enabled = true
                    game:GetService("CoreGui").Deadshot.QuadHaze.Visible = true
                end
                game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(MaskOn):Play()
                game:GetObjects("rbxassetid://8075232446")[1].Parent = workspace --// i uploaded the model, so if you use an exploit you can get the model in-game with this line.
                game.Workspace.stpart.Deadshot.Parent = game.CoreGui --// putting the ui (red vignette) in the CoreGui
                local a = true
                local b = true
                game.Workspace.stpart.left.Position = Vector3.new(-6.144, 0.15, -11.227)
                game.Workspace.stpart.right.Position = Vector3.new(-6.124, 0.15, -11.227)
                game["Run Service"].RenderStepped:Connect(function() -- this is a loop for the ui.
                    game.Workspace.stpart:SetPrimaryPartCFrame(game.Workspace.Camera.CFrame) -- putting ui on camera
                end)
                while wait(0.05) do -- shakey loop!
                    if a == true then
                        game.Workspace.stpart.left.Position -= Vector3.new(0.001,0,0)
                        a = false
                    elseif a == false then
                        game.Workspace.stpart.left.Position += Vector3.new(0.001,0,0)
                        a = true
                    end
                    
                    if b == true then
                        game.Workspace.stpart.right.Position -= Vector3.new(0.001,0,0)
                        b = false
                    elseif b == false then
                        game.Workspace.stpart.right.Position += Vector3.new(0.001,0,0)
                        b = true
                    end
                end
            elseif deadshot == true then
                deadshot = false
                Play2(7229541025)
                game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(MaskOff):Play()
                game.Workspace.stpart.left.SurfaceGui.Enabled = false
                game.Workspace.stpart.right.SurfaceGui.Enabled = false
                game:GetService("CoreGui").Deadshot.QuadHaze.Visible = false
                guiinvis = true
            end
        end;
    end);
    end)
end)

Tab5Section:NewButton("Hearing", "Hearing Stand", function()
grm = getrawmetatable(game)
setreadonly(grm, false)
old = grm.__namecall
grm.__namecall = newcclosure(function(self, ...)
	local args = {...}
	if tostring(args[1]) == "TeleportDetect" then
		return
	elseif tostring(args[1]) == "CHECKER_1" then
		return
	elseif tostring(args[1]) == "CHECKER" then
		return
	elseif tostring(args[1]) == "GUI_CHECK" then
		return
	elseif tostring(args[1]) == "OneMoreTime" then
		return
	elseif tostring(args[1]) == "checkingSPEED" then
		return
	elseif tostring(args[1]) == "BANREMOTE" then
		return
	elseif tostring(args[1]) == "PERMAIDBAN" then
		return
	elseif tostring(args[1]) == "KICKREMOTE" then
		return
	elseif tostring(args[1]) == "BR_KICKPC" then
		return
	elseif tostring(args[1]) == "BR_KICKMOBILE" then
		return
	end
	return old(self, ...)
end)
function Hearing()
	function sandbox(var,func)
		local env = getfenv(func)
		local newenv = setmetatable({},{
			__index = function(self,k)
				if k=="script" then
					return var
				else
					return env[k]
				end
			end,
		})
		setfenv(func,newenv)
		return func
	end
	cors = {}
	mas = Instance.new("Model",game:GetService("Lighting"))
	Tool0 = Instance.new("Tool")
	LocalScript1 = Instance.new("LocalScript")
	BillboardGui2 = Instance.new("BillboardGui")
	ImageLabel3 = Instance.new("ImageLabel")
	ScreenGui4 = Instance.new("ScreenGui")
	TextLabel5 = Instance.new("TextLabel")
	ScreenGui6 = Instance.new("ScreenGui")
	ImageLabel7 = Instance.new("ImageLabel")
	Tool0.Name = "Hearing"
	Tool0.Parent = mas
	Tool0.CanBeDropped = false
	Tool0.RequiresHandle = false
	LocalScript1.Parent = Tool0
	table.insert(cors,sandbox(LocalScript1,function()
		wait();
		local l__LocalPlayer__1 = game.Players.LocalPlayer;
		while true do
			wait();
			if l__LocalPlayer__1.Character then
				break;
			end;
		end;
		local l__Character__2 = l__LocalPlayer__1.Character;
		local u1 = false;
		local l__PlayerGui__2 = game.CoreGui;
		function ChatFunc(p1)
			local v3 = p1.Chatted:connect(function(p2)
				if u1 then
					local v4 = BrickColor.Random();
					local v5 = script.MsgGui:Clone();
					if string.find(string.lower(p2), "super") then
						v5.Msg.TextSize = 29;
					end;
					v5.Msg.Text = p1.Name .. ": " .. p2;
					v5.Msg.TextColor3 = v4.Color;
					v5.Msg.Position = UDim2.new(0.5, math.random(-350, 350), 0.5, math.random(-210, 250));
					v5.Parent = l__PlayerGui__2;
					local v6 = script.DotGui:Clone();
					v6.Dot.ImageColor3 = v4.Color;
					v6.Enabled = true;
					if p1.Character then
						if p1.Character:findFirstChild("Head") then
							v6.Parent = p1.Character.Head;
						end;
					end;
					spawn(function()
						local v7 = 1 - 1;
						while true do
							v6.Size = v6.Size - UDim2.new(0, 1, 0, 1);
							game:GetService("RunService").RenderStepped:wait();
							if 0 <= 1 then
								if v7 < 70 then

								else
									break;
								end;
							elseif 70 < v7 then

							else
								break;
							end;
							v7 = v7 + 1;				
						end;
					end);
					game.Debris:AddItem(v5, 3);
					game.Debris:AddItem(v6, 6);
				end;
			end);
		end;
		for v8, v9 in pairs(game.Players:GetChildren()) do
			ChatFunc(v9);
		end;
		game.Players.PlayerAdded:connect(function(p3)
			ChatFunc(p3);
		end);
		local u3 = false;
		local u4 = nil;
		script.Parent.Equipped:connect(function(p4)
			p4.Button1Down:connect(function()
				if u3 then
					return;
				end;
				u3 = true;
				if not u1 then
					u4 = script.Frame:Clone();
					u4.Parent = l__PlayerGui__2;
					u1 = true;
				else
					u4:Destroy();
					u1 = false;
				end;
				wait(1);
				u3 = false;
			end);
		end);
	end))
	BillboardGui2.Name = "DotGui"
	BillboardGui2.Parent = LocalScript1
	BillboardGui2.Enabled = false
	BillboardGui2.Size = UDim2.new(0, 90, 0, 90)
	BillboardGui2.Active = true
	BillboardGui2.ClipsDescendants = true
	BillboardGui2.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	BillboardGui2.AlwaysOnTop = true
	ImageLabel3.Name = "Dot"
	ImageLabel3.Parent = BillboardGui2
	ImageLabel3.Size = UDim2.new(1, 0, 1, 0)
	ImageLabel3.BackgroundColor = BrickColor.new("Institutional white")
	ImageLabel3.BackgroundColor3 = Color3.new(1, 1, 1)
	ImageLabel3.BackgroundTransparency = 1
	ImageLabel3.Image = "rbxassetid://130424513"
	ImageLabel3.ImageColor3 = Color3.new(1, 0, 0)
	ScreenGui4.Name = "MsgGui"
	ScreenGui4.Parent = LocalScript1
	ScreenGui4.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	TextLabel5.Name = "Msg"
	TextLabel5.Parent = ScreenGui4
	TextLabel5.Position = UDim2.new(0, 300, 0, 25)
	TextLabel5.Size = UDim2.new(0, 1, 0, 1)
	TextLabel5.BackgroundColor = BrickColor.new("Institutional white")
	TextLabel5.BackgroundColor3 = Color3.new(1, 1, 1)
	TextLabel5.BackgroundTransparency = 1
	TextLabel5.Font = Enum.Font.SourceSansBold
	TextLabel5.FontSize = Enum.FontSize.Size28
	TextLabel5.Text = ""
	TextLabel5.TextColor = BrickColor.new("Really black")
	TextLabel5.TextColor3 = Color3.new(0, 0, 0)
	TextLabel5.TextSize = 25
	TextLabel5.TextStrokeTransparency = 0.60000002384186
	ScreenGui6.Name = "Frame"
	ScreenGui6.Parent = LocalScript1
	ScreenGui6.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	ImageLabel7.Name = "Image"
	ImageLabel7.Parent = ScreenGui6
	ImageLabel7.Size = UDim2.new(1, 0, 1, 0)
	ImageLabel7.BackgroundColor = BrickColor.new("Institutional white")
	ImageLabel7.BackgroundColor3 = Color3.new(1, 1, 1)
	ImageLabel7.BackgroundTransparency = 1
	ImageLabel7.Image = "rbxassetid://36869195"
	ImageLabel7.ImageColor3 = Color3.new(0.290196, 1, 0.917647)
	ImageLabel7.ImageTransparency = 0.80000001192093
	for i,v in pairs(mas:GetChildren()) do
		v.Parent = game.Players.LocalPlayer.Backpack
		pcall(function() v:MakeJoints() end)
	end
	mas:Destroy()
	for i,v in pairs(cors) do
		spawn(function()
			pcall(v)
		end)
	end
end
game.Players.LocalPlayer.Character:WaitForChild("FULLY_LOADED_CHAR")
wait(1)
Hearing()
game.Players.LocalPlayer.CharacterAdded:connect(function()
	game.Players.LocalPlayer.Character:WaitForChild("FULLY_LOADED_CHAR")
	wait(1)
	Hearing()
end)
end)

Tab5Section:NewButton("Wolverine", "Wolverine Stand", function()
local OriginalKeyUpValue = 0
local LocalPlayer = game:GetService("Players").LocalPlayer

local OldChar = LocalPlayer.Character

function StopAudio()
    OldChar.LowerTorso.BOOMBOXSOUND:Stop()
end

function stop(ID, Key)
    local cor = coroutine.wrap(function()
        wait(OldChar.LowerTorso.BOOMBOXSOUND.TimeLength-0.1)
        if OldChar.LowerTorso.BOOMBOXSOUND.SoundId == "rbxassetid://"..ID and OriginalKeyUpValue == Key then
            StopAudio()
        end
    end)
    cor()
end


function play(ID, STOP, LMAO)
    if LocalPlayer.Backpack:FindFirstChild("[Boombox]") then
        local Tool = nil
        if OldChar:FindFirstChildOfClass("Tool") and LMAO == true then
            Tool = OldChar:FindFirstChildOfClass("Tool")
            OldChar:FindFirstChildOfClass("Tool").Parent = LocalPlayer.Backpack
        end
        LocalPlayer.Backpack["[Boombox]"].Parent =
            OldChar
        game.ReplicatedStorage.MainEvent:FireServer("Boombox", ID)
        OldChar["[Boombox]"].RequiresHandle = false
        if OldChar["[Boombox]"]:FindFirstChild("Handle") then
            OldChar["[Boombox]"].Handle:Destroy()
        end
        OldChar["[Boombox]"].Parent =
            LocalPlayer.Backpack
        LocalPlayer.PlayerGui.MainScreenGui.BoomboxFrame.Visible = false
        if Tool ~= true then
            if Tool then
                Tool.Parent = OldChar
            end
        end
        if STOP == true then
            OldChar.LowerTorso:WaitForChild("BOOMBOXSOUND")
            local cor = coroutine.wrap(function()
                repeat wait() until OldChar.LowerTorso.BOOMBOXSOUND.SoundId == "rbxassetid://"..ID and OldChar.LowerTorso.BOOMBOXSOUND.TimeLength > 0.01
                OriginalKeyUpValue = OriginalKeyUpValue+1
                stop(ID, OriginalKeyUpValue)
            end)
            cor()
        end
    end
end

local Player = game:GetService("Players").LocalPlayer
local Character = Player.Character
local Root = Character.HumanoidRootPart 
local ply = game.Players.LocalPlayer
local chr = ply.Character

   
 local Tool = Instance.new('Tool')
 Tool.Parent = game.Players.LocalPlayer.Backpack
 Tool.Name = "Wolverine"
 Tool.RequiresHandle = false
 
    
 local WVHandle = Instance.new('Tool')
 WVHandle.Parent = game.Players.LocalPlayer.Backpack
 WVHandle.Name = "-"
 WVHandle.RequiresHandle = false

 function GetKnives()
    local Target = game.Workspace.Ignored.Shop['[Knife] - $150']
    local Tool = Instance.new('Tool')
    Tool.Parent = game.Players.LocalPlayer.Backpack
    Tool.Name = "Collect Knives"
    Tool.RequiresHandle = false
    
    
    Tool.Activated:Connect(function()
    
    for i,v in pairs(game.Workspace.Ignored.ItemsDrop:GetDescendants()) do
    if v.Name == "[Knife]" then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame
        break
    end
    end
    end)
end
GetKnives()

plr = game.Players.LocalPlayer
 
hum = plr.Character.HumanoidRootPart
 
mouse = plr:GetMouse()
local loopenabled = false

-- tool here

Tool.Activated:Connect(function() 

    WVHandle.Parent = game.Players.LocalPlayer.Character
    
    wait(0.1)

Tool.Parent = game:GetService('Players').LocalPlayer.Backpack

    play(2769472393, true, true)
    wait(0.1)
    local Char = game.Players.LocalPlayer.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")
    local Anim = Instance.new("Animation")

wait(1)
local count = 0 
for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
  if v.Name == '[Knife]' then
    count = count + 1
    if count == 1 then
        v.GripForward = Vector3.new(-0.999, 0.038, -0.019)
        v.GripPos = Vector3.new(0.134, -0.006, -0.27)
        v.GripRight = Vector3.new(0.021, 0.06, -0.998)
        v.GripUp = Vector3.new(0.037, 0.997, 0.06)
    elseif count == 2 then
        v.GripForward = Vector3.new(-0.999, 0.038, -0.019)
        v.GripPos = Vector3.new(0.128, -0.037, -0.008)
        v.GripRight = Vector3.new(0.021, 0.06, -0.998)
        v.GripUp = Vector3.new(0.037, 0.997, 0.06)
    else
        v.GripForward = Vector3.new(-0.999, 0.038, -0.019)
        v.GripPos = Vector3.new(0.12, -0.072, 0.23)
        v.GripRight = Vector3.new(0.021, 0.06, -0.998)
        v.GripUp = Vector3.new(0.037, 0.997, 0.06)
    end
    v.Parent = game.Players.LocalPlayer.Character
  end
end

local FastSprint = Instance.new("IntValue",ply.Character.BodyEffects.Movement);FastSprint.Name = "FastSprint"
local HulkJump = Instance.new("IntValue",ply.Character.BodyEffects.Movement);HulkJump.Name = "HighJump"
    
    Anim.AnimationId = "rbxassetid://7861306542"
    function WolvAnim()
        local XD = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):LoadAnimation(Anim)
        XD:Play()
        XD.TimePosition = 0.40
        XD.Looped = false
        XD:AdjustSpeed(1.8)
    end
    if loopenabled == false then
        loopenabled = true
    while true do
    wait()
if game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoWalkSpeed") then game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoWalkSpeed"):Destroy() end
if game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("ReduceWalk") then game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("ReduceWalk"):Destroy() end
if game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoJumping") then game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoJumping"):Destroy() end
if game.Players.LocalPlayer.Character.BodyEffects.Reload.Value == true then game.Players.LocalPlayer.Character.BodyEffects.Reload.Value = false end

if game.Players.LocalPlayer.Backpack:FindFirstChild('-') then
    for i,v in pairs(game.Players.LocalPlayer.Character.BodyEffects.Movement:GetChildren()) do
        if v.Name == "FastSprint" then v:Destroy()
        elseif v.Name == "HighJump" then v:Destroy()
            play(2769472667, true, true)
            end
        end
    end        

        for i,v in next, Hum:GetPlayingAnimationTracks() do
            if v.Animation.AnimationId == "rbxassetid://3033700364" then
                v:Stop();
                wait(.1)
                WolvAnim()
            end
        end
    end
end
end)
end)

local Tab6 = Window:NewTab("Auto Farm")
local Tab6Section = Tab6:NewSection("Auto Farm Script")

Tab6Section:NewToggle("Fist Farm", "Auto Farm", function(state)
    if state then
loadstring(game:HttpGet('https://raw.githubusercontent.com/Exploit-blox/helloDaHood/main/DaHoodKidW'))()
    else
loadstring(game:HttpGet('https://raw.githubusercontent.com/Exploit-blox/Da-Hood/main/ProKidEsterAlt'))()
    end
end)

Tab6Section:NewToggle("Letuce Farm", "Auto Farm", function(state)
    if state then
loadstring(game:HttpGet('https://raw.githubusercontent.com/Exploit-blox/my-fault/main/beest4r'))()
    else
loadstring(game:HttpGet('https://raw.githubusercontent.com/Exploit-blox/legend-of-speeds/main/Lettuce%20False'))()
    end
end)

Tab6Section:NewToggle("Hostpital Farm", "Auto Farm", function(state)
    if state then
loadstring(game:HttpGet('https://pastebin.com/raw/wGU2QCtp'))()
    else
loadstring(game:HttpGet('https://pastebin.com/raw/kiywMAGC'))()
    end
end)

Tab6Section:NewButton("Money Farm", "Auto Farn", function()
loadstring(game:HttpGet("https://pastebin.com/raw/Zx061kiT", true))()
end)

local Tab7 = Window:NewTab("Aimlock")
local Tab7Section = Tab7:NewSection("Aimlock [Q]")

Tab7Section:NewButton("Aimlock","Aimlock",function()
	getgenv().AimPart = "HumanoidRootPart"
	getgenv().AimlockKey = "q"
	getgenv().AimRadius = 30
	getgenv().ThirdPerson = true
	getgenv().FirstPerson = true
	getgenv().TeamCheck = false
	getgenv().PredictMovement = true
	getgenv().PredictionVelocity = 9
	local L_27_, L_28_, L_29_, L_30_ =
            game:GetService "Players",
            game:GetService "UserInputService",
            game:GetService "RunService",
            game:GetService "StarterGui"
	local L_31_, L_32_, L_33_, L_34_, L_35_, L_36_, L_37_ =
            L_27_.LocalPlayer,
            L_27_.LocalPlayer:GetMouse(),
            workspace.CurrentCamera,
            CFrame.new,
            Ray.new,
            Vector3.new,
            Vector2.new
	local L_38_, L_39_, L_40_ = true, false, false
	local L_41_
	getgenv().CiazwareUniversalAimbotLoaded = true
	getgenv().WorldToViewportPoint = function(L_42_arg0)
		return L_33_:WorldToViewportPoint(L_42_arg0)
	end
	getgenv().WorldToScreenPoint = function(L_43_arg0)
		return L_33_.WorldToScreenPoint(L_33_, L_43_arg0)
	end
	getgenv().GetObscuringObjects = function(L_44_arg0)
		if L_44_arg0 and L_44_arg0:FindFirstChild(getgenv().AimPart) and L_31_ and L_31_.Character:FindFirstChild("Head") then
			local L_45_ = workspace:FindPartOnRay(L_35_(L_44_arg0[getgenv().AimPart].Position, L_31_.Character.Head.Position))
			if L_45_ then
				return L_45_:IsDescendantOf(L_44_arg0)
			end
		end
	end
	getgenv().GetNearestTarget = function()
		local L_46_ = {}
		local L_47_ = {}
		local L_48_ = {}
		for L_50_forvar0, L_51_forvar1 in pairs(L_27_:GetPlayers()) do
			if L_51_forvar1 ~= L_31_ then
				table.insert(L_46_, L_51_forvar1)
			end
		end
		for L_52_forvar0, L_53_forvar1 in pairs(L_46_) do
			if L_53_forvar1.Character ~= nil then
				local L_54_ = L_53_forvar1.Character:FindFirstChild("Head")
				if getgenv().TeamCheck == true and L_53_forvar1.Team ~= L_31_.Team then
					local L_55_ =
                            (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
					local L_56_ =
                            Ray.new(
                            game.Workspace.CurrentCamera.CFrame.p,
                            (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_55_
                        )
					local L_57_, L_58_ = game.Workspace:FindPartOnRay(L_56_, game.Workspace)
					local L_59_ = math.floor((L_58_ - L_54_.Position).magnitude)
					L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
					L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_55_
					L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
					L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_59_
					table.insert(L_48_, L_59_)
				elseif getgenv().TeamCheck == false and L_53_forvar1.Team == L_31_.Team then
					local L_60_ =
                            (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
					local L_61_ =
                            Ray.new(
                            game.Workspace.CurrentCamera.CFrame.p,
                            (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_60_
                        )
					local L_62_, L_63_ = game.Workspace:FindPartOnRay(L_61_, game.Workspace)
					local L_64_ = math.floor((L_63_ - L_54_.Position).magnitude)
					L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
					L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_60_
					L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
					L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_64_
					table.insert(L_48_, L_64_)
				end
			end
		end
		if unpack(L_48_) == nil then
			return nil
		end
		local L_49_ = math.floor(math.min(unpack(L_48_)))
		if L_49_ > getgenv().AimRadius then
			return nil
		end
		for L_65_forvar0, L_66_forvar1 in pairs(L_47_) do
			if L_66_forvar1.diff == L_49_ then
				return L_66_forvar1.plr
			end
		end
		return nil
	end
	L_32_.KeyDown:Connect(
            function(L_67_arg0)
		if L_67_arg0 == AimlockKey and L_41_ == nil then
			pcall(
                        function()
				if L_39_ ~= true then
					L_39_ = true
				end
				local L_68_
				L_68_ = GetNearestTarget()
				if L_68_ ~= nil then
					L_41_ = L_68_
				end
			end
                    )
		elseif L_67_arg0 == AimlockKey and L_41_ ~= nil then
			if L_41_ ~= nil then
				L_41_ = nil
			end
			if L_39_ ~= false then
				L_39_ = false
			end
		end
	end)
	L_29_.RenderStepped:Connect(
            function()
		if getgenv().ThirdPerson == true and getgenv().FirstPerson == true then
			if
                        (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 or
                            (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1
                     then
				L_40_ = true
			else
				L_40_ = false
			end
		elseif getgenv().ThirdPerson == true and getgenv().FirstPerson == false then
			if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 then
				L_40_ = true
			else
				L_40_ = false
			end
		elseif getgenv().ThirdPerson == false and getgenv().FirstPerson == true then
			if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1 then
				L_40_ = true
			else
				L_40_ = false
			end
		end
		if L_38_ == true and L_39_ == true then
			if L_41_ and L_41_.Character and L_41_.Character:FindFirstChild(getgenv().AimPart) then
				if getgenv().FirstPerson == true then
					if L_40_ == true then
						if getgenv().PredictMovement == true then
							L_33_.CFrame =
                                        L_34_(
                                        L_33_.CFrame.p,
                                        L_41_.Character[getgenv().AimPart].Position +
                                            L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                    )
						elseif getgenv().PredictMovement == false then
							L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
						end
					end
				elseif getgenv().ThirdPerson == true then
					if L_40_ == true then
						if getgenv().PredictMovement == true then
							L_33_.CFrame =
                                        L_34_(
                                        L_33_.CFrame.p,
                                        L_41_.Character[getgenv().AimPart].Position +
                                            L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                    )
						elseif getgenv().PredictMovement == false then
							L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
						end
					end
				end
			end
		end
	end)
end)

Tab7Section:NewTextBox("Aimlock Key","Aimlock Key should be lowercase.",function(L_69_arg0)
	getgenv().AimlockKey = L_69_arg0
end)

Tab7Section:NewTextBox("Aimlock Prediction","Customize your aimlock prediction",function(L_70_arg0)
	PredictionVelocity = L_70_arg0
end)

Tab7Section:NewDropdown("AimPart","AimPart",{"Head","UpperTorso","HumanoidRootPart","LowerTorso"},function(L_71_arg0)
	getgenv().AimPart = L_71_arg0
end)

local Tab7Section = Tab7:NewSection("Silent Aim [T]")

Tab7Section:NewButton("Silent Aim","Silent Aim Toggle Key is T.",function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/tayodevelup/imsoniac/main/silentaim", true))()
end)

Tab7Section:NewTextBox("Silent Aim Prediction","0.157 for low ping 0.178 high ping",function(L_72_arg0)
	DaHoodSettings.Prediction = L_72_arg0
end)

Tab7Section:NewDropdown("Silent Aim Part","Choose Part",{"Head","UpperTorso","HumanoidRootPart","LowerTorso"},function(L_73_arg0)
	Aiming.TargetPart = L_73_arg0
end)

Tab7Section:NewTextBox("Silent Aim Size Fov","Silent Aim Size",function(L_74_arg0)
	Aiming.FOV = L_74_arg0
end)

Tab7Section:NewToggle("Silent Aim Show Fov","Show The Silent Aim Fov",function(L_75_arg0)
	Aiming.ShowFOV = L_75_arg0
end)

local Tab7Section = Tab7:NewSection("Anti Lock [Z]")

Tab7Section:NewButton("Anti-Lock","Key is Z.",function()
	repeat
		wait()
	until game:IsLoaded()
	getgenv().Fix = true
	getgenv().TeclasWS = {
		["tecla1"] = "nil",
		["tecla2"] = "nil",
		["tecla3"] = "H"
	}
	local L_121_ = game:GetService("Players")
	local L_122_ = game:GetService("StarterGui") or "son una mierda"
	local L_123_ = L_121_.LocalPlayer
	local L_124_ = L_123_:GetMouse()
	local L_125_ = getrenv()._G
	local L_126_ = getrawmetatable(game)
	local L_127_ = L_126_.__newindex
	local L_128_ = L_126_.__index
	local L_129_ = 22
	local L_130_ = true
	function anunciar_atentado_terrorista(L_138_arg0)
		L_122_:SetCore("SendNotification", {
			Title = "anti lock fix",
			Text = L_138_arg0
		})
	end
	getgenv().TECHWAREWALKSPEED_LOADED = true
	wait(1.5)
	anunciar_atentado_terrorista("Press  " .. TeclasWS.tecla3 .. " to turn on/off anti lock fix")
	L_124_.KeyDown:Connect(
            function(L_139_arg0)
		if L_139_arg0:lower() == TeclasWS.tecla1:lower() then
			L_129_ = L_129_ + 1
			anunciar_atentado_terrorista("æ­æ¾å¨éåº¦å·²æé« (speed = " .. tostring(L_129_) .. ")")
		elseif L_139_arg0:lower() == TeclasWS.tecla2:lower() then
			L_129_ = L_129_ - 1
			anunciar_atentado_terrorista("ç©å®¶çéåº¦å·²éä½ (speed = " .. tostring(L_129_) .. ")")
		elseif L_139_arg0:lower() == TeclasWS.tecla3:lower() then
			if L_130_ then
				L_130_ = false
				anunciar_atentado_terrorista("anti lock fix off")
			else
				L_130_ = true
				anunciar_atentado_terrorista("anti lock fix on")
			end
		end
	end
        )
	setreadonly(L_126_, false)
	L_126_.__index =
            newcclosure(
            function(L_140_arg0, L_141_arg1)
		local L_142_ = checkcaller()
		if L_141_arg1 == "WalkSpeed" and not L_142_ then
			return L_125_.CurrentWS
		end
		return L_128_(L_140_arg0, L_141_arg1)
	end)
	L_126_.__newindex =
            newcclosure(
            function(L_143_arg0, L_144_arg1, L_145_arg2)
		local L_146_ = checkcaller()
		if L_130_ then
			if L_144_arg1 == "WalkSpeed" and L_145_arg2 ~= 0 and not L_146_ then
				return L_127_(L_143_arg0, L_144_arg1, L_129_)
			end
		end
		return L_127_(L_143_arg0, L_144_arg1, L_145_arg2)
	end)
	setreadonly(L_126_, true)
	repeat
		wait()
	until game:IsLoaded()
	local L_131_ = game:service("Players")
	local L_132_ = L_131_.LocalPlayer
	repeat
		wait()
	until L_132_.Character
	local L_133_ = game:service("UserInputService")
	local L_134_ = game:service("RunService")
	local L_135_ = -0.27
	local L_136_ = false
	local L_137_
	L_133_.InputBegan:connect(
            function(L_147_arg0)
		if L_147_arg0.KeyCode == Enum.KeyCode.LeftBracket then
			L_135_ = L_135_ + 0.01
			print(L_135_)
			wait(0.2)
			while L_133_:IsKeyDown(Enum.KeyCode.LeftBracket) do
				wait()
				L_135_ = L_135_ + 0.01
				print(L_135_)
			end
		end
		if L_147_arg0.KeyCode == Enum.KeyCode.RightBracket then
			L_135_ = L_135_ - 0.01
			print(L_135_)
			wait(0.2)
			while L_133_:IsKeyDown(Enum.KeyCode.RightBracket) do
				wait()
				L_135_ = L_135_ - 0.01
				print(L_135_)
			end
		end
		if L_147_arg0.KeyCode == Enum.KeyCode.Z then
			L_136_ = not L_136_
			if L_136_ == true then
				repeat
					game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame +
                                game.Players.LocalPlayer.Character.Humanoid.MoveDirection * L_135_
					game:GetService("RunService").Stepped:wait()
				until L_136_ == false
			end
		end
	end)
end)

local Tab7Section = Tab7:NewSection("Other Lock")

Tab7Section:NewButton("Aim Lock {Old Arceus X Aimlock Tools}", "Arceus X AimLock", function()
loadstring(game:HttpGet('https://pastebin.com/raw/HA8kAiYp'))()
end)

Tab7Section:NewButton("Aimbot", "", function()
loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/Hyotinhofofinho/s1mple/main/LIXO"))()
end)

Tab7Section:NewButton("Streamable [Q]", "Q", function()
loadstring(game:HttpGet('https://pastebin.com/raw/XfdzBV2y'))()
end)

Tab7Section:NewButton("Aimbot [Q]", "Q", function()
loadstring(game:HttpGet('https://pastebin.com/raw/XzCsiJaD'))()
end)

Tab7Section:NewButton("Kloy Lock [Q]", "Q", function()
loadstring(game:HttpGet('https://pastebin.com/raw/BtQYq4EG'))()
end)

Tab7Section:NewButton("Fire Lock {Tool Lock}", "Tool Lock", function()
local Enabled = true
local Prediction = 0.1202938
local Notifications = true
local AimPart = "UpperTorso"


local Tool = Instance.new("Tool")
Tool.RequiresHandle = false
Tool.Name = "FireLock"
Tool.TextureId = "rbxthumb://type=Asset&id=9904511449&w=150&h=150"

local Camera = game:GetService("Workspace").CurrentCamera
local Mouse = game.Players.LocalPlayer:GetMouse()
local Plr

local Part = Instance.new("Part", game.Workspace)

Part.Anchored = true
Part.CanCollide = false
Part.Color = Color3.fromRGB(999, 999, 999)
Part.Material = Enum.Material.Neon
Part.Size = Vector3.new(1.5, 1.5, 1.5)
Part.Shape = Enum.PartType.Block

function FindClosestPlayer()
    local closestPlayer
    local shortestDistance = math.huge

    for i, v in pairs(game.Players:GetPlayers()) do
        if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("Humanoid") and
            v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then
            local pos = Camera:WorldToViewportPoint(v.Character.PrimaryPart.Position)
            local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(Mouse.X, Mouse.Y)).magnitude
            if magnitude < shortestDistance then
                closestPlayer = v
                shortestDistance = magnitude
            end
        end
    end
    return closestPlayer
end

Tool.Activated:Connect(function()

    if Enabled == true then
        Enabled = false
        if Notifications == true then

            Plr = FindClosestPlayer()
            TargetPlayer = tostring(Plr)
            game.StarterGui:SetCore("SendNotification", {
                Title = "──｜FireHood｜──",
                Text = "Unlocked"
            })
        end

    else
        Plr = FindClosestPlayer()
        TargetPlayer = tostring(Plr)

        Enabled = true

        if Notifications == true then

            Plr = FindClosestPlayer()
            TargetPlayer = tostring(Plr)
            game.StarterGui:SetCore("SendNotification", {
                Title = "──｜FireHood｜──",
                Text = "Locked To :  " .. tostring(TargetPlayer)
            })
        end
    end
end)

game:GetService("RunService").Stepped:Connect(function()
    if Enabled == true then

        Part.Position = game.Players[TargetPlayer].Character.HumanoidRootPart.Position
    else
        Part.CFrame = CFrame.new(0, -9999, 0)

    end
end)

local mt = getrawmetatable(game)
local old = mt.__namecall
setreadonly(mt, false)
mt.__namecall = newcclosure(function(...)
    local args = { ... }

    if Enabled and getnamecallmethod() == "FireServer" and args[2] == "UpdateMousePos" then
        args[3] = game.Players[TargetPlayer].Character[AimPart].Position +

            (game.Players[TargetPlayer].Character[AimPart].Velocity * Prediction)

        return old(unpack(args))
    end
    return old(...)
end)

Tool.Parent = game.Players.LocalPlayer.Backpack
end)

local Tab8 = Window:NewTab("Marco")
local Tab8Section = Tab8:NewSection("Marco")

Tab8Section:NewButton("Speed Glitch [X]", "Speed", function()
--Settings
local sped = 110 -- Speed
local keybind = "X"




--The Script

yes = false
	plr = game.Players.LocalPlayer
	mouse = plr:GetMouse()
	mouse.KeyDown:connect(function(key)
		if key == keybind and yes == false then
			yes = true
			game.Players.LocalPlayer.Character.Humanoid.Name = "Humz"
			game.Players.LocalPlayer.Character.Humz.WalkSpeed = sped
			game.Players.LocalPlayer.Character.Humz.JumpPower = 50
		elseif key == keybind and yes == true then
			yes = false
			game.Players.LocalPlayer.Character.Humz.WalkSpeed = 16
			game.Players.LocalPlayer.Character.Humz.JumpPower = 50
			game.Players.LocalPlayer.Character.Humz.Name = "Humanoid"
		end
	end)
end)

Tab9Section:NewButton("Fake Marco Animation [X]", "Fake Marco", function()
_G.Key = "x"
local plr = game:GetService("Players").LocalPlayer
local Mouse = plr:GetMouse()
local On_Check = false
local Item = plr.Backpack.Wallet
local UAnimation = Instance.new("Animation")

function stopTracks()
	for _, v in next, game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):GetPlayingAnimationTracks() do
		if (v.Animation.AnimationId:match("rbxassetid")) then
			v:Stop()
		end
	end
end

function loadAnimation(id)
	if UAnimation.AnimationId == id then
		stopTracks()
		UAnimation.AnimationId = "1"
	else
		UAnimation.AnimationId = id
		local animationTrack = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):LoadAnimation(UAnimation)
		animationTrack:Play()
	end
end

Mouse.KeyDown:Connect(function(Key)
	if Key == _G.Key then
		On_Check = not On_Check
		if On_Check == true then
			stopTracks()
			loadAnimation("rbxassetid://3189777795")
			wait(1.5)
			Item.Parent = plr.Character
			wait(0.15)
			plr.Character.Wallet.Parent = plr.Backpack
			wait(0.05)
			repeat game:GetService("RunService").Heartbeat:wait()
				keypress(0x49)
				game:GetService("RunService").Heartbeat:wait()
				keypress(0x4F)
				game:GetService("RunService").Heartbeat:wait()
				keyrelease(0x49)
				game:GetService("RunService").Heartbeat:wait()
				keyrelease(0x4F)
				game:GetService("RunService").Heartbeat:wait()
				keypress(0x49)
				game:GetService("RunService").Heartbeat:wait()
				keypress(0x4F)
				game:GetService("RunService").Heartbeat:wait()
				keyrelease(0x49)
				game:GetService("RunService").Heartbeat:wait()
				keyrelease(0x4F)
				game:GetService("RunService").Heartbeat:wait()
			until On_Check == false
		end
	end
end)
end)

local Tab9 = Window:NewTab("Credits")
local Tab9Section = Tab9:NewSection("Credits")
Tab9Section:NewLabel("Ui: Kavo Libary")
Tab9Section:NewLabel("Fly Gui V2")
Tab9Section:NewLabel("Owner: ALT1LR")
Tab9Section:NewLabel("Discord: alt1lr#9459")
