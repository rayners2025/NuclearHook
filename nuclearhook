-- Nuclear.Hook v2.8 | Project Delta Exclusive | Made by SILENT
-- ============================================================
-- DEV BUILD - not public
-- Game check: only fully activates in Project Delta
-- ============================================================

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")
local Lighting = game:GetService("Lighting")
local MarketplaceService = game:GetService("MarketplaceService")
local LocalPlayer = Players.LocalPlayer
local Camera = workspace.CurrentCamera or workspace:WaitForChild("Camera", 10)
local Mouse = LocalPlayer:GetMouse()
local UseDrawing = Drawing ~= nil

-- ============ PROJECT DELTA GAME CHECK ============
local gameName = "Unknown"
local isProjectDelta = false
pcall(function()
	gameName = MarketplaceService:GetProductInfo(game.PlaceId).Name
end)
if gameName:lower():find("delta") then
	isProjectDelta = true
end
print("[Nuclear.Hook] Game detected: " .. gameName .. " | Project Delta: " .. tostring(isProjectDelta))

local Theme = {
	Bg = Color3.fromRGB(16, 10, 10),
	Top = Color3.fromRGB(28, 14, 14),
	Card = Color3.fromRGB(34, 18, 18),
	Accent = Color3.fromRGB(255, 60, 60),
	Accent2 = Color3.fromRGB(0, 220, 90),
	Text = Color3.fromRGB(255, 235, 235),
	Dim = Color3.fromRGB(190, 140, 140),
	Danger = Color3.fromRGB(255, 70, 90)
}

local function TintCard()
	return Theme.Card
end

-- ============ RAINBOW OUTLINE ENGINE ============
_G.RainbowOutline = false
local strokeTargets = {}
local function RegStroke(stroke)
	if stroke then strokeTargets[#strokeTargets + 1] = stroke end
end
local uiHue = 0
RunService.RenderStepped:Connect(function(dt)
	if _G.RainbowOutline then
		uiHue = (uiHue + dt * 0.3) % 1
		local col = Color3.fromHSV(uiHue, 0.7, 1)
		for _, s in ipairs(strokeTargets) do
			if s and s.Parent then
				pcall(function() s.Color = col end)
			end
		end
	end
end)

-- ============ LOADING ANIMATION ============
local LoadGui = Instance.new("ScreenGui")
LoadGui.Name = "NuclearLoad"
LoadGui.ResetOnSpawn = false
LoadGui.IgnoreGuiInset = true
LoadGui.DisplayOrder = 100
LoadGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local LoadBg = Instance.new("Frame")
LoadBg.Size = UDim2.new(1, 0, 1, 0)
LoadBg.BackgroundColor3 = Color3.fromRGB(5, 5, 5)
LoadBg.BorderSizePixel = 0
LoadBg.Parent = LoadGui

local LoadTitle = Instance.new("TextLabel")
LoadTitle.Size = UDim2.new(1, 0, 0, 50)
LoadTitle.Position = UDim2.new(0, 0, 0.4, -60)
LoadTitle.BackgroundTransparency = 1
LoadTitle.Text = "NUCLEAR.HOOK"
LoadTitle.TextColor3 = Theme.Accent
LoadTitle.Font = Enum.Font.GothamBlack
LoadTitle.TextSize = 44
LoadTitle.Parent = LoadBg

local LoadVer = Instance.new("TextLabel")
LoadVer.Size = UDim2.new(1, 0, 0, 24)
LoadVer.Position = UDim2.new(0, 0, 0.4, -8)
LoadVer.BackgroundTransparency = 1
LoadVer.RichText = true
LoadVer.Text = "<font color=\"#ff3b3b\">DEV</font> v1.3"
LoadVer.Font = Enum.Font.GothamBold
LoadVer.TextSize = 16
LoadVer.Parent = LoadBg

local LoadPct = Instance.new("TextLabel")
LoadPct.Size = UDim2.new(1, 0, 0, 30)
LoadPct.Position = UDim2.new(0, 0, 0.55, 0)
LoadPct.BackgroundTransparency = 1
LoadPct.Text = "0%"
LoadPct.TextColor3 = Theme.Text
LoadPct.Font = Enum.Font.GothamBold
LoadPct.TextSize = 24
LoadPct.Parent = LoadBg

local LoadBarBg = Instance.new("Frame")
LoadBarBg.Size = UDim2.new(0, 400, 0, 10)
LoadBarBg.Position = UDim2.new(0.5, -200, 0.55, 38)
LoadBarBg.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
LoadBarBg.BorderSizePixel = 0
LoadBarBg.Parent = LoadBg
Instance.new("UICorner", LoadBarBg).CornerRadius = UDim.new(1, 0)

local LoadBar = Instance.new("Frame")
LoadBar.Size = UDim2.new(0, 0, 1, 0)
LoadBar.BackgroundColor3 = Theme.Accent
LoadBar.BorderSizePixel = 0
LoadBar.Parent = LoadBarBg
Instance.new("UICorner", LoadBar).CornerRadius = UDim.new(1, 0)

-- Key GUI (created now, hidden until loading done)
local VALID_KEYS = { "123", "123", "123", "123", "123" }

local KeyGui = Instance.new("ScreenGui")
KeyGui.Name = "NuclearKey"
KeyGui.ResetOnSpawn = false
KeyGui.Enabled = false
KeyGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local KeyFrame = Instance.new("Frame")
KeyFrame.Size = UDim2.new(0, 360, 0, 200)
KeyFrame.Position = UDim2.new(0.5, -180, 0.5, -100)
KeyFrame.BackgroundColor3 = Theme.Bg
KeyFrame.BorderSizePixel = 0
KeyFrame.Parent = KeyGui
Instance.new("UICorner", KeyFrame).CornerRadius = UDim.new(0, 12)

local KeyStroke = Instance.new("UIStroke", KeyFrame)
KeyStroke.Color = Theme.Accent
KeyStroke.Thickness = 1
KeyStroke.Transparency = 0.4
RegStroke(KeyStroke)

local KeyTitle = Instance.new("TextLabel")
KeyTitle.Size = UDim2.new(1, 0, 0, 26)
KeyTitle.Position = UDim2.new(0, 0, 0, 10)
KeyTitle.BackgroundTransparency = 1
KeyTitle.Text = "NUCLEAR.HOOK"
KeyTitle.TextColor3 = Theme.Accent
KeyTitle.Font = Enum.Font.GothamBlack
KeyTitle.TextSize = 22
KeyTitle.Parent = KeyFrame

local KeyVer = Instance.new("TextLabel")
KeyVer.Size = UDim2.new(1, 0, 0, 16)
KeyVer.Position = UDim2.new(0, 0, 0, 36)
KeyVer.BackgroundTransparency = 1
KeyVer.RichText = true
KeyVer.Text = "<font color=\"#ff3b3b\">DEV</font> v1.3"
KeyVer.Font = Enum.Font.GothamBold
KeyVer.TextSize = 12
KeyVer.Parent = KeyFrame

local KeySub = Instance.new("TextLabel")
KeySub.Size = UDim2.new(1, 0, 0, 16)
KeySub.Position = UDim2.new(0, 0, 0, 54)
KeySub.BackgroundTransparency = 1
KeySub.Text = "Enter key to continue"
KeySub.TextColor3 = Theme.Dim
KeySub.Font = Enum.Font.Gotham
KeySub.TextSize = 12
KeySub.Parent = KeyFrame

local KeyBox = Instance.new("TextBox")
KeyBox.Size = UDim2.new(0.82, 0, 0, 36)
KeyBox.Position = UDim2.new(0.09, 0, 0.44, 0)
KeyBox.BackgroundColor3 = Theme.Card
KeyBox.Text = ""
KeyBox.PlaceholderText = "Key..."
KeyBox.TextColor3 = Theme.Text
KeyBox.Font = Enum.Font.Gotham
KeyBox.TextSize = 15
KeyBox.Parent = KeyFrame
Instance.new("UICorner", KeyBox).CornerRadius = UDim.new(0, 7)

local KeyBtn = Instance.new("TextButton")
KeyBtn.Size = UDim2.new(0.82, 0, 0, 36)
KeyBtn.Position = UDim2.new(0.09, 0, 0.74, 0)
KeyBtn.BackgroundColor3 = Theme.Accent
KeyBtn.Text = "Unlock"
KeyBtn.TextColor3 = Color3.new(0, 0, 0)
KeyBtn.Font = Enum.Font.GothamBold
KeyBtn.TextSize = 15
KeyBtn.Parent = KeyFrame
Instance.new("UICorner", KeyBtn).CornerRadius = UDim.new(0, 7)

local KeyWarn = Instance.new("TextLabel")
KeyWarn.Size = UDim2.new(1, 0, 0, 14)
KeyWarn.Position = UDim2.new(0, 0, 0, 178)
KeyWarn.BackgroundTransparency = 1
KeyWarn.Text = ""
KeyWarn.TextColor3 = Color3.fromRGB(255, 80, 80)
KeyWarn.Font = Enum.Font.Gotham
KeyWarn.TextSize = 10
KeyWarn.Parent = KeyFrame

local function CheckKey(txt)
	for _, k in ipairs(VALID_KEYS) do
		if txt == k then return true end
	end
	return false
end

-- Run loading animation BEFORE anything else boots
task.spawn(function()
	for i = 0, 100 do
		LoadPct.Text = i .. "%"
		LoadBar.Size = UDim2.new(i / 100, 0, 1, 0)
		-- flash between red and green
		LoadBar.BackgroundColor3 = (i % 2 == 0) and Theme.Accent or Theme.Accent2
		task.wait(0.02)
	end
	task.wait(0.3)
	LoadGui:Destroy()
	KeyGui.Enabled = true
end)

-- MAIN GUI (built behind loading screen)
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "NuclearHook"
ScreenGui.ResetOnSpawn = false
ScreenGui.Enabled = false
ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local Main = Instance.new("Frame")
Main.Size = UDim2.new(0, 780, 0, 480)
Main.Position = UDim2.new(0.5, -390, 0.5, -240)
Main.BackgroundColor3 = Theme.Bg
Main.BorderSizePixel = 0
Main.Active = true
Main.Draggable = true
Main.Parent = ScreenGui
Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 10)
Main.Size = UDim2.new(0, 0, 0, 0)
Main.BackgroundTransparency = 1

local MainStroke = Instance.new("UIStroke", Main)
MainStroke.Color = Theme.Accent
MainStroke.Thickness = 1.5
MainStroke.Transparency = 0.25
RegStroke(MainStroke)

local Top = Instance.new("Frame")
Top.Size = UDim2.new(1, 0, 0, 52)
Top.BackgroundColor3 = Theme.Top
Top.BorderSizePixel = 0
Top.Parent = Main
Instance.new("UICorner", Top).CornerRadius = UDim.new(0, 10)

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(0, 220, 0, 26)
Title.Position = UDim2.new(0, 15, 0, 5)
Title.BackgroundTransparency = 1
Title.Text = "NUCLEAR.HOOK"
Title.TextColor3 = Theme.Accent
Title.Font = Enum.Font.GothamBlack
Title.TextSize = 18
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = Top

