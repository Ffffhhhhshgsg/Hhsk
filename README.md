local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/5gm/scripts/main/OrionUI.lua"))()
local Window = OrionLib:MakeWindow({
	Name = "🌀 سكربت نو كليب - يـولـيـوس",
	HidePremium = false,
	SaveConfig = true,
	ConfigFolder = "YuliusNoclip"
})

-- رسالة ترحيب
OrionLib:MakeNotification({
	Name = "نو كليب مفعل!",
	Content = "منور 😎 سكربت نو كليب - يوليوس",
	Image = "rbxassetid://4483345998",
	Time = 5
})

local Noclip = false
local Stepped

Window:MakeTab({
	Name = "المميزات",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
}):AddButton({
	Name = "تشغيل / إيقاف النوكليب",
	Callback = function()
		Noclip = not Noclip
		if Noclip then
			Stepped = game:GetService("RunService").Stepped:Connect(function()
				pcall(function()
					game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
				end)
			end)
		else
			if Stepped then Stepped:Disconnect() end
		end
	end    
})
