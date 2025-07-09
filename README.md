-- Xoá GUI & Blur nếu có
pcall(function() game.CoreGui:FindFirstChild("MeMaybeoKeyUI"):Destroy() end)
pcall(function() game.Lighting:FindFirstChild("MeMaybeoBlur"):Destroy() end)

local cg = game:GetService("CoreGui")
local Lighting = game:GetService("Lighting")

-- Blur nền
local blur = Instance.new("BlurEffect", Lighting)
blur.Name = "MeMaybeoBlur"
blur.Size = 10

-- GUI
local gui = Instance.new("ScreenGui", cg)
gui.Name = "MeMaybeoKeyUI"
gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
gui.ResetOnSpawn = false

-- Khung chính
local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 460, 0, 260)
main.Position = UDim2.new(0.5, -230, 0.5, -130)
main.BackgroundColor3 = Color3.fromRGB(240, 240, 255) -- Nền trắng nhạt
main.BackgroundTransparency = 0
main.BorderSizePixel = 0
Instance.new("UICorner", main).CornerRadius = UDim.new(0, 8)

-- Logo
local logo = Instance.new("ImageLabel", main)
logo.Image = "rbxassetid://9387351497"
logo.Size = UDim2.new(0, 32, 0, 32)
logo.Position = UDim2.new(0, 20, 0, 10)
logo.BackgroundTransparency = 1

-- Tiêu đề
local title = Instance.new("TextLabel", main)
title.Text = "MeMaybeo Hub Key System"
title.Size = UDim2.new(1, -120, 0, 32)
title.Position = UDim2.new(0, 60, 0, 10)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(40, 40, 80)
title.Font = Enum.Font.GothamBold
title.TextSize = 20
title.TextXAlignment = Enum.TextXAlignment.Left

-- Subtitle
local subtitle = Instance.new("TextLabel", main)
subtitle.Text = "Get Key (Linkvertise ONLY IN DISCORD)"
subtitle.Size = UDim2.new(1, -40, 0, 25)
subtitle.Position = UDim2.new(0, 20, 0, 50)
subtitle.BackgroundTransparency = 1
subtitle.TextColor3 = Color3.fromRGB(90, 90, 120)
subtitle.Font = Enum.Font.Gotham
subtitle.TextSize = 15
subtitle.TextXAlignment = Enum.TextXAlignment.Left

-- Nhập key
local input = Instance.new("TextBox", main)
input.Size = UDim2.new(1, -40, 0, 40)
input.Position = UDim2.new(0, 20, 0, 90)
input.PlaceholderText = "Enter your key..."
input.Text = ""
input.Font = Enum.Font.Gotham
input.TextSize = 16
input.TextColor3 = Color3.new(0, 0, 0)
input.PlaceholderColor3 = Color3.fromRGB(150, 150, 150)
input.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Instance.new("UICorner", input).CornerRadius = UDim.new(0, 6)

-- Nút check key
local checkBtn = Instance.new("TextButton", main)
checkBtn.Size = UDim2.new(1, -40, 0, 35)
checkBtn.Position = UDim2.new(0, 20, 0, 140)
checkBtn.Text = "Check Key"
checkBtn.Font = Enum.Font.GothamBold
checkBtn.TextSize = 16
checkBtn.TextColor3 = Color3.new(1, 1, 1)
checkBtn.BackgroundColor3 = Color3.fromRGB(100, 100, 200)
Instance.new("UICorner", checkBtn).CornerRadius = UDim.new(0, 6)

-- Xử lý nhập key
checkBtn.MouseButton1Click:Connect(function()
	if input.Text == "Dr123" then
		checkBtn.Text = "✅ Correct! Loading..."

		-- Thông báo thành công
		local notify = Instance.new("Frame", gui)
		notify.Size = UDim2.new(0, 300, 0, 50)
		notify.Position = UDim2.new(0.5, -150, 1, -60)
		notify.BackgroundColor3 = Color3.fromRGB(30, 255, 120)
		notify.BackgroundTransparency = 0.15
		Instance.new("UICorner", notify).CornerRadius = UDim.new(0, 8)

		local icon = Instance.new("ImageLabel", notify)
		icon.Image = "rbxassetid://87017226532045"
		icon.Size = UDim2.new(0, 32, 0, 32)
		icon.Position = UDim2.new(0, 10, 0.5, -16)
		icon.BackgroundTransparency = 1

		local label = Instance.new("TextLabel", notify)
		label.Text = "Executed Successfully!"
		label.Size = UDim2.new(1, -50, 1, 0)
		label.Position = UDim2.new(0, 50, 0, 0)
		label.TextColor3 = Color3.new(1, 1, 1)
		label.Font = Enum.Font.GothamBold
		label.TextSize = 16
		label.BackgroundTransparency = 1
		label.TextXAlignment = Enum.TextXAlignment.Left

		task.delay(3, function()
			notify:Destroy()
			gui:Destroy()
			blur:Destroy()

			-- Chạy script chính
			loadstring(game:HttpGet("https://raw.githubusercontent.com/cac02j1/Script/main/README.md"))()
		end)
	else
		checkBtn.Text = "❌ Wrong Key!"
		wait(1.2)
		checkBtn.Text = "Check Key"
	end
end)