local Ver = Instance.new("TextLabel")
Ver.Size = UDim2.new(0, 220, 0, 16)
Ver.Position = UDim2.new(0, 15, 0, 30)
Ver.BackgroundTransparency = 1
Ver.RichText = true
Ver.Text = "<font color=\"#ff3b3b\">DEV</font> v1.3"
Ver.Font = Enum.Font.GothamBold
Ver.TextSize = 11
Ver.TextXAlignment = Enum.TextXAlignment.Left
Ver.Parent = Top

local MadeBy = Instance.new("TextLabel")
MadeBy.Size = UDim2.new(0, 150, 0, 16)
MadeBy.Position = UDim2.new(0, 15, 0, 44)
MadeBy.BackgroundTransparency = 1
MadeBy.Text = "made by SILENT"
MadeBy.TextColor3 = Theme.Accent2
MadeBy.Font = Enum.Font.GothamBold
MadeBy.TextSize = 10
MadeBy.TextXAlignment = Enum.TextXAlignment.Left
MadeBy.Parent = Top

local Close = Instance.new("TextButton")
Close.Size = UDim2.new(0, 42, 0, 52)
Close.Position = UDim2.new(1, -42, 0, 0)
Close.BackgroundTransparency = 1
Close.Text = "x"
Close.TextColor3 = Theme.Danger
Close.Font = Enum.Font.GothamBold
Close.TextSize = 22
Close.Parent = Top

local TabBar = Instance.new("Frame")
TabBar.Size = UDim2.new(1, -300, 1, 0)
TabBar.Position = UDim2.new(0, 245, 0, 0)
TabBar.BackgroundTransparency = 1
TabBar.Parent = Top

local TabLayout = Instance.new("UIListLayout")
TabLayout.FillDirection = Enum.FillDirection.Horizontal
TabLayout.Padding = UDim.new(0, 5)
TabLayout.Parent = TabBar

local Content = Instance.new("Frame")
Content.Size = UDim2.new(1, -24, 1, -66)
Content.Position = UDim2.new(0, 12, 0, 58)
Content.BackgroundTransparency = 1
Content.Parent = Main

local Tabs, Current = {}, nil

local function MakeTab(name)
	local b = Instance.new("TextButton")
	b.Size = UDim2.new(0, 78, 0, 29)
	b.BackgroundColor3 = Theme.Card
	b.Text = name
	b.TextColor3 = Theme.Dim
	b.Font = Enum.Font.Gotham
	b.TextSize = 13
	b.AutoButtonColor = false
	b.Parent = TabBar
	Instance.new("UICorner", b).CornerRadius = UDim.new(0, 6)

	local page = Instance.new("ScrollingFrame")
	page.Size = UDim2.new(1, 0, 1, 0)
	page.BackgroundTransparency = 1
	page.BorderSizePixel = 0
	page.ScrollBarThickness = 4
	page.ScrollBarImageColor3 = Theme.Accent
	page.Visible = false
	page.AutomaticCanvasSize = Enum.AutomaticSize.Y
	page.Parent = Content

	local lay = Instance.new("UIListLayout")
	lay.Padding = UDim.new(0, 6)
	lay.Parent = page

	local pad = Instance.new("UIPadding")
	pad.PaddingTop = UDim.new(0, 4)
	pad.Parent = page

	Tabs[name] = { Btn = b, Page = page }

	b.MouseButton1Click:Connect(function()
		if Current then
			Tabs[Current].Btn.BackgroundColor3 = Theme.Card
			Tabs[Current].Btn.TextColor3 = Theme.Dim
			Tabs[Current].Page.Visible = false
		end
		Current = name
		b.BackgroundColor3 = Theme.Accent
		b.TextColor3 = Color3.new(0, 0, 0)
		page.Visible = true
	end)
	return page
end

local Combat = MakeTab("Combat")
local Visuals = MakeTab("Visuals")
local Loot = MakeTab("Loot")
local World = MakeTab("World")
local Misc = MakeTab("Misc")
local Settings = MakeTab("Settings")

Tabs["Combat"].Btn.BackgroundColor3 = Theme.Accent
Tabs["Combat"].Btn.TextColor3 = Color3.new(0, 0, 0)
Tabs["Combat"].Page.Visible = true
Current = "Combat"

-- UI HELPERS
local function Section(parent, text)
	local l = Instance.new("TextLabel")
	l.Size = UDim2.new(1, 0, 0, 20)
	l.BackgroundTransparency = 1
	l.Text = text
	l.TextColor3 = Theme.Accent
	l.Font = Enum.Font.GothamBold
	l.TextSize = 13
	l.TextXAlignment = Enum.TextXAlignment.Left
	l.Parent = parent
end

local function Note(parent, text)
	local l = Instance.new("TextLabel")
	l.Size = UDim2.new(1, 0, 0, 18)
	l.BackgroundTransparency = 1
	l.Text = text
	l.TextColor3 = Theme.Dim
	l.Font = Enum.Font.Gotham
	l.TextSize = 12
	l.TextXAlignment = Enum.TextXAlignment.Left
	l.Parent = parent
end

local function Toggle(parent, text, default, cb)
	local on = default or false
	local f = Instance.new("Frame")
	f.Size = UDim2.new(1, 0, 0, 30)
	f.BackgroundColor3 = Theme.Card
	f.Parent = parent
	Instance.new("UICorner", f).CornerRadius = UDim.new(0, 6)

	local l = Instance.new("TextLabel")
	l.Size = UDim2.new(1, -52, 1, 0)
	l.Position = UDim2.new(0, 12, 0, 0)
	l.BackgroundTransparency = 1
	l.Text = text
	l.TextColor3 = Theme.Text
	l.Font = Enum.Font.Gotham
	l.TextSize = 13
	l.TextXAlignment = Enum.TextXAlignment.Left
	l.Parent = f

	local t = Instance.new("TextButton")
	t.Size = UDim2.new(0, 38, 0, 18)
	t.Position = UDim2.new(1, -46, 0.5, -9)
	t.BackgroundColor3 = on and Theme.Accent or Color3.fromRGB(48, 26, 26)
	t.Text = ""
	t.AutoButtonColor = false
	t.Parent = f
	Instance.new("UICorner", t).CornerRadius = UDim.new(1, 0)

	local c = Instance.new("Frame")
	c.Size = UDim2.new(0, 14, 0, 14)
	c.Position = on and UDim2.new(1, -16, 0.5, -7) or UDim2.new(0, 2, 0.5, -7)
	c.BackgroundColor3 = Color3.new(1, 1, 1)
	c.Parent = t
	Instance.new("UICorner", c).CornerRadius = UDim.new(1, 0)

	t.MouseButton1Click:Connect(function()
		on = not on
		TweenService:Create(t, TweenInfo.new(0.12), { BackgroundColor3 = on and Theme.Accent or Color3.fromRGB(48, 26, 26) }):Play()
		TweenService:Create(c, TweenInfo.new(0.12), { Position = on and UDim2.new(1, -16, 0.5, -7) or UDim2.new(0, 2, 0.5, -7) }):Play()
		if cb then cb(on) end
	end)
end

local function Slider(parent, text, min, max, default, suffix, cb)
	local value = default
	local f = Instance.new("Frame")
	f.Size = UDim2.new(1, 0, 0, 46)
	f.BackgroundColor3 = Theme.Card
	f.Parent = parent
	Instance.new("UICorner", f).CornerRadius = UDim.new(0, 6)

	local lbl = Instance.new("TextLabel")
	lbl.Size = UDim2.new(1, -70, 0, 18)
	lbl.Position = UDim2.new(0, 12, 0, 6)
	lbl.BackgroundTransparency = 1
	lbl.Text = text
	lbl.TextColor3 = Theme.Text
	lbl.Font = Enum.Font.Gotham
	lbl.TextSize = 13
	lbl.TextXAlignment = Enum.TextXAlignment.Left
	lbl.Parent = f

	local vLbl = lbl:Clone()
	vLbl.Size = UDim2.new(0, 56, 0, 18)
	vLbl.Position = UDim2.new(1, -64, 0, 6)
	vLbl.Text = tostring(value) .. suffix
	vLbl.TextColor3 = Theme.Accent2
	vLbl.Font = Enum.Font.GothamBold
	vLbl.TextXAlignment = Enum.TextXAlignment.Right
	vLbl.Parent = f

	local track = Instance.new("Frame")
	track.Size = UDim2.new(1, -24, 0, 6)
	track.Position = UDim2.new(0, 12, 0, 32)
	track.BackgroundColor3 = Color3.fromRGB(40, 22, 22)
	track.Parent = f
	Instance.new("UICorner", track).CornerRadius = UDim.new(1, 0)

	local fill = Instance.new("Frame")
	fill.Size = UDim2.new((value - min) / (max - min), 0, 1, 0)
	fill.BackgroundColor3 = Theme.Accent2
	fill.Parent = track
	Instance.new("UICorner", fill).CornerRadius = UDim.new(1, 0)

	local knob = Instance.new("TextButton")
	knob.Size = UDim2.new(0, 16, 0, 16)
	knob.Position = UDim2.new((value - min) / (max - min), -8, 0.5, -8)
	knob.BackgroundColor3 = Color3.new(1, 1, 1)
	knob.Text = ""
	knob.AutoButtonColor = false
	knob.Parent = track
	Instance.new("UICorner", knob).CornerRadius = UDim.new(1, 0)

	local dragging = false
	local function UpdateFromMouse()
		local ratio = math.clamp((Mouse.X - track.AbsolutePosition.X) / track.AbsoluteSize.X, 0, 1)
		value = math.clamp(math.floor(min + (max - min) * ratio + 0.5), min, max)
		ratio = (value - min) / (max - min)
		fill.Size = UDim2.new(ratio, 0, 1, 0)
		knob.Position = UDim2.new(ratio, -8, 0.5, -8)
		vLbl.Text = tostring(value) .. suffix
		if cb then cb(value) end
	end

	knob.MouseButton1Down:Connect(function() dragging = true end)
	UserInputService.InputEnded:Connect(function(inp)
		if inp.UserInputType == Enum.UserInputType.MouseButton1 then dragging = false end
	end)
	UserInputService.InputChanged:Connect(function(inp)
		if inp.UserInputType == Enum.UserInputType.MouseMovement and dragging then UpdateFromMouse() end
	end)
end

-- KEYBIND SYSTEM
local Binds = {
	Silent    = Enum.UserInputType.MouseButton1,
	Trigger   = Enum.KeyCode.T,
	Spin      = Enum.KeyCode.V,
	Hitbox    = Enum.KeyCode.H,
	Pred      = Enum.KeyCode.P,
	AntiDrop  = Enum.KeyCode.G,
	InstantHit= Enum.KeyCode.U,
	RageBot   = Enum.KeyCode.R,
	
}

local bindWaiting = nil
local BindButtons = {}

