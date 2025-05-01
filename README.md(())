local player = game:GetService("Players").LocalPlayer
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
gui.Name = "NQHX_Menu"
gui.ResetOnSpawn = false

-- Botão flutuante
local flutuante = Instance.new("TextButton", gui)
flutuante.Size = UDim2.new(0, 120, 0, 40)
flutuante.Position = UDim2.new(0, 100, 0, 100)
flutuante.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
flutuante.TextColor3 = Color3.new(1, 1, 1)
flutuante.Text = "NQHX-oficial"
flutuante.Font = Enum.Font.GothamBold
flutuante.TextSize = 16
flutuante.Visible = false
flutuante.Active = true
flutuante.Draggable = true
flutuante.BorderSizePixel = 0
flutuante.AutoButtonColor = false
flutuante.BackgroundTransparency = 0.2

-- Menu principal com fundo transparente
local menu = Instance.new("Frame", gui)
menu.Size = UDim2.new(0, 280, 1, 0)
menu.Position = UDim2.new(0, 0, 0, 0)
menu.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
menu.BackgroundTransparency = 0.3
menu.BorderSizePixel = 0

-- Título
local titulo = Instance.new("TextLabel", menu)
titulo.Size = UDim2.new(1, -40, 0, 60)
titulo.Position = UDim2.new(0, 10, 0, 10)
titulo.BackgroundTransparency = 1
titulo.Text = "NQHX-oficial"
titulo.TextColor3 = Color3.new(1, 1, 1)
titulo.TextXAlignment = Enum.TextXAlignment.Left
titulo.TextYAlignment = Enum.TextYAlignment.Top
titulo.Font = Enum.Font.GothamBold
titulo.TextSize = 20
titulo.TextWrapped = true

-- Botão fechar
local fechar = Instance.new("TextButton", menu)
fechar.Size = UDim2.new(0, 28, 0, 28)
fechar.Position = UDim2.new(1, -35, 0, 6)
fechar.Text = "X"
fechar.TextColor3 = Color3.new(1, 1, 1)
fechar.Font = Enum.Font.GothamBold
fechar.TextSize = 18
fechar.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
fechar.BorderSizePixel = 0
fechar.AutoButtonColor = false

-- Painel lateral do Aimbot-Mobile
local painelAimbot = Instance.new("Frame", menu)
painelAimbot.Size = UDim2.new(0, 240, 0, 100)
painelAimbot.Position = UDim2.new(0, 300, 0, 80)
painelAimbot.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
painelAimbot.BackgroundTransparency = 0.2
painelAimbot.BorderSizePixel = 0
painelAimbot.Visible = false

-- Botão ATIVAR
local ativarBtn = Instance.new("TextButton", painelAimbot)
ativarBtn.Size = UDim2.new(0, 100, 0, 40)
ativarBtn.Position = UDim2.new(0, 10, 0, 10)
ativarBtn.Text = "Ativar"
ativarBtn.TextColor3 = Color3.new(1, 1, 1)
ativarBtn.Font = Enum.Font.GothamBold
ativarBtn.TextSize = 18
ativarBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
ativarBtn.BorderSizePixel = 0

-- Botão DESATIVAR
local desativarBtn = Instance.new("TextButton", painelAimbot)
desativarBtn.Size = UDim2.new(0, 100, 0, 40)
desativarBtn.Position = UDim2.new(0, 120, 0, 10)
desativarBtn.Text = "Desativar"
desativarBtn.TextColor3 = Color3.new(1, 1, 1)
desativarBtn.Font = Enum.Font.GothamBold
desativarBtn.TextSize = 18
desativarBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
desativarBtn.BorderSizePixel = 0

-- Criar botão estilizado
local function criarBotao(nome, ordem, onClick)
	local botao = Instance.new("TextButton", menu)
	botao.Size = UDim2.new(1, -20, 0, 40)
	botao.Position = UDim2.new(0, 10, 0, 80 + (ordem - 1) * 45)
	botao.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	botao.TextColor3 = Color3.new(1, 1, 1)
	botao.Text = nome
	botao.Font = Enum.Font.Gotham
	botao.TextSize = 18
	botao.AutoButtonColor = true
	botao.BorderSizePixel = 0
	botao.BackgroundTransparency = 0.05
	botao.TextWrapped = true
	botao.TextXAlignment = Enum.TextXAlignment.Center

	if onClick then
		botao.MouseButton1Click:Connect(onClick)
	end

	return botao
end

-- Aimbot-Mobile painel toggle
local aimbotMobileAberto = false
local function togglePainelAimbot()
	aimbotMobileAberto = not aimbotMobileAberto
	painelAimbot.Visible = aimbotMobileAberto
end

-- Fly System
local flying = false
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local function toggleFly()
	local char = player.Character
	local root = char and char:FindFirstChild("HumanoidRootPart")
	if not root then return end

	flying = not flying
	if flying then
		local bv = Instance.new("BodyVelocity", root)
		bv.Name = "FlyVelocity"
		bv.MaxForce = Vector3.new(1e5, 1e5, 1e5)
		bv.Velocity = Vector3.zero

		RunService:BindToRenderStep("Fly", Enum.RenderPriority.Character.Value + 1, function()
			local move = Vector3.new(
				(UIS:IsKeyDown(Enum.KeyCode.D) and 1 or 0) - (UIS:IsKeyDown(Enum.KeyCode.A) and 1 or 0),
				(UIS:IsKeyDown(Enum.KeyCode.Space) and 1 or 0) - (UIS:IsKeyDown(Enum.KeyCode.LeftControl) and 1 or 0),
				(UIS:IsKeyDown(Enum.KeyCode.S) and 1 or 0) - (UIS:IsKeyDown(Enum.KeyCode.W) and 1 or 0)
			)
			bv.Velocity = (player.Character.HumanoidRootPart.CFrame:VectorToWorldSpace(move)) * 70
		end)
	else
		local root = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
		if root and root:FindFirstChild("FlyVelocity") then
			root.FlyVelocity:Destroy()
		end
		RunService:UnbindFromRenderStep("Fly")
	end
end

-- Atalho F
UIS.InputBegan:Connect(function(input, gpe)
	if gpe then return end
	if input.KeyCode == Enum.KeyCode.F then
		toggleFly()
	end
end)

-- Botões principais
criarBotao("Aimbot-Mobile", 1, togglePainelAimbot)
criarBotao("Aimbot-PC", 2, function()
	print("[Aimbot-PC] botão clicado.")
end)
criarBotao("Fly", 3, toggleFly)

-- Fechar menu
fechar.MouseButton1Click:Connect(function()
	menu.Visible = false
	flutuante.Visible = true
end)

-- Reabrir menu
flutuante.MouseButton1Click:Connect(function()
	menu.Visible = true
	flutuante.Visible = false
end)
