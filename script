local HttpService = game:GetService("HttpService")
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0, 400, 0, 300)
Frame.Position = UDim2.new(0.5, 0, 0.5, 0)
Frame.AnchorPoint = Vector2.new(0.5, 0.5)
Frame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
Frame.BorderSizePixel = 0
Frame.Active = true
Frame.Draggable = true
Frame.Parent = ScreenGui

local FrameCorner = Instance.new("UICorner")
FrameCorner.CornerRadius = UDim.new(0, 10)
FrameCorner.Parent = Frame

local Close = Instance.new("TextButton")
Close.Size = UDim2.new(0, 40, 0, 40)
Close.Position = UDim2.new(1, -40, 0, 0)
Close.BackgroundTransparency = 1
Close.Text = "×"
Close.TextScaled = true
Close.TextColor3 = Color3.fromRGB(150, 150, 150)
Close.Parent = Frame
Close.MouseButton1Click:Connect(function()
   ScreenGui:Destroy()
end)

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0, 30)
Title.Position = UDim2.new(0, 0, 0.05, 0)
Title.Text = "Key System"
Title.TextSize = 18
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.BackgroundTransparency = 1
Title.Parent = Frame

local Instructions = Instance.new("TextLabel")
Instructions.Size = UDim2.new(1, 0, 0, 30)
Instructions.Position = UDim2.new(0, 0, 0.2, 0)
Instructions.Text = "Enter Key To Access The Script"
Instructions.TextSize = 13
Instructions.TextColor3 = Color3.fromRGB(150, 150, 150)
Instructions.BackgroundTransparency = 1
Instructions.Parent = Frame

-- TextBox to display the entered key
local TextBox = Instance.new("TextBox")
TextBox.Size = UDim2.new(0.8, 0, 0.2, 0)
TextBox.Position = UDim2.new(0.1, 0, 0.4, 0)
TextBox.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
TextBox.PlaceholderText = "Enter Key..."
TextBox.Text = ""
TextBox.TextSize = 18
TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
TextBox.Parent = Frame

local TextBoxCorner = Instance.new("UICorner")
TextBoxCorner.CornerRadius = UDim.new(0, 5)
TextBoxCorner.Parent = TextBox

-- CheckKey button to validate the key
local CheckKey = Instance.new("TextButton")
CheckKey.Size = UDim2.new(0.35, 0, 0.15, 0)
CheckKey.Position = UDim2.new(0.55, 0, 0.7, 0)
CheckKey.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
CheckKey.Text = "Check Key"
CheckKey.TextSize = 18
CheckKey.TextColor3 = Color3.fromRGB(150, 150, 150)
CheckKey.Parent = Frame

local CheckKeyCorner = Instance.new("UICorner")
CheckKeyCorner.CornerRadius = UDim.new(0, 5)
CheckKeyCorner.Parent = CheckKey

-- GetKey button to generate and display the encrypted key
local GetKey = Instance.new("TextButton")
GetKey.Size = UDim2.new(0.35, 0, 0.15, 0)
GetKey.Position = UDim2.new(0.1, 0, 0.7, 0)
GetKey.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
GetKey.Text = "Get Key"
GetKey.TextSize = 18
GetKey.TextColor3 = Color3.fromRGB(150, 150, 150)
GetKey.Parent = Frame

local GetKeyCorner = Instance.new("UICorner")
GetKeyCorner.CornerRadius = UDim.new(0, 5)
GetKeyCorner.Parent = GetKey

-- Function to encrypt the username by shifting each letter by 5
local function encryptUsername(username)
    local encrypted = ""
    username = username:lower()  -- Convert the username to lowercase

    for i = 1, #username do
        local letter = username:sub(i, i)
        local ascii = string.byte(letter)

        if ascii >= 97 and ascii <= 122 then  -- Check if it's a lowercase letter
            -- Shift the letter by 5 positions
            local newAscii = ascii + 5
            if newAscii > 122 then
                newAscii = newAscii - 26  -- Wrap around after 'z'
            end
            encrypted = encrypted .. string.char(newAscii)
        else
            encrypted = encrypted .. letter  -- Non-alphabetical characters remain unchanged
        end
    end

    return encrypted
end

-- Event handler to check the key when the button is clicked
CheckKey.MouseButton1Click:Connect(function()
    local enteredKey = TextBox.Text
    local player = game.Players.LocalPlayer
    local username = player.Name

    -- Encrypt the username to generate the key
    local generatedKey = encryptUsername(username)

    -- Validate the entered key by comparing it with the generated key
    if enteredKey == generatedKey then
        TextBox.PlaceholderText = "Correct Key!"
        TextBox.Text = ""
        wait(1)
        ScreenGui:Destroy()  -- Destroy the GUI after successful validation

           loadstring(game:HttpGet("https://raw.githubusercontent.com/CxssieDev/ZScriptHUB/refs/heads/main/Utility"))()

    else
        TextBox.PlaceholderText = "Incorrect Key!"
    end
end)

-- Event handler to generate and display the key when the "Get Key" button is clicked
GetKey.MouseButton1Click:Connect(function()
    -- Copy the link to clipboard
    local url = "https://zhubofficial.github.io/KeyGenerator/"
    setclipboard(url) 

    -- Display the URL in the TextBox
    TextBox.Text = url
    TextBox.PlaceholderText = "URL Copied! You can paste it now."
end)