local function GetBindName(bind)
	if typeof(bind) == "EnumItem" then
		if bind.EnumType == Enum.KeyCode then
			return bind.Name
		elseif bind.EnumType == Enum.UserInputType then
			if bind == Enum.UserInputType.MouseButton1 then return "M1" end
			if bind == Enum.UserInputType.MouseButton2 then return "M2" end
			if bind == Enum.UserInputType.MouseButton3 then return "M3" end
			if bind == Enum.UserInputType.MouseButton4 then return "M4" end
			return bind.Name
		end
	end
	return "None"
end

local function RefreshBindButtons()
	for name, btn in pairs(BindButtons) do
		btn.Text = GetBindName(Binds[name])
	end
end

local function IsBindDown(bind)
	if not bind then return false end
	if bind.EnumType == Enum.KeyCode then
		return UserInputService:IsKeyDown(bind)
	elseif bind.EnumType == Enum.UserInputType then
		return UserInputService:IsMouseButtonPressed(bind)
	end
	return false
end

local function ToggleWithBind(parent, text, default, bindName, cb)
	local on = default or false

	local f = Instance.new("Frame")
	f.Size = UDim2.new(1, 0, 0, 30)
	f.BackgroundColor3 = Theme.Card
	f.Parent = parent
	Instance.new("UICorner", f).CornerRadius = UDim.new(0, 6)

	local l = Instance.new("TextLabel")
	l.Size = UDim2.new(1, -145, 1, 0)
	l.Position = UDim2.new(0, 12, 0, 0)
	l.BackgroundTransparency = 1
	l.Text = text
	l.TextColor3 = Theme.Text
	l.Font = Enum.Font.Gotham
	l.TextSize = 13
	l.TextXAlignment = Enum.TextXAlignment.Left
	l.Parent = f

	local bindBtn = Instance.new("TextButton")
	bindBtn.Size = UDim2.new(0, 70, 0, 22)
	bindBtn.Position = UDim2.new(1, -120, 0.5, -11)
	bindBtn.BackgroundColor3 = Color3.fromRGB(58, 30, 30)
	bindBtn.TextColor3 = Theme.Text
	bindBtn.Font = Enum.Font.GothamBold
	bindBtn.TextSize = 12
	bindBtn.Text = GetBindName(Binds[bindName])
	bindBtn.Parent = f
	Instance.new("UICorner", bindBtn).CornerRadius = UDim.new(0, 5)

	BindButtons[bindName] = bindBtn

	bindBtn.MouseButton1Click:Connect(function()
		bindWaiting = bindName
		bindBtn.Text = "..."
	end)

	local t = Instance.new("TextButton")
	t.Size = UDim2.new(0, 38, 0, 18)
	t.Position = UDim2.new(1, -46, 0.5, -9)
	t.BackgroundColor3 = on and Theme.Accent or Color3.fromRGB(48, 26, 26)
	t.Text = ""
	t.AutoButtonColor = false
	t.Parent = f
	Instance.new("UICorner", t).CornerRadius = UDim.new(1, 0)

	local c = Instance.new("Frame")
	c.Size = UDim2.new(0, 14, 0, 14)
	c.Position = on and UDim2.new(1, -16, 0.5, -7) or UDim2.new(0, 2, 0.5, -7)
	c.BackgroundColor3 = Color3.new(1, 1, 1)
	c.Parent = t
	Instance.new("UICorner", c).CornerRadius = UDim.new(1, 0)

	t.MouseButton1Click:Connect(function()
		on = not on
		TweenService:Create(t, TweenInfo.new(0.12), { BackgroundColor3 = on and Theme.Accent or Color3.fromRGB(48, 26, 26) }):Play()
		TweenService:Create(c, TweenInfo.new(0.12), { Position = on and UDim2.new(1, -16, 0.5, -7) or UDim2.new(0, 2, 0.5, -7) }):Play()
		if cb then cb(on) end
	end)
end

-- DROPDOWN SYSTEM
local OpenPopups = {}

local function CloseAllPopups()
	local copy = table.clone(OpenPopups)
	for _, close in ipairs(copy) do
		pcall(close)
	end
end

