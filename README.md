-- LIXO MENU - UI DEMONSTRATIVO
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer

-- GUI
local gui = Instance.new("ScreenGui", player.PlayerGui)
gui.Name = "LixoMenu"

-- Botão lixo (abrir/fechar)
local lixoBtn = Instance.new("ImageButton", gui)
lixoBtn.Size = UDim2.new(0,60,0,60)
lixoBtn.Position = UDim2.new(0,20,0.5,-30)
lixoBtn.Image = "rbxassetid://7072728347" -- imagem de lixo
lixoBtn.BackgroundTransparency = 1

-- Menu
local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0,250,0,200)
frame.Position = UDim2.new(0.5,-125,0.5,-100)
frame.BackgroundColor3 = Color3.new(0,0,0)
frame.Visible = true

local corner = Instance.new("UICorner", frame)

-- Título
local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,40)
title.Text = "LIXO MENU"
title.TextColor3 = Color3.new(1,1,1)
title.BackgroundTransparency = 1
title.Font = Enum.Font.GothamBold
title.TextSize = 20

-- Botão Aimbot
local aimbot = Instance.new("TextButton", frame)
aimbot.Position = UDim2.new(0,20,0,60)
aimbot.Size = UDim2.new(1,-40,0,30)
aimbot.Text = "AIMBOT"
aimbot.BackgroundColor3 = Color3.new(1,1,1)
aimbot.TextColor3 = Color3.new(0,0,0)

-- Botão Silent
local silent = Instance.new("TextButton", frame)
silent.Position = UDim2.new(0,20,0,100)
silent.Size = UDim2.new(1,-40,0,30)
silent.Text = "SILENT"
silent.BackgroundColor3 = Color3.new(1,1,1)
silent.TextColor3 = Color3.new(0,0,0)

-- FOV Texto
local fovText = Instance.new("TextLabel", frame)
fovText.Position = UDim2.new(0,20,0,140)
fovText.Size = UDim2.new(1,-40,0,20)
fovText.Text = "FOV: 100"
fovText.TextColor3 = Color3.new(1,1,1)
fovText.BackgroundTransparency = 1

-- Círculo FOV
local fovCircle = Instance.new("Frame", gui)
fovCircle.Size = UDim2.new(0,200,0,200)
fovCircle.AnchorPoint = Vector2.new(0.5,0.5)
fovCircle.Position = UDim2.new(0.5,0,0.5,0)
fovCircle.BackgroundTransparency = 1
fovCircle.Visible = false

local stroke = Instance.new("UIStroke", fovCircle)
stroke.Color = Color3.fromRGB(255,0,0)
stroke.Thickness = 2

local corner2 = Instance.new("UICorner", fovCircle)
corner2.CornerRadius = UDim.new(1,0)

-- Estados
local menuOpen = true
local aimbotOn = false

-- Abrir / fechar menu
lixoBtn.MouseButton1Click:Connect(function()
	menuOpen = not menuOpen
	frame.Visible = menuOpen
end)

-- Aimbot visual
aimbot.MouseButton1Click:Connect(function()
	aimbotOn = not aimbotOn
	fovCircle.Visible = aimbotOn
	aimbot.Text = aimbotOn and "AIMBOT [ON]" or "AIMBOT"
end)

-- Silent visual
silent.MouseButton1Click:Connect(function()
	silent.Text = silent.Text == "SILENT" and "SILENT [ON]" or "SILENT"
end)

-- Aumentar / diminuir FOV
UserInputService.InputBegan:Connect(function(input)
	if input.KeyCode == Enum.KeyCode.Equals then
		fovCircle.Size += UDim2.new(0,20,0,20)
	end
	if input.KeyCode == Enum.KeyCode.Minus then
		fovCircle.Size -= UDim2.new(0,20,0,20)
	end
end)