local function Dropdown(parent, text, options, defaultIdx, cb)
	local idx = defaultIdx or 1
	local open = false

	local f = Instance.new("Frame")
	f.Size = UDim2.new(1, 0, 0, 30)
	f.BackgroundColor3 = Theme.Card
	f.Parent = parent
	Instance.new("UICorner", f).CornerRadius = UDim.new(0, 6)

	local l = Instance.new("TextLabel")
	l.Size = UDim2.new(1, -130, 1, 0)
	l.Position = UDim2.new(0, 12, 0, 0)
	l.BackgroundTransparency = 1
	l.Text = text
	l.TextColor3 = Theme.Text
	l.Font = Enum.Font.Gotham
	l.TextSize = 13
	l.TextXAlignment = Enum.TextXAlignment.Left
	l.Parent = f

	local b = Instance.new("TextButton")
	b.Size = UDim2.new(0, 110, 0, 22)
	b.Position = UDim2.new(1, -120, 0.5, -11)
	b.BackgroundColor3 = Color3.fromRGB(58, 30, 30)
	b.TextColor3 = Theme.Accent2
	b.Font = Enum.Font.GothamBold
	b.TextSize = 11
	b.Text = options[idx]
	b.Parent = f
	Instance.new("UICorner", b).CornerRadius = UDim.new(0, 5)

	local popupGui, popup

	local function ClosePopup()
		open = false
		for i = #OpenPopups, 1, -1 do
			if OpenPopups[i] == ClosePopup then
				table.remove(OpenPopups, i)
				break
			end
		end
		if popupGui then pcall(function() popupGui:Destroy() end) popupGui = nil end
	end

	local function OpenPopup()
		if open then ClosePopup() return end
		open = true
		CloseAllPopups()
		OpenPopups[#OpenPopups + 1] = ClosePopup

		popupGui = Instance.new("ScreenGui")
		popupGui.Name = "NuclearDropdown"
		popupGui.ResetOnSpawn = false
		popupGui.IgnoreGuiInset = true
		popupGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

		local blocker = Instance.new("TextButton")
		blocker.Size = UDim2.new(1, 0, 1, 0)
		blocker.BackgroundTransparency = 1
		blocker.Text = ""
		blocker.ZIndex = 10
		blocker.Parent = popupGui
		blocker.Activated:Connect(ClosePopup)

		local absPos = b.AbsolutePosition
		local absSize = b.AbsoluteSize
		local width = math.max(absSize.X, 180)
		local height = math.min(#options, 9) * 24 + 8
		local vp = Camera.ViewportSize

		local x = absPos.X
		local y = absPos.Y + absSize.Y + 2
		if x + width > vp.X then x = vp.X - width end
		if y + height > vp.Y then y = absPos.Y - height - 2 end
		if y < 0 then y = 0 end

		popup = Instance.new("Frame")
		popup.Size = UDim2.fromOffset(width, height)
		popup.Position = UDim2.fromOffset(x, y)
		popup.BackgroundColor3 = Theme.Bg
		popup.BorderSizePixel = 0
		popup.ZIndex = 11
		popup.Parent = popupGui
		Instance.new("UICorner", popup).CornerRadius = UDim.new(0, 6)

		local stroke = Instance.new("UIStroke", popup)
		stroke.Color = Theme.Accent
		stroke.Thickness = 1
		stroke.Transparency = 0.4
		RegStroke(stroke)

		local list = Instance.new("ScrollingFrame")
		list.Size = UDim2.new(1, -8, 1, -8)
		list.Position = UDim2.new(0, 4, 0, 4)
		list.BackgroundTransparency = 1
		list.BorderSizePixel = 0
		list.ScrollBarThickness = 3
		list.ScrollBarImageColor3 = Theme.Accent2
		list.AutomaticCanvasSize = Enum.AutomaticSize.Y
		list.ZIndex = 12
		list.Parent = popup

		local ll = Instance.new("UIListLayout", list)
		ll.Padding = UDim.new(0, 2)

		for i, opt in ipairs(options) do
			local row = Instance.new("TextButton")
			row.Size = UDim2.new(1, 0, 0, 22)
			row.BackgroundColor3 = (i == idx) and Color3.fromRGB(70, 35, 35) or Theme.Card
			row.Text = opt
			row.TextColor3 = (i == idx) and Theme.Accent2 or Theme.Text
			row.Font = Enum.Font.Gotham
			row.TextSize = 12
			row.TextXAlignment = Enum.TextXAlignment.Left
			row.ZIndex = 13
			row.Parent = list
			Instance.new("UICorner", row).CornerRadius = UDim.new(0, 4)
			local pad = Instance.new("UIPadding", row)
			pad.PaddingLeft = UDim.new(0, 8)

			row.MouseButton1Click:Connect(function()
				idx = i
				b.Text = options[idx]
				ClosePopup()
				if cb then cb(options[idx]) end
			end)
		end
	end

	b.MouseButton1Click:Connect(OpenPopup)

	return {
		Get = function() return options[idx] end,
		Set = function(name)
			for i, o in ipairs(options) do
				if o == name then
					idx = i
					b.Text = o
					return
				end
			end
		end
	}
end

-- FEATURE FLAGS
_G.SilentAim = false
_G.Triggerbot = false
_G.Spinbot = false
_G.HitboxExpander = false
_G.TeamCheck = true
_G.VisCheck = true
_G.Prediction = false
_G.ShowFOV = false
_G.AimFOV = 140
_G.AimPart = "Head"
_G.ESP_Box = false
_G.ESP_Highlight = false
_G.ESP_Names = false
_G.ESP_Health = false
_G.ESP_Distance = false
_G.ESP_Tracer = false
_G.RainbowChams = false
_G.ESP_MaxDistance = 5000
_G.Noclip = false
_G.Watermark = true
_G.AntiDropOff = false
_G.InstantHit = false
_G.HitChance = 100
_G.DropOffTimeout = 0.8
_G.RageBot = false
_G.RageFireRate = 0.1
_G.LootESP = false
_G.LootRenderDistance = 250
_G.LootShowValue = true
_G.LootShowContents = false
_G.LootShowName = true
_G.LootShowPrice = true
_G.InvLookHUD = false
_G.KeybindHUD = false
_G.ForceThird = false
_G.NoRecoil = false

local AimPartList = {
	"Head", "HumanoidRootPart", "UpperTorso", "LowerTorso", "Torso",
	"Left Arm", "Right Arm", "Left Leg", "Right Leg",
	"LeftUpperArm", "RightUpperArm", "LeftLowerArm", "RightLowerArm",
	"LeftUpperLeg", "RightUpperLeg", "LeftLowerLeg", "RightLowerLeg"
}

-- ============ INVENTORY / GEAR DATA ============
local function GetPlayerGearData(plr)
	local char = plr.Character
	local data = { holding = nil, wearing = {}, backpack = {}, items = {} }

	if char then
		local tool = char:FindFirstChildOfClass("Tool")
		if tool then
			data.holding = tool.Name
			local inv = tool:FindFirstChild("Inventory")
			if inv then
				for _, item in ipairs(inv:GetChildren()) do
					local props = item:FindFirstChild("ItemProperties")
					if props then
						local amt = props:GetAttribute("Amount") or 1
						local nm = props:GetAttribute("CallSign") or item.Name
						table.insert(data.items, "  > " .. nm .. (amt > 1 and (" x" .. amt) or ""))
					end
				end
			end
		end
		for _, it in ipairs(char:GetChildren()) do
			if it:IsA("Accessory") then
				table.insert(data.wearing, it.Name)
			elseif it:IsA("Model") and not it:FindFirstChildOfClass("Humanoid") and it.Name ~= "Humanoid" then
				table.insert(data.wearing, it.Name)
			end
		end
		local inv = char:FindFirstChild("Inventory")
		if inv then
			for _, item in ipairs(inv:GetChildren()) do
				local props = item:FindFirstChild("ItemProperties")
				if props then
					local amt = props:GetAttribute("Amount") or 1
					local nm = props:GetAttribute("CallSign") or item.Name
					table.insert(data.items, nm .. (amt > 1 and (" x" .. amt) or ""))
				end
			end
		end
	end

	local bp = plr:FindFirstChild("Backpack")
	if bp then
		for _, it in ipairs(bp:GetChildren()) do
			if it:IsA("Tool") or it:IsA("Model") then
				table.insert(data.backpack, it.Name)
			end
		end
	end
	return data
end

-- ============ INVENTORY CHECKER (OWN SEPARATE GUI WINDOW) ============
local InvGui = Instance.new("ScreenGui")
InvGui.Name = "NuclearInvWindow"
InvGui.ResetOnSpawn = false
InvGui.Enabled = false
InvGui.DisplayOrder = 50
InvGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local InvWin = Instance.new("Frame")
InvWin.Size = UDim2.new(0, 260, 0, 340)
InvWin.Position = UDim2.new(1, -280, 0.5, -170)
InvWin.BackgroundColor3 = Theme.Bg
InvWin.BorderSizePixel = 0
InvWin.Active = true
InvWin.Draggable = true
InvWin.Parent = InvGui
Instance.new("UICorner", InvWin).CornerRadius = UDim.new(0, 8)

local InvWinStroke = Instance.new("UIStroke", InvWin)
InvWinStroke.Color = Theme.Accent
InvWinStroke.Thickness = 1.5
InvWinStroke.Transparency = 0.25
RegStroke(InvWinStroke)

local InvWinTop = Instance.new("Frame")
InvWinTop.Size = UDim2.new(1, 0, 0, 30)
InvWinTop.BackgroundColor3 = Theme.Top
InvWinTop.BorderSizePixel = 0
InvWinTop.Parent = InvWin
Instance.new("UICorner", InvWinTop).CornerRadius = UDim.new(0, 8)

local InvWinTitle = Instance.new("TextLabel")
InvWinTitle.Size = UDim2.new(1, -30, 1, 0)
InvWinTitle.Position = UDim2.new(0, 10, 0, 0)
InvWinTitle.BackgroundTransparency = 1
InvWinTitle.Text = "INVENTORY CHECKER"
InvWinTitle.TextColor3 = Theme.Accent
InvWinTitle.Font = Enum.Font.GothamBold
InvWinTitle.TextSize = 12
InvWinTitle.TextXAlignment = Enum.TextXAlignment.Left
InvWinTitle.Parent = InvWinTop

local InvWinStatus = Instance.new("TextLabel")
InvWinStatus.Size = UDim2.new(1, -110, 1, 0)
InvWinStatus.Position = UDim2.new(0, 110, 0, 0)
InvWinStatus.BackgroundTransparency = 1
InvWinStatus.Text = "no player"
InvWinStatus.TextColor3 = Theme.Dim
InvWinStatus.Font = Enum.Font.Gotham
InvWinStatus.TextSize = 11
InvWinStatus.TextXAlignment = Enum.TextXAlignment.Right
InvWinStatus.Parent = InvWinTop

local InvScroll = Instance.new("ScrollingFrame")
InvScroll.Size = UDim2.new(1, -10, 1, -40)
InvScroll.Position = UDim2.new(0, 5, 0, 34)
InvScroll.BackgroundTransparency = 1
InvScroll.BorderSizePixel = 0
InvScroll.ScrollBarThickness = 4
InvScroll.ScrollBarImageColor3 = Theme.Accent2
InvScroll.AutomaticCanvasSize = Enum.AutomaticSize.Y
InvScroll.Parent = InvWin

local InvScrollLay = Instance.new("UIListLayout", InvScroll)
InvScrollLay.Padding = UDim.new(0, 2)

local lastInvPlr = nil
local lastInvRebuild = 0

local function RebuildInvWindow(d, plrName)
	for _, c in ipairs(InvScroll:GetChildren()) do
		if c:IsA("TextLabel") then c:Destroy() end
	end

	local function Row(text, color)
		local r = Instance.new("TextLabel")
		r.Size = UDim2.new(1, -6, 0, 16)
		r.BackgroundTransparency = 1
		r.Text = text
		r.TextColor3 = color or Theme.Text
		r.Font = Enum.Font.Gotham
		r.TextSize = 11
		r.TextXAlignment = Enum.TextXAlignment.Left
		r.TextTruncate = Enum.TextTruncate.AtEnd
		r.Parent = InvScroll
	end

	Row(plrName, Theme.Accent)
	if d.holding then
		Row("[HOLDING] " .. d.holding, Color3.fromRGB(90, 220, 140))
	else
		Row("[HOLDING] nothing", Theme.Dim)
	end
	if #d.wearing > 0 then
		for _, w in ipairs(d.wearing) do
			Row("[Wearing] " .. w, Color3.fromRGB(120, 200, 255))
		end
	else
		Row("[Wearing] nothing visible", Theme.Dim)
	end
	if #d.backpack > 0 then
		for _, bk in ipairs(d.backpack) do
			Row("[Backpack] " .. bk, Color3.fromRGB(230, 220, 130))
		end
	end
	for _, l in ipairs(d.items) do
		Row(l, Theme.Text)
	end
end

local invLookConn = RunService.Heartbeat:Connect(function()
	if not _G.InvLookHUD then
		InvGui.Enabled = false
		return
	end

	InvGui.Enabled = true

	local cam = workspace.CurrentCamera
	if not cam then return end
	local vp = cam.ViewportSize
	local unitRay = cam:ViewportPointToRay(vp.X / 2, vp.Y / 2)
	local rayParams = RaycastParams.new()
	rayParams.FilterType = Enum.RaycastFilterType.Exclude
	rayParams.FilterDescendantsInstances = { LocalPlayer.Character or nil }
	rayParams.IgnoreWater = true
	local hit = workspace:Raycast(unitRay.Origin, unitRay.Direction * 1500, rayParams)

	local foundPlr = nil
	if hit then
		local model = hit.Instance:FindFirstAncestorOfClass("Model")
		while model do
			local p = Players:GetPlayerFromCharacter(model)
			if p and p ~= LocalPlayer then
				foundPlr = p
				break
			end
			model = model:FindFirstAncestorOfClass("Model")
		end
	end

	if not foundPlr or not foundPlr.Character then
		InvWinStatus.Text = "no player"
		lastInvPlr = nil
		return
	end

	InvWinStatus.Text = foundPlr.Name

	-- Rebuild max every 0.5s or when target changes
	if foundPlr ~= lastInvPlr or os.clock() - lastInvRebuild > 0.5 then
		lastInvPlr = foundPlr
		lastInvRebuild = os.clock()
		RebuildInvWindow(GetPlayerGearData(foundPlr), foundPlr.Name)
	end
end)

-- ============ COMBAT TAB ============
Section(Combat, "Combat")

ToggleWithBind(Combat, "Silent Aim (M1)", false, "Silent", function(v)
	_G.SilentAim = v
end)

ToggleWithBind(Combat, "Triggerbot (Visible Only)", false, "Trigger", function(v)
	_G.Triggerbot = v
end)

ToggleWithBind(Combat, "Spinbot", false, "Spin", function(v)
	_G.Spinbot = v
end)

ToggleWithBind(Combat, "Hitbox Expander", false, "Hitbox", function(v)
	_G.HitboxExpander = v
end)

ToggleWithBind(Combat, "Prediction", false, "Pred", function(v)
	_G.Prediction = v
end)

Section(Combat, "Recoil")
Toggle(Combat, "No Recoil (ALL guns)", false, function(v)
	_G.NoRecoil = v
end)
Note(Combat, isProjectDelta and "Project Delta detected - recoil compensation active" or "NOT in Project Delta - No Recoil may not work")

Section(Combat, "Aim Enhancements")

ToggleWithBind(Combat, "Anti Drop-Off", false, "AntiDrop", function(v)
	_G.AntiDropOff = v
end)

Slider(Combat, "Drop-Off Timeout (ms)", 100, 2000, 800, "ms", function(v)
	_G.DropOffTimeout = v / 1000
end)

ToggleWithBind(Combat, "Instant Hit", false, "InstantHit", function(v)
	_G.InstantHit = v
end)

Slider(Combat, "Hit Chance %", 1, 100, 100, "%", function(v)
	_G.HitChance = v
end)

ToggleWithBind(Combat, "Rage Bot", false, "RageBot", function(v)
	_G.RageBot = v
end)

Slider(Combat, "Rage Fire Rate (ms)", 50, 500, 100, "ms", function(v)
	_G.RageFireRate = v / 1000
end)

Section(Combat, "Aim Settings")
Toggle(Combat, "Show FOV Circle", false, function(v) _G.ShowFOV = v end)
Slider(Combat, "Aim FOV (px)", 20, 400, 140, "", function(v) _G.AimFOV = v end)
local AimPartDrop = Dropdown(Combat, "Aim Part", AimPartList, 1, function(part)
	_G.AimPart = part
end)

Section(Combat, "Filters")
Toggle(Combat, "Team Check", true, function(v) _G.TeamCheck = v end)
Toggle(Combat, "Visibility Check", true, function(v) _G.VisCheck = v end)

-- ============ VISUALS TAB ============
Section(Visuals, "ESP")
Toggle(Visuals, "Box", false, function(v) _G.ESP_Box = v end)
Toggle(Visuals, "Highlight / Chams", false, function(v) _G.ESP_Highlight = v end)
Toggle(Visuals, "Rainbow Chams", false, function(v) _G.RainbowChams = v end)
Toggle(Visuals, "Name Tags", false, function(v) _G.ESP_Names = v end)
Toggle(Visuals, "Health Bar", false, function(v) _G.ESP_Health = v end)
Toggle(Visuals, "Distance", false, function(v) _G.ESP_Distance = v end)
Toggle(Visuals, "Tracer Lines", false, function(v) _G.ESP_Tracer = v end)
Slider(Visuals, "ESP Max Distance", 500, 10000, 5000, "studs", function(v)
	_G.ESP_MaxDistance = v
end)
Note(Visuals, "ESP renders up to max distance (default 5000 studs = super far)")

-- ============ LOOT TAB ============
Section(Loot, "Container ESP")
Toggle(Loot, "Loot Finder ESP", false, function(v)
	_G.LootESP = v
	if not v then
		for _, d in pairs(containerDrawings) do
			for _, obj in pairs(d) do
				pcall(function() obj:Remove() end)
			end
		end
		containerDrawings = {}
	end
end)

Slider(Loot, "Render Distance", 50, 800, 250, "studs", function(v)
	_G.LootRenderDistance = v
end)

Section(Loot, "Player Inventory Checker")
Toggle(Loot, "Show Inventory On Look", false, function(v) _G.InvLookHUD = v end)
Note(Loot, "Look at a player - separate window pops up on the right with full list")

Section(Loot, "Display Options")
Toggle(Loot, "Show Container Name", true, function(v) _G.LootShowName = v end)
Toggle(Loot, "Show Total Price", true, function(v) _G.LootShowPrice = v end)
Toggle(Loot, "Show Item Details", false, function(v) _G.LootShowContents = v end)
Toggle(Loot, "Show Value Tier", true, function(v) _G.LootShowValue = v end)

-- ============ LOOT FINDER ENGINE ============
local containerDrawings = {}

local LootValueCache = {
	["6B45"] = 16, ["AS Val"] = 16, ["ATC Key"] = 4, ["Airfield Key"] = 6,
	["Altyn"] = 16, ["Altyn Visor"] = 8, ["Attak-5 60L"] = 16,
	["Bolts"] = 1, ["Crane Key"] = 6, ["DAGR"] = 8, ["Duct Tape"] = 1,
	["Fast MT"] = 10, ["Flare Gun"] = 8, ["Fueling Station Key"] = 4,
	["Garage Key"] = 4, ["Hammer"] = 1, ["JPC"] = 10, ["Lighthouse Key"] = 6,
	["M4A1"] = 12, ["Nails"] = 1, ["Nuts"] = 1, ["Saiga 12"] = 8,
	["Super Glue"] = 1, ["Village Key"] = 4, ["Wrench"] = 1,
	["RPG-7"] = 16, ["MK12"] = 12, ["Mk23"] = 8, ["SVD"] = 10,
	["AKMN"] = 10, ["PKM"] = 16, ["R700"] = 16, ["TFZ-98S"] = 16,
	["REAP-IR"] = 16, ["SOCOM556-RC2"] = 16, ["Sniper Scope"] = 8,
	["Repair Kit"] = 12, ["EDF Flare Gun"] = 16, ["RGO"] = 4,
	["PEIPSI Water Bottle"] = 1, ["Bandage"] = 1, ["AI-2"] = 2,
	["Max Energy"] = 1, ["Benny's Beans"] = 1, ["Bloxy Cola"] = 1,
	["Condensed Milk"] = 1, ["Comrade CatFrog Soda"] = 1,
	["Rags"] = 1, ["Res Kola"] = 1, ["Junk"] = 1, ["SPSh-44"] = 4,
	["Legendary Gift Box"] = 16
}

local ValueColorMap = {
	[0] = Color3.fromRGB(255, 255, 255),
	[4] = Color3.fromRGB(76, 187, 23),
	[8] = Color3.fromRGB(218, 112, 214),
	[12] = Color3.fromRGB(233, 116, 81),
	[16] = Color3.fromRGB(255, 36, 0)
}

local function GetContainerValueColor(totalValue)
	local highest = -1
	local color = ValueColorMap[0]
	for tier, col in pairs(ValueColorMap) do
		if totalValue >= tier and tier > highest then
			color = col
			highest = tier
		end
	end
	return color
end

local function CleanupContainerDrawings()
	for _, d in pairs(containerDrawings) do
		for _, obj in pairs(d) do
			pcall(function() obj:Remove() end)
		end
	end
	containerDrawings = {}
end

local function CreateContainerDrawing(container)
	if not UseDrawing then return end

	local txt = Drawing.new("Text")
	txt.Center = true
	txt.Font = 2
	txt.Outline = true
	txt.Size = 13

	local subTxt = Drawing.new("Text")
	subTxt.Center = true
	subTxt.Font = 1
	subTxt.Outline = true
	subTxt.Size = 11

	containerDrawings[container] = { main = txt, sub = subTxt }

	containerDrawings[container].con = RunService.RenderStepped:Connect(function()
		if not _G.LootESP then
			txt.Visible = false
			subTxt.Visible = false
			return
		end

		local anchor = container.PrimaryPart or container:FindFirstChildWhichIsA("BasePart", true)
		if not anchor then
			txt.Visible = false
			subTxt.Visible = false
			return
		end

		local char = LocalPlayer.Character
		local myRoot = char and (char:FindFirstChild("HumanoidRootPart") or char:FindFirstChildWhichIsA("BasePart"))
		if not myRoot then
			txt.Visible = false
			subTxt.Visible = false
			return
		end

		local distance = (anchor.Position - myRoot.Position).Magnitude
		if distance > _G.LootRenderDistance then
			txt.Visible = false
			subTxt.Visible = false
			return
		end

		local pos, onScreen = Camera:WorldToViewportPoint(anchor.Position)
		if not onScreen then
			txt.Visible = false
			subTxt.Visible = false
			return
		end

		local displayName = container:GetAttribute("DisplayName") or container.Name
		local totalPrice = 0
		local totalValue = 0
		local itemLines = {}

		local inventory = container:FindFirstChild("Inventory", true)
		if inventory then
			for _, item in ipairs(inventory:GetChildren()) do
				local props = item:FindFirstChild("ItemProperties")
				if props then
					local amount = props:GetAttribute("Amount") or 1
					local itemName = props:GetAttribute("CallSign") or item.Name
					local price = props:GetAttribute("Price") or 0
					totalPrice = totalPrice + (price * amount)
					totalValue = totalValue + ((LootValueCache[itemName] or 1) * amount)
					if #itemLines < 8 then
						table.insert(itemLines, itemName .. (amount > 1 and " x" .. amount or ""))
					end
				end
			end
		end

		local color = GetContainerValueColor(totalValue)

		local lines = {}
		if _G.LootShowName then table.insert(lines, displayName) end
		if _G.LootShowPrice and totalPrice > 0 then table.insert(lines, "$" .. totalPrice) end
		if _G.LootShowValue then
			local tierName = totalValue >= 16 and "Legendary" or totalValue >= 12 and "Epic" or totalValue >= 8 and "Rare" or totalValue >= 4 and "Uncommon" or "Common"
			table.insert(lines, tierName .. " (" .. totalValue .. ")")
		end
		table.insert(lines, math.floor(distance) .. " studs")

		txt.Text = table.concat(lines, "\n")
		txt.Color = color
		txt.Position = Vector2.new(pos.X, pos.Y)
		txt.Visible = true

		if _G.LootShowContents and #itemLines > 0 then
			subTxt.Text = table.concat(itemLines, "\n")
			subTxt.Color = Theme.Dim
			subTxt.Position = Vector2.new(pos.X, pos.Y + 16 + (#lines * 14))
			subTxt.Visible = true
		else
			subTxt.Visible = false
		end
	end)
end

task.spawn(function()
	local found = 0
	for _, v in ipairs(workspace:GetDescendants()) do
		if v:IsA("Model") and v:FindFirstChild("Inventory") then
			CreateContainerDrawing(v)
			found += 1
		end
	end
	print("[Nuclear.Hook] Loot Finder: tracking " .. found .. " containers")

	workspace.DescendantAdded:Connect(function(desc)
		task.wait(0.5)
		if _G.LootESP and desc:IsA("Model") and desc:FindFirstChild("Inventory") and not containerDrawings[desc] then
			CreateContainerDrawing(desc)
		end
	end)
end)

-- ============ WORLD TAB ============
Section(World, "World")
Toggle(World, "Fullbright", false, function(v)
	if v then
		Lighting.Brightness = 2
		Lighting.ClockTime = 14
		Lighting.FogEnd = 9e9
		Lighting.GlobalShadows = false
	else
		Lighting.Brightness = 1
		Lighting.ClockTime = 14
		Lighting.FogEnd = 1000
		Lighting.GlobalShadows = true
	end
end)
Toggle(World, "No Fog", false, function(v) Lighting.FogEnd = v and 9e9 or 1000 end)
Toggle(World, "No Grass", false, function(v)
	for _, obj in ipairs(workspace:GetDescendants()) do
		if obj:IsA("BasePart") and (obj.Material == Enum.Material.Grass or obj.Name:lower():find("grass") or obj.Name:lower():find("leaf")) then
			obj.Transparency = v and 1 or 0
		end
	end
end)
Toggle(World, "Sky Changer", false, function(v)
	if v then
		local sky = Instance.new("Sky")
		sky.SkyboxBk = "rbxassetid://591058823"
		sky.SkyboxDn = "rbxassetid://591059876"
		sky.SkyboxFt = "rbxassetid://591058104"
		sky.SkyboxLf = "rbxassetid://591057843"
		sky.SkyboxRt = "rbxassetid://591057672"
		sky.SkyboxUp = "rbxassetid://591058672"
		sky.Parent = Lighting
	else
		for _, s in ipairs(Lighting:GetChildren()) do
			if s:IsA("Sky") then s:Destroy() end
		end
	end
end)

-- ============ MISC TAB ============
Section(Misc, "Player")
Toggle(Misc, "3rd Person (Forced)", false, function(v)
	_G.ForceThird = v
end)
Toggle(Misc, "Noclip", false, function(v) _G.Noclip = v end)



-- 3RD PERSON ENFORCER
RunService.RenderStepped:Connect(function()
	if unloaded then return end
	if _G.ForceThird then
		pcall(function()
			LocalPlayer.CameraMode = Enum.CameraMode.Classic
			LocalPlayer.CameraMaxZoomDistance = 25
			LocalPlayer.CameraMinZoomDistance = 6
			if not Camera.CameraSubject then
				local char = LocalPlayer.Character
				if char then Camera.CameraSubject = char:FindFirstChildOfClass("Humanoid") end
			end
			local hum = LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
			if hum and hum.CameraOffset ~= Vector3.new(2, 1, 8) then
				hum.CameraOffset = Vector3.new(2, 1, 8)
			end
		end)
	end
end)

-- ============ NO RECOIL ENGINE (Project Delta) ============
-- Project Delta applies recoil as client-side camera kick + viewmodel punch.
-- We compensate by: 1) tracking camera pitch kick from mouse deltas and
-- countering it, 2) zeroing CameraOffset shake, 3) optionally hooking
-- FireSignal so the camera never receives the recoil impulse.
local recoilCompensator = nil
local lastCamCF = nil

local function StartNoRecoil()
	if recoilCompensator then return end
	lastCamCF = Camera.CFrame
	recoilCompensator = RunService.RenderStepped:Connect(function()
		if not _G.NoRecoil then return end
		-- Count camera pitch kick: recoil in Delta rotates the camera up.
		-- We detect fast upward pitch delta right after firing and undo it.
		pcall(function()
			local current = Camera.CFrame
			if lastCamCF then
				local delta = current.Position - lastCamCF.Position
				-- camera position doesn't move on recoil, only rotation.
				-- Compare look vectors; large sudden pitch-up = recoil
				local d1 = lastCamCF.LookVector
				local d2 = current.LookVector
				local pitchDelta = math.asin(math.clamp(d1.Y, -1, 1)) and (math.asin(d2.Y) - math.asin(d1.Y)) or 0
				if pitchDelta > 0.008 then
					-- counter-rotate back down by the same amount
					local x, y, z = current:ToOrientation()
					Camera.CFrame = CFrame.fromOrientation(x - pitchDelta, y, z) + current.Position
				end
			end
			lastCamCF = Camera.CFrame
		end)
		-- Neutralize humanoid camera shake offset
		pcall(function()
			local char = LocalPlayer.Character
			local hum = char and char:FindFirstChildOfClass("Humanoid")
			if hum and hum.CameraOffset.Magnitude > 0.05 then
				hum.CameraOffset = Vector3.new(0, 0, 0)
			end
		end)
	end)
end

local function StopNoRecoil()
	if recoilCompensator then
		recoilCompensator:Disconnect()
		recoilCompensator = nil
	end
end

StartNoRecoil() -- always listening, gated by _G.NoRecoil

-- ============ SETTINGS TAB ============
Section(Settings, "General")
Toggle(Settings, "Watermark", true, function(v) _G.Watermark = v end)
Toggle(Settings, "Keybind HUD", false, function(v)
	_G.KeybindHUD = v
	HudGui.Enabled = v
end)
Toggle(Settings, "Rainbow Outline", false, function(v)
	_G.RainbowOutline = v
end)

Section(Settings, "Config")
local ConfigName = Instance.new("TextBox")
ConfigName.Size = UDim2.new(1, 0, 0, 30)
ConfigName.BackgroundColor3 = Theme.Card
ConfigName.Text = "Default"
ConfigName.TextColor3 = Theme.Text
ConfigName.Font = Enum.Font.Gotham
ConfigName.TextSize = 13
ConfigName.Parent = Settings
Instance.new("UICorner", ConfigName).CornerRadius = UDim.new(0, 7)

local savedConfigs = {}
local function MakeBtn(parent, text, cb)
	local b = Instance.new("TextButton")
	b.Size = UDim2.new(1, 0, 0, 30)
	b.BackgroundColor3 = Theme.Accent
	b.Text = text
	b.TextColor3 = Color3.new(0, 0, 0)
	b.Font = Enum.Font.GothamBold
	b.TextSize = 13
	b.Parent = parent
	Instance.new("UICorner", b).CornerRadius = UDim.new(0, 7)
	b.MouseButton1Click:Connect(cb)
end

MakeBtn(Settings, "Save Config", function()
	savedConfigs[ConfigName.Text] = {
		SilentAim = _G.SilentAim, Triggerbot = _G.Triggerbot, Spinbot = _G.Spinbot,
		HitboxExpander = _G.HitboxExpander,
		ESP_Box = _G.ESP_Box, ESP_Highlight = _G.ESP_Highlight, RainbowChams = _G.RainbowChams,
		ESP_Names = _G.ESP_Names, ESP_Health = _G.ESP_Health, ESP_Distance = _G.ESP_Distance,
		ESP_Tracer = _G.ESP_Tracer, ESP_MaxDistance = _G.ESP_MaxDistance, Noclip = _G.Noclip,
		AimFOV = _G.AimFOV, Prediction = _G.Prediction, AimPart = _G.AimPart,
		AntiDropOff = _G.AntiDropOff, InstantHit = _G.InstantHit, HitChance = _G.HitChance,
		DropOffTimeout = _G.DropOffTimeout, RageBot = _G.RageBot, RageFireRate = _G.RageFireRate,
		LootESP = _G.LootESP, LootRenderDistance = _G.LootRenderDistance,
		InvLookHUD = _G.InvLookHUD, LagSwitch = _G.LagSwitch, LagAmount = _G.LagAmount,
		KeybindHUD = _G.KeybindHUD, ForceThird = _G.ForceThird, NoRecoil = _G.NoRecoil
	}
	print("[Nuclear.Hook] Saved:", ConfigName.Text)
end)

MakeBtn(Settings, "Load Config", function()
	local c = savedConfigs[ConfigName.Text]
	if c then
		for k, v in pairs(c) do _G[k] = v end
		if AimPartDrop then AimPartDrop.Set(_G.AimPart) end
		HudGui.Enabled = _G.KeybindHUD
		print("[Nuclear.Hook] Loaded:", ConfigName.Text)
	end
end)

Section(Settings, "Danger")
Note(Settings, "DEV v1.3 | made by SILENT | Project Delta only")
Note(Settings, "Menu: Right Alt / Right Shift | Silent Aim = M1 | Lag = X")

-- ============ KEYBIND HUD (toggleable, default off) ============
local HudGui = Instance.new("ScreenGui")
HudGui.Name = "NuclearBinds"
HudGui.ResetOnSpawn = false
HudGui.Enabled = false
HudGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local Hud = Instance.new("Frame")
Hud.Size = UDim2.new(0, 260, 0, 440)
Hud.Position = UDim2.new(0, 16, 1, -456)
Hud.BackgroundColor3 = Theme.Bg
Hud.BackgroundTransparency = 0.06
Hud.BorderSizePixel = 0
Hud.Active = true
Hud.Draggable = true
Hud.Parent = HudGui
Instance.new("UICorner", Hud).CornerRadius = UDim.new(0, 8)

local HudStroke = Instance.new("UIStroke", Hud)
HudStroke.Color = Theme.Accent
HudStroke.Thickness = 1
HudStroke.Transparency = 0.35
RegStroke(HudStroke)

local HudPad = Instance.new("UIPadding", Hud)
HudPad.PaddingTop = UDim.new(0, 8)
HudPad.PaddingBottom = UDim.new(0, 8)
HudPad.PaddingLeft = UDim.new(0, 10)
HudPad.PaddingRight = UDim.new(0, 10)

local HudLayout = Instance.new("UIListLayout", Hud)
HudLayout.Padding = UDim.new(0, 3)

local HudTitle = Instance.new("TextLabel")
HudTitle.Size = UDim2.new(1, 0, 0, 24)
HudTitle.BackgroundTransparency = 1
HudTitle.RichText = true
HudTitle.Text = "NUCLEAR.HOOK  <font color=\"#ff3b3b\">DEV</font> v1.3"
HudTitle.TextColor3 = Theme.Accent
HudTitle.Font = Enum.Font.GothamSemibold
HudTitle.TextSize = 13
HudTitle.TextXAlignment = Enum.TextXAlignment.Left
HudTitle.Parent = Hud

local HudMadeBy = Instance.new("TextLabel")
HudMadeBy.Size = UDim2.new(1, 0, 0, 16)
HudMadeBy.BackgroundTransparency = 1
HudMadeBy.Text = "made by SILENT"
HudMadeBy.TextColor3 = Theme.Accent2
HudMadeBy.Font = Enum.Font.GothamBold
HudMadeBy.TextSize = 10
HudMadeBy.TextXAlignment = Enum.TextXAlignment.Left
HudMadeBy.Parent = Hud

local HudDefs = {
	{ Key = "Silent",    Label = "Silent Aim (M1)" },
	{ Key = "Trigger",   Label = "Triggerbot" },
	{ Key = "Spin",      Label = "Spinbot" },
	{ Key = "Hitbox",    Label = "Hitbox Expander" },
	{ Key = "Pred",      Label = "Prediction" },
	{ Key = "AntiDrop",  Label = "Anti Drop-Off" },
	{ Key = "InstantHit",Label = "Instant Hit" },
	{ Key = "RageBot",   Label = "Rage Bot" },
	
}

local BindFlag = {
	Silent    = "SilentAim",
	Trigger   = "Triggerbot",
	Spin      = "Spinbot",
	Hitbox    = "HitboxExpander",
	Pred      = "Prediction",
	AntiDrop  = "AntiDropOff",
	InstantHit= "InstantHit",
	RageBot   = "RageBot",
	
}

local hudRows = {}

local function HudRow(label)
	local row = Instance.new("Frame")
	row.Size = UDim2.new(1, 0, 0, 22)
	row.BackgroundTransparency = 1
	row.Parent = Hud

	local key = Instance.new("TextLabel")
	key.Size = UDim2.new(0, 46, 1, 0)
	key.BackgroundTransparency = 1
	key.Text = "-"
	key.TextColor3 = Theme.Accent
	key.Font = Enum.Font.GothamBold
	key.TextSize = 11
	key.TextXAlignment = Enum.TextXAlignment.Left
	key.Parent = row

	local name = Instance.new("TextLabel")
	name.Size = UDim2.new(1, -106, 1, 0)
	name.Position = UDim2.new(0, 50, 0, 0)
	name.BackgroundTransparency = 1
	name.Text = label
	name.TextColor3 = Theme.Text
	name.Font = Enum.Font.GothamMedium
	name.TextSize = 12
	name.TextXAlignment = Enum.TextXAlignment.Left
	name.Parent = row

	local state = Instance.new("TextLabel")
	state.Size = UDim2.new(0, 44, 1, 0)
	state.Position = UDim2.new(1, -48, 0, 0)
	state.BackgroundTransparency = 1
	state.Text = "OFF"
	state.TextColor3 = Theme.Dim
	state.Font = Enum.Font.GothamBold
	state.TextSize = 10
	state.TextXAlignment = Enum.TextXAlignment.Right
	state.Parent = row

	return { Key = key, State = state }
end

for _, def in ipairs(HudDefs) do
	hudRows[def.Key] = HudRow(def.Label)
end

-- OPEN / CLOSE ANIMATION
local menuOpen = false
local unloaded = false

local function OpenMenu()
	if menuOpen or unloaded then return end
	menuOpen = true
	CloseAllPopups()
	ScreenGui.Enabled = true
	Main.Size = UDim2.new(0, 0, 0, 0)
	Main.BackgroundTransparency = 1
	Main.Position = UDim2.new(0.5, 0, 0.5, 0)
	TweenService:Create(Main, TweenInfo.new(0.35, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
		Size = UDim2.new(0, 780, 0, 480),
		Position = UDim2.new(0.5, -390, 0.5, -240),
		BackgroundTransparency = 0
	}):Play()
end

local function CloseMenu()
	if not menuOpen then return end
	menuOpen = false
	CloseAllPopups()
	local tween = TweenService:Create(Main, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {
		Size = UDim2.new(0, 0, 0, 0),
		Position = UDim2.new(0.5, 0, 0.5, 0),
		BackgroundTransparency = 1
	})
	tween:Play()
	tween.Completed:Connect(function()
		ScreenGui.Enabled = false
	end)
end

Close.MouseButton1Click:Connect(CloseMenu)

-- SCREEN CENTER
local function ScreenCenter()
	local vp = Camera.ViewportSize
	return Vector2.new(vp.X / 2, vp.Y / 2)
end

-- WATERMARK + FOV
local Watermark = UseDrawing and Drawing.new("Text") or nil
if Watermark then
	Watermark.Text = "NUCLEAR.HOOK DEV v1.3 | made by SILENT"
	Watermark.Size = 14
	Watermark.Color = Theme.Accent
	Watermark.Outline = true
	Watermark.OutlineColor = Color3.new(0, 0, 0)
	Watermark.Position = Vector2.new(12, 12)
	Watermark.Visible = _G.Watermark
end

local FOVCircle = UseDrawing and Drawing.new("Circle") or nil
if FOVCircle then
	FOVCircle.Thickness = 1.5
	FOVCircle.Color = Theme.Accent2
	FOVCircle.NumSides = 64
	FOVCircle.Filled = false
	FOVCircle.Visible = false
end

RunService.RenderStepped:Connect(function()
	if unloaded then return end
	if FOVCircle then
		local c = ScreenCenter()
		FOVCircle.Position = c
		FOVCircle.Radius = math.clamp(_G.AimFOV, 5, 2000)
		FOVCircle.Visible = _G.ShowFOV
	end
	if Watermark then
		Watermark.Visible = _G.Watermark
		Watermark.Color = Theme.Accent
	end

	for key, row in pairs(hudRows) do
		row.Key.Text = GetBindName(Binds[key])
		local on = _G[BindFlag[key]] or IsBindDown(Binds[key])
		if on then
			row.State.Text = "ON"
			row.State.TextColor3 = Color3.fromRGB(90, 220, 140)
		else
			row.State.Text = "OFF"
			row.State.TextColor3 = Theme.Dim
		end
	end
end)

-- AIM LOGIC
local function isVisible(targetPart)
	if not targetPart then return true end
	local origin = Camera.CFrame.Position
	local direction = (targetPart.Position - origin)
	local ray = workspace:Raycast(origin, direction)
	if ray then
		return ray.Instance:IsDescendantOf(targetPart.Parent)
	end
	return true
end

local function FindPart(char, name)
	if not char then return nil end
	local p = char:FindFirstChild(name)
	if p then return p end
	for _, d in ipairs(char:GetDescendants()) do
		if d.Name == name and d:IsA("BasePart") then return d end
	end
	return nil
end

local function GetAimPart(char)
	if not char then return nil end
	local p = _G.AimPart and FindPart(char, _G.AimPart)
	if p then return p end
	for _, name in ipairs(AimPartList) do
		local q = FindPart(char, name)
		if q then return q end
	end
	return char:FindFirstChild("HumanoidRootPart") or char:FindFirstChild("Head")
end

local lastTargetInfo = { plr = nil, lastSeen = 0 }

local function GetClosest(center)
	local closest, best = nil, math.huge
	for _, plr in ipairs(Players:GetPlayers()) do
		if plr == LocalPlayer then continue end
		local char = plr.Character
		local root = char and char:FindFirstChild("HumanoidRootPart")
		local hum = char and char:FindFirstChildOfClass("Humanoid")
		if not root or not hum or hum.Health <= 0 then continue end
		if _G.TeamCheck and plr.Team and plr.Team == LocalPlayer.Team then continue end
		-- ESP max distance also gates aim
		if (root.Position - Camera.CFrame.Position).Magnitude > _G.ESP_MaxDistance then continue end

		local aimPart = GetAimPart(char) or root
		if _G.VisCheck and not isVisible(aimPart) then
			if not (_G.AntiDropOff or IsBindDown(Binds.AntiDrop)) then continue end
		end

		local pos, onScreen = Camera:WorldToViewportPoint(aimPart.Position)
		if not onScreen then
			if not (_G.AntiDropOff or IsBindDown(Binds.AntiDrop)) then continue end
			local offDist = (Vector2.new(pos.X, pos.Y) - center).Magnitude * 0.5
			if offDist < best then
				best = offDist
				closest = plr
			end
			continue
		end

		local dist = (Vector2.new(pos.X, pos.Y) - center).Magnitude
		if dist <= _G.AimFOV and dist < best then
			best = dist
			closest = plr
		end
	end

	local wantAntiDrop = _G.AntiDropOff or IsBindDown(Binds.AntiDrop)
	if closest then
		lastTargetInfo.plr = closest
		lastTargetInfo.lastSeen = os.clock()
	elseif wantAntiDrop and lastTargetInfo.plr then
		local elapsed = os.clock() - lastTargetInfo.lastSeen
		if elapsed < _G.DropOffTimeout then
			local char = lastTargetInfo.plr.Character
			local hum = char and char:FindFirstChildOfClass("Humanoid")
			if char and hum and hum.Health > 0 then
				return lastTargetInfo.plr
			end
		end
	end

	return closest
end

local SilentTarget, SilentAimPos = nil, nil
local originalCameraType = Camera.CameraType

local protect = newcclosure or function(f) return f end
local canHook, prev = hookmetamethod ~= nil, nil

-- SILENT AIM ENGINE
if canHook then
	local okSet = pcall(function()
		prev = hookmetamethod(game, "__index", protect(function(self, key)
			if self == Camera and key == "CFrame" and _G.SilentAim and SilentTarget and SilentAimPos then
				local real = prev(self, key)
				return CFrame.lookAt(real.Position, SilentAimPos)
			end
			return prev(self, key)
		end))
	end)
	if not okSet or not prev then
		canHook = false
	end
end

local InstantHitRemotes = {
	"RemoteEvent", "HitEvent", "DamageEvent", "BulletHit", "ProjectileHit",
	"WeaponHit", "MeleeHit", "RemoteFunction", "HitRemote", "FireEvent"
}

local function FireInstantHit(target)
	if not target or not target.Character then return end
	local tool = LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass("Tool")
	if tool then
		for _, name in ipairs(InstantHitRemotes) do
			local ev = tool:FindFirstChild(name, true)
			if ev and (ev:IsA("RemoteEvent") or ev:IsA("RemoteFunction")) then
				pcall(function()
					if ev:IsA("RemoteEvent") then
						ev:FireServer(target.Character, target.Character:FindFirstChild("HumanoidRootPart"))
					else
						ev:InvokeServer(target.Character, target.Character:FindFirstChild("HumanoidRootPart"))
					end
				end)
			end
		end
	end
end

-- AIM LOOP
local lastRageFire = 0
local spinAngle = 0

RunService:BindToRenderStep("NuclearAim", Enum.RenderPriority.Camera.Value + 5, function()
	if unloaded then return end
	local center = ScreenCenter()

	local wantSilent = _G.SilentAim or IsBindDown(Binds.Silent)
	local wantSpin   = _G.Spinbot or IsBindDown(Binds.Spin)
	local wantPred   = _G.Prediction or IsBindDown(Binds.Pred)

	local target = GetClosest(center)

	local aimPos = nil
	if target and target.Character then
		local aimPart = GetAimPart(target.Character)
		if aimPart then
			aimPos = aimPart.Position
			if wantPred then
				aimPos = aimPos + (aimPart.AssemblyLinearVelocity * 0.14)
			end
		end
	end

	if aimPos and wantSilent then
		SilentTarget = target
		SilentAimPos = aimPos
		pcall(function()
			if not canHook then
				local real = Camera.CFrame
				Camera.CFrame = CFrame.lookAt(real.Position, aimPos)
			end
		end)
	else
		SilentTarget, SilentAimPos = nil, nil
	end

	-- SPINBOT
	if wantSpin then
		local char = LocalPlayer.Character
		local hrp = char and char:FindFirstChild("HumanoidRootPart")
		if hrp then
			local hum = char:FindFirstChildOfClass("Humanoid")
			if hum then hum.AutoRotate = false end
			spinAngle = (spinAngle + 14) % 360
			local pos = hrp.Position
			char:PivotTo(CFrame.new(pos) * CFrame.Angles(0, math.rad(spinAngle), 0))
		end
	elseif LocalPlayer.Character then
		local hum = LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
		if hum and not hum.AutoRotate then hum.AutoRotate = true end
	end

	-- Rage Bot
	local wantRage = _G.RageBot or IsBindDown(Binds.RageBot)
	local wantInstant = _G.InstantHit or IsBindDown(Binds.InstantHit)
	if wantRage and aimPos and target then
		local now = os.clock()
		if now - lastRageFire >= _G.RageFireRate then
			if math.random(1, 100) <= _G.HitChance then
				pcall(function() mouse1click() end)
				if wantInstant then
					FireInstantHit(target)
				end
			end
			lastRageFire = now
		end
	end
end)

-- Triggerbot
local lastClick = 0
RunService.Heartbeat:Connect(function()
	if unloaded then return end
	local wantTrigger = _G.Triggerbot or IsBindDown(Binds.Trigger)
	if not wantTrigger then return end

	local wantRage = _G.RageBot or IsBindDown(Binds.RageBot)
	if wantRage then return end

	local now = os.clock()
	if now - lastClick < 0.06 then return end
	local center = ScreenCenter()
	local t = GetClosest(center)
	if t and t.Character then
		local aimPart = GetAimPart(t.Character)
		local pos, on = nil, false
		if aimPart then
			pos, on = Camera:WorldToViewportPoint(aimPart.Position)
		end
		if on and (Vector2.new(pos.X, pos.Y) - center).Magnitude < 24 then
			if math.random(1, 100) <= _G.HitChance then
				pcall(function() mouse1click() end)
				if (_G.InstantHit or IsBindDown(Binds.InstantHit)) then
					FireInstantHit(t)
				end
			end
			lastClick = now
		end
	end
end)

-- NOCLIP
RunService.Stepped:Connect(function()
	if _G.Noclip and LocalPlayer.Character then
		for _, p in ipairs(LocalPlayer.Character:GetDescendants()) do
			if p:IsA("BasePart") then p.CanCollide = false end
		end
	end
end)

-- HITBOX
local HitboxScale = 1.25
local baseSizes = {}
local BodyPartNames = {
	["Head"] = true, ["Torso"] = true, ["UpperTorso"] = true, ["LowerTorso"] = true,
	["Left Arm"] = true, ["Right Arm"] = true, ["Left Leg"] = true, ["Right Leg"] = true,
	["LeftHand"] = true, ["RightHand"] = true, ["LeftFoot"] = true, ["RightFoot"] = true,
	["LeftLowerArm"] = true, ["RightLowerArm"] = true, ["LeftUpperArm"] = true, ["RightUpperArm"] = true,
	["LeftLowerLeg"] = true, ["RightLowerLeg"] = true, ["LeftUpperLeg"] = true, ["RightUpperLeg"] = true
}

RunService.Stepped:Connect(function()
	local wantHitbox = _G.HitboxExpander or IsBindDown(Binds.Hitbox)
	if wantHitbox then
		for _, plr in ipairs(Players:GetPlayers()) do
			if plr == LocalPlayer then continue end
			if _G.TeamCheck and plr.Team and plr.Team == LocalPlayer.Team then continue end
			local char = plr.Character
			if not char then continue end
			local tbl = baseSizes[plr]
			if not tbl then
				tbl = {}
				for _, part in ipairs(char:GetDescendants()) do
					if part:IsA("BasePart") and BodyPartNames[part.Name] then
						tbl[part] = part.Size
					end
				end
				baseSizes[plr] = tbl
			end
			for part, base in pairs(tbl) do
				if part.Parent then
					part.Size = base * HitboxScale
				else
					tbl[part] = nil
				end
			end
		end
	else
		for p, tbl in pairs(baseSizes) do
			for part, base in pairs(tbl) do
				if part.Parent then part.Size = base end
			end
		end
		baseSizes = {}
	end
end)

-- ESP (super far rendering, rainbow chams)
local espItems, highlights = {}, {}

local function makeESP()
	if not Drawing then return nil end
	local o = {}
	o.box = Drawing.new("Square")
	o.box.Thickness = 1.5
	o.box.Visible = false
	o.name = Drawing.new("Text")
	o.name.Size = 13
	o.name.Center = true
	o.name.Outline = true
	o.name.OutlineColor = Color3.new(0, 0, 0)
	o.name.Visible = false
	o.dist = Drawing.new("Text")
	o.dist.Size = 11
	o.dist.Center = true
	o.dist.Outline = true
	o.dist.OutlineColor = Color3.new(0, 0, 0)
	o.dist.Visible = false
	o.hp = Drawing.new("Line")
	o.hp.Thickness = 3
	o.hp.Visible = false
	o.hpbg = Drawing.new("Line")
	o.hpbg.Thickness = 5
	o.hpbg.Color = Color3.new(0, 0, 0)
	o.hpbg.Visible = false
	o.hpcap = Drawing.new("Line")
	o.hpcap.Thickness = 1
	o.hpcap.Color = Color3.new(1, 1, 1)
	o.hpcap.Visible = false
	o.tracer = Drawing.new("Line")
	o.tracer.Thickness = 1
	o.tracer.Visible = false
	return o
end

local function hideESP(p)
	local o = espItems[p]
	if o then
		o.box.Visible = false
		o.name.Visible = false
		o.dist.Visible = false
		o.hp.Visible = false
		o.hpbg.Visible = false
		o.hpcap.Visible = false
		o.tracer.Visible = false
	end
end

local function SafeDestroy(h)
	if h then pcall(function() if h.Parent then h:Destroy() end end) end
end

Players.PlayerRemoving:Connect(function(plr)
	local o = espItems[plr]
	if o then
		pcall(function()
			o.box:Remove() o.name:Remove() o.dist:Remove()
			o.hp:Remove() o.hpbg:Remove() o.hpcap:Remove() o.tracer:Remove()
		end)
		espItems[plr] = nil
	end
	if highlights[plr] then
		SafeDestroy(highlights[plr])
		highlights[plr] = nil
	end
end)

local function IsESPOn()
	return _G.ESP_Box or _G.ESP_Highlight or _G.ESP_Names or _G.ESP_Health or _G.ESP_Distance or _G.ESP_Tracer
end

local chamHue = 0
RunService.RenderStepped:Connect(function()
	chamHue = (chamHue + 0.004) % 1
end)

RunService.RenderStepped:Connect(function()
	if unloaded then return end
	local center = ScreenCenter()
	if not IsESPOn() then
		for p in pairs(espItems) do hideESP(p) end
		for p, h in pairs(highlights) do SafeDestroy(h) highlights[p] = nil end
		return
	end

	local camPos = Camera.CFrame.Position

	for _, plr in ipairs(Players:GetPlayers()) do
		if plr == LocalPlayer then continue end
		local char = plr.Character
		local root = char and char:FindFirstChild("HumanoidRootPart")
		local hum = char and char:FindFirstChildOfClass("Humanoid")
		if not root or not hum or hum.Health <= 0 then hideESP(plr) continue end
		if _G.TeamCheck and plr.Team and plr.Team == LocalPlayer.Team then hideESP(plr) continue end

		-- SUPER FAR: render up to ESP_MaxDistance (default 5000 studs)
		local worldDist = (root.Position - camPos).Magnitude
		if worldDist > _G.ESP_MaxDistance then hideESP(plr) continue end

		if _G.ESP_Highlight then
			local h = highlights[plr]
			local alive = h and pcall(function() return h.Parent == char end)
			local chamColor = _G.RainbowChams and Color3.fromHSV(chamHue, 1, 1) or Theme.Accent
			if not alive then
				SafeDestroy(h)
				h = Instance.new("Highlight")
				h.FillColor = chamColor
				h.FillTransparency = 0.35
				h.OutlineColor = Color3.new(1, 1, 1)
				h.OutlineTransparency = 0
				h.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
				h.Parent = char
				highlights[plr] = h
			elseif _G.RainbowChams then
				h.FillColor = chamColor
			end
		else
			if highlights[plr] then SafeDestroy(highlights[plr]) highlights[plr] = nil end
		end

		if not UseDrawing then continue end
		local o = espItems[plr]
		if not o then o = makeESP() if not o then continue end espItems[plr] = o end

		local p3 = Camera:WorldToViewportPoint(root.Position)
		if p3.Z < 0 then hideESP(plr) continue end

		local bottom = Camera:WorldToViewportPoint(root.Position - Vector3.new(0, 2, 0))
		local top = Camera:WorldToViewportPoint(root.Position + Vector3.new(0, 2.5, 0))
		local topY, bottomY = top.Y, bottom.Y
		local boxHgt = bottomY - topY
		local boxWid = boxHgt * 0.62
		local c2 = Vector2.new(p3.X, (topY + bottomY) / 2)

		if _G.ESP_Box then
			o.box.Color = Theme.Accent
			o.box.Position = Vector2.new(c2.X - boxWid/2, topY)
			o.box.Size = Vector2.new(boxWid, boxHgt)
			o.box.Visible = true
		else o.box.Visible = false end

		if _G.ESP_Tracer then
			o.tracer.Color = Theme.Accent
			o.tracer.From = center
			o.tracer.To = Vector2.new(c2.X, bottomY)
			o.tracer.Visible = true
		else o.tracer.Visible = false end

		if _G.ESP_Names then
			o.name.Text = plr.Name
			o.name.Color = Theme.Text
			o.name.Position = Vector2.new(c2.X, topY - 16)
			o.name.Visible = true
		else o.name.Visible = false end

		if _G.ESP_Distance then
			o.dist.Text = math.floor(worldDist) .. " studs"
			o.dist.Color = Color3.fromRGB(200, 230, 210)
			o.dist.Position = Vector2.new(c2.X, bottomY + 2)
			o.dist.Visible = true
		else o.dist.Visible = false end

		if _G.ESP_Health then
			local hpRatio = math.clamp(hum.Health / math.max(hum.MaxHealth, 1), 0, 1)
			local barX = c2.X - boxWid/2 - 6
			o.hpbg.From = Vector2.new(barX, topY)
			o.hpbg.To = Vector2.new(barX, bottomY)
			o.hpbg.Visible = true
			o.hp.Color = Color3.fromRGB(255*(1-hpRatio), 255*hpRatio, 60)
			o.hp.From = Vector2.new(barX, bottomY - ((bottomY-topY)*hpRatio))
			o.hp.To = Vector2.new(barX, bottomY)
			o.hp.Visible = true
			o.hpcap.From = Vector2.new(barX-2, topY)
			o.hpcap.To = Vector2.new(barX+2, topY)
			o.hpcap.Visible = true
		else
			o.hp.Visible = false
			o.hpbg.Visible = false
			o.hpcap.Visible = false
		end
	end
end)

-- Key System (opens after loading animation completes)
KeyBtn.MouseButton1Click:Connect(function()
	if CheckKey(KeyBox.Text) then
		KeyGui:Destroy()
		OpenMenu()
	else
		KeyBox.Text = ""
		KeyBox.PlaceholderText = "Wrong Key"
	end
end)

-- ============ UNLOAD ============
MakeBtn(Settings, "UNLOAD CHEAT", function()
	unloaded = true
	CloseMenu()
	for _, k in ipairs({ "SilentAim", "Triggerbot", "Spinbot", "HitboxExpander",
		"Prediction", "AntiDropOff", "InstantHit", "RageBot", "ShowFOV", "Noclip",
		"LootESP", "InvLookHUD", "LagSwitch", "Watermark", "ForceThird",
		"RainbowOutline", "RainbowChams", "NoRecoil" }) do
		_G[k] = false
	end
	StopLagSpam()
	StopNoRecoil()
	pcall(function()
		Camera.CameraType = originalCameraType
		LocalPlayer.CameraMode = Enum.CameraMode.Classic
		LocalPlayer.CameraMaxZoomDistance = 128
		LocalPlayer.CameraMinZoomDistance = 0.5
	end)
	pcall(function()
		local char = LocalPlayer.Character
		if char then
			local hum = char:FindFirstChildOfClass("Humanoid")
			if hum then
				hum.CameraOffset = Vector3.new(0, 0, 0)
				hum.AutoRotate = true
			end
		end
	end)
	pcall(CleanupContainerDrawings)
	if Watermark then pcall(function() Watermark:Remove() end) end
	if FOVCircle then pcall(function() FOVCircle:Remove() end) end
	for p in pairs(espItems) do
		pcall(function()
			local o = espItems[p]
			o.box:Remove() o.name:Remove() o.dist:Remove()
			o.hp:Remove() o.hpbg:Remove() o.hpcap:Remove() o.tracer:Remove()
		end)
	end
	for _, h in pairs(highlights) do SafeDestroy(h) end
	pcall(function() RunService:UnbindFromRenderStep("NuclearAim") end)
	pcall(function() invLookConn:Disconnect() end)
	CloseAllPopups()
	pcall(function() ScreenGui:Destroy() end)
	pcall(function() HudGui:Destroy() end)
	pcall(function() InvGui:Destroy() end)
	pcall(function() KeyGui:Destroy() end)
	print("[Nuclear.Hook] DEV v1.3 unloaded. Rejoin or re-execute to use again.")
end)

-- Input Handling
UserInputService.InputBegan:Connect(function(inp, gp)
	if unloaded then return end
	if bindWaiting then
		if inp.UserInputType == Enum.UserInputType.Keyboard then
			Binds[bindWaiting] = inp.KeyCode
			RefreshBindButtons()
			bindWaiting = nil
			return
		elseif inp.UserInputType == Enum.UserInputType.MouseButton1
			or inp.UserInputType == Enum.UserInputType.MouseButton2
			or inp.UserInputType == Enum.UserInputType.MouseButton3
			or inp.UserInputType == Enum.UserInputType.MouseButton4 then
			Binds[bindWaiting] = inp.UserInputType
			RefreshBindButtons()
			bindWaiting = nil
			return
		end
		return
	end

	if gp then return end

	if inp.KeyCode == Enum.KeyCode.RightShift or inp.KeyCode == Enum.KeyCode.RightAlt then
		if menuOpen then
			CloseMenu()
		else
			if not KeyGui or not KeyGui.Parent then
				OpenMenu()
			end
		end
	end
end)

print("[Nuclear.Hook] v1.3 DEV loaded | made by SILENT | Project Delta exclusive | No Recoil | Server Lag Switch | Rainbow Chams | Super-Far ESP | Inv Checker window | Loading animation + key system")
