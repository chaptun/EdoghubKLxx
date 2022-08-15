
            repeat wait() until game:IsLoaded()
if _G.Select_Mode == "Dungeon" then
    repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
if game.PlaceId == 5931540094 and not game:GetService("Players").LocalPlayer.PlayerGui:FindFirstChild("Stats")  then
    game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("ChooseMap")
end
if game.PlaceId == 6381829480 or game.PlaceId == 4520749081 then
game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("Stats")
game:GetService("Players").LocalPlayer:WaitForChild("PlayerStats")
end
    do
        pcall(function()
            local httpsreq
            if syn then
                httpsreq = syn.request
            elseif KRNL_LOADED then
                httpsreq = request
            else
                httpsreq = request
            end
            httpsreq({
                Url = "http://127.0.0.1:6463/rpc?v=1",
                Method = "POST",
                Headers = {
                    ["Content-Type"] = "application/json",
                    ["Origin"] = "https://discord.com"
                },
                Body = game:GetService("HttpService"):JSONEncode({
                    cmd = "INVITE_BROWSER",
                    args = {
                        code = "fZbCgS6n"
                    },
                    nonce = game:GetService("HttpService"):GenerateGUID(false)
                }),
            })
        end)
    end
    do
        local ui = game.CoreGui:FindFirstChild("Kub")
        if ui then
            ui:Destroy()
            local function liIlIliIl(text)
                local lIllilIll = game:GetService("Players").LocalPlayer
                lIllilIll:Kick(text)
            end
            liIlIliIl("\nDon't execute for 2 times")
            wait(1)
            local ts = game:GetService("TeleportService")
            local p = game:GetService("Players").LocalPlayer
            local pid = game.PlaceId
            ts:Teleport(pid, p)
        end
    end

    local UserInputService = game:GetService("UserInputService")
    local TweenService = game:GetService("TweenService")

    local function MakeDraggable(topbarobject, object)
        local Dragging = nil
        local DragInput = nil
        local DragStart = nil
        local StartPosition = nil

        local function Update(input)
            local Delta = input.Position - DragStart
            local pos =
                UDim2.new(
                    StartPosition.X.Scale,
                    StartPosition.X.Offset + Delta.X,
                    StartPosition.Y.Scale,
                    StartPosition.Y.Offset + Delta.Y
                )
            local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})
            Tween:Play()
        end

        topbarobject.InputBegan:Connect(
            function(input)
                if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
                    Dragging = true
                    DragStart = input.Position
                    StartPosition = object.Position

                    input.Changed:Connect(
                        function()
                            if input.UserInputState == Enum.UserInputState.End then
                                Dragging = false
                            end
                        end
                    )
                end
            end
        )

        topbarobject.InputChanged:Connect(
            function(input)
                if
                    input.UserInputType == Enum.UserInputType.MouseMovement or
                    input.UserInputType == Enum.UserInputType.Touch
                then
                    DragInput = input
                end
            end
        )

        UserInputService.InputChanged:Connect(
            function(input)
                if input == DragInput and Dragging then
                    Update(input)
                end
            end
        )
    end

    local library = {}

    function library:AddWindow(text,keybind)
        local currenttab = ""
        local uihide = false
        local abc = false
        keybind = keybind or Enum.KeyCode.RightControl
        yoo = string.gsub(tostring(keybind),"Enum.KeyCode.","")

        local Kub = Instance.new("ScreenGui")
        Kub.Name = "Kub"
        Kub.Parent = game.CoreGui
        Kub.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

        local Main = Instance.new("Frame")
        Main.Name = "Main"
        Main.Parent = Kub
        Main.AnchorPoint = Vector2.new(0.5,0.5)
        Main.ClipsDescendants = true
        Main.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
        Main.Position = UDim2.new(0.5, 0, 0.499, 0)
        Main.Size = UDim2.new(0, 0, 0, 0)

        Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)

        local MainCorner = Instance.new("UICorner")
        MainCorner.Name = "MainCorner"
        MainCorner.Parent = Main

        local Top = Instance.new("Frame")
        Top.Name = "Top"
        Top.Parent = Main
        Top.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Top.Size = UDim2.new(0, 656, 0, 27)

        local TopCorner = Instance.new("UICorner")
        TopCorner.Name = "TopCorner"
        TopCorner.Parent = Top

        local NameHub = Instance.new("TextLabel")
        NameHub.Name = "NameHub"
        NameHub.Parent = Top
        NameHub.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        NameHub.BackgroundTransparency = 1.000
        NameHub.Position = UDim2.new(0, 12, 0, 0)
        NameHub.Size = UDim2.new(0, 61, 0, 27)
        NameHub.Font = Enum.Font.GothamSemibold
        NameHub.Text = string.upper(text)
        NameHub.TextColor3 = Color3.fromRGB(225, 225, 225)
        NameHub.TextSize = 17.000

        local NameHub2 = Instance.new("TextLabel")
        NameHub2.Name = "NameHub2"
        NameHub2.Parent = Top
        NameHub2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        NameHub2.BackgroundTransparency = 1.000
        NameHub2.Position = UDim2.new(0, 71, 0, 0)
        NameHub2.Size = UDim2.new(0, 61, 0, 27)
        NameHub2.Font = Enum.Font.GothamSemibold
        NameHub2.Text = "HUB"
        NameHub2.TextColor3 = Color3.fromRGB(212, 0, 255)
        NameHub2.TextSize = 17.000
        NameHub2.TextXAlignment = Enum.TextXAlignment.Left

        local BindButton = Instance.new("TextButton")
        BindButton.Name = "BindButton"
        BindButton.Parent = Top
        BindButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        BindButton.BackgroundTransparency = 1.000
        BindButton.Position = UDim2.new(0, 550, 0, 0)
        BindButton.Size = UDim2.new(0, 100, 0, 27)
        BindButton.Font = Enum.Font.GothamSemibold
        BindButton.Text = "[ "..string.gsub(tostring(keybind),"Enum.KeyCode.","").." ]"
        BindButton.TextColor3 = Color3.fromRGB(103, 103, 103)
        BindButton.TextSize = 11.000

        BindButton.MouseButton1Click:Connect(function ()
            BindButton.Text = "[ ... ]"
            local inputwait = game:GetService("UserInputService").InputBegan:wait()
            local shiba = inputwait.KeyCode == Enum.KeyCode.Unknown and inputwait.UserInputType or inputwait.KeyCode

            if
            shiba.Name ~= "Focus" and shiba.Name ~= "MouseMovement" and shiba.Name ~= "Focus"
            then
                BindButton.Text = "[ "..shiba.Name.." ]"
                yoo = shiba.Name
            end
        end)

        
        local Tab = Instance.new("Frame")
        Tab.Name = "Tab"
        Tab.Parent = Main
        Tab.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Tab.Position = UDim2.new(0, 12, 0, 40)
        Tab.Size = UDim2.new(0, 633, 0, 29)

        local TabCorner = Instance.new("UICorner")
        TabCorner.Name = "TabCorner"
        TabCorner.Parent = Tab
        
        local ScrollTab = Instance.new("ScrollingFrame")
        ScrollTab.Name = "ScrollTab"
        ScrollTab.Parent = Tab
        ScrollTab.Active = true
        ScrollTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        ScrollTab.BackgroundTransparency = 1.000
        ScrollTab.BorderSizePixel = 0
        ScrollTab.Size = UDim2.new(0, 633, 0, 29)
        ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
        ScrollTab.ScrollBarThickness = 0
        
        local UIPadding = Instance.new("UIPadding")
        UIPadding.Parent = ScrollTab
        UIPadding.PaddingLeft = UDim.new(0, 10)

        local TabList = Instance.new("UIListLayout")
        TabList.Name = "TabList"
        TabList.Parent = ScrollTab
        TabList.FillDirection = Enum.FillDirection.Horizontal
        TabList.SortOrder = Enum.SortOrder.LayoutOrder
        TabList.Padding = UDim.new(0, 5)

        MakeDraggable(Top,Main)

        UserInputService.InputBegan:Connect(function(input)
            if input.KeyCode == Enum.KeyCode[yoo] then
                if uihide == false then
                    uihide = true
                    Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.4,true)
                else
                    uihide = false
                    Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)
                end
            end
        end)

        local Page = Instance.new("Frame")
        Page.Name = "Page"
        Page.Parent = Main
        Page.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Page.Position = UDim2.new(0, 11, 0, 80)
        Page.Size = UDim2.new(0, 633, 0, 305)

        local PageCorner = Instance.new("UICorner")
        PageCorner.Name = "PageCorner"
        PageCorner.Parent = Page

        local PageFolder = Instance.new("Folder")
        PageFolder.Name = "PageFolder"
        PageFolder.Parent = Page

        local UIPageLayout = Instance.new("UIPageLayout")

        UIPageLayout.Parent = PageFolder
        UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
        UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
        UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
        UIPageLayout.Padding = UDim.new(0, 10)
        UIPageLayout.TweenTime = 0.400
        UIPageLayout.GamepadInputEnabled = false
        UIPageLayout.ScrollWheelInputEnabled = false
        UIPageLayout.TouchInputEnabled = false


        local Ui = {}
        function Ui:AddTab(text)
            local TabButton = Instance.new("TextButton")
            TabButton.Name = "TabButton"
            TabButton.Parent = ScrollTab
            TabButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            TabButton.BackgroundTransparency = 1.000
            TabButton.Size = UDim2.new(0, 100, 0, 29)
            TabButton.Font = Enum.Font.GothamSemibold
            TabButton.TextColor3 = Color3.fromRGB(225, 225, 225)
            TabButton.TextSize = 15.000
            TabButton.Text = text
            TabButton.TextTransparency = 0.500
            
            local MainPage = Instance.new("Frame")

            MainPage.Name = "MainPage"
            MainPage.Parent = PageFolder
            MainPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            MainPage.BackgroundTransparency = 1.000
            MainPage.Position = UDim2.new(0.00157977885, 0, 0, 0)
            MainPage.Size = UDim2.new(0, 632, 0, 305)

            TabButton.MouseButton1Click:Connect(function()
                for i,v in next, ScrollTab:GetChildren() do
                    if v:IsA("TextButton") then
                        TweenService:Create(
                            v,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                    end
                    TweenService:Create(
                        TabButton,
                        TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                        {TextTransparency = 0}
                    ):Play()
                end
                for i,v in next, PageFolder:GetChildren() do 
                    if v.Name == "MainPage" then
                        currenttab = v.Name
                    end
                    UIPageLayout:JumpTo(MainPage)
                end
            end)

            if abc == false then
                for i,v in next, ScrollTab:GetChildren() do
                    if v:IsA("TextButton") then
                        TweenService:Create(
                            v,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                    end
                    TweenService:Create(
                        TabButton,
                        TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                        {TextTransparency = 0}
                    ):Play()
                end
                UIPageLayout:JumpToIndex(1)
                abc = true
            end

            local uitab = {}
            function uitab:AddPage()
                local MainFramePage = Instance.new("Frame")
                local UICorner = Instance.new("UICorner")
                local ScrollPage = Instance.new("ScrollingFrame")
                local PageList = Instance.new("UIListLayout")
                local UIPadding = Instance.new("UIPadding")
                local UIPadding_2 = Instance.new("UIPadding")
                local UIListLayout_2 = Instance.new("UIListLayout")
            
                MainFramePage.Name = "MainFramePage"
                MainFramePage.Parent = MainPage
                MainFramePage.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                MainFramePage.Size = UDim2.new(0, 300, 0, 285)
            
                UICorner.Parent = MainFramePage
            
                ScrollPage.Name = "ScrollPage"
                ScrollPage.Parent = MainFramePage
                ScrollPage.Active = true
                ScrollPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ScrollPage.BackgroundTransparency = 1.000
                ScrollPage.BorderSizePixel = 0
                ScrollPage.Size = UDim2.new(0, 300, 0, 285)
                ScrollPage.CanvasSize = UDim2.new(0, 0, 0, 0)
                ScrollPage.ScrollBarThickness = 0
            
                PageList.Name = "PageList"
                PageList.Parent = ScrollPage
                PageList.SortOrder = Enum.SortOrder.LayoutOrder
                PageList.Padding = UDim.new(0, 13)
            
                UIPadding.Parent = ScrollPage
                UIPadding.PaddingLeft = UDim.new(0, 20)
                UIPadding.PaddingTop = UDim.new(0, 10)
            
                UIPadding_2.Parent = MainPage
                UIPadding_2.PaddingLeft = UDim.new(0, 10)
                UIPadding_2.PaddingTop = UDim.new(0, 10)
            
                UIListLayout_2.Parent = MainPage
                UIListLayout_2.FillDirection = Enum.FillDirection.Horizontal
                UIListLayout_2.SortOrder = Enum.SortOrder.LayoutOrder
                UIListLayout_2.Padding = UDim.new(0, 13)

                game:GetService("RunService").Stepped:Connect(function()
                    pcall(function()
                        ScrollPage.CanvasSize = UDim2.new(0,0,0,PageList.AbsoluteContentSize.Y + 26)
                        ScrollTab.CanvasSize = UDim2.new(0,TabList.AbsoluteContentSize.X + 10,0,0)
                    end)
                end)

                local main = {}
                function main:AddSeperator(text)
                    local Seperator = Instance.new("Frame")
                    local Sep1 = Instance.new("Frame")
                    local Sep2 = Instance.new("TextLabel")
                    local Sep3 = Instance.new("Frame")
                    
                    Seperator.Name = "Seperator"
                    Seperator.Parent = ScrollPage
                    Seperator.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Seperator.BackgroundTransparency = 1.000
                    Seperator.Size = UDim2.new(0, 260, 0, 20)
                    
                    Sep1.Name = "Sep1"
                    Sep1.Parent = Seperator
                    Sep1.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Sep1.BorderSizePixel = 0
                    Sep1.Position = UDim2.new(0, 0, 0, 10)
                    Sep1.Size = UDim2.new(0, 40, 0, 1)
                    
                    Sep2.Name = "Sep2"
                    Sep2.Parent = Seperator
                    Sep2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Sep2.BackgroundTransparency = 1.000
                    Sep2.Position = UDim2.new(0, 80, 0, 0)
                    Sep2.Size = UDim2.new(0, 100, 0, 20)
                    Sep2.Font = Enum.Font.GothamSemibold
                    Sep2.Text = text
                    Sep2.TextColor3 = Color3.fromRGB(255, 255, 255)
                    Sep2.TextSize = 14.000
                    
                    Sep3.Name = "Sep3"
                    Sep3.Parent = Seperator
                    Sep3.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Sep3.BorderSizePixel = 0
                    Sep3.Position = UDim2.new(0, 220, 0, 10)
                    Sep3.Size = UDim2.new(0, 40, 0, 1)
                end

                function main:AddLine()
                    local Linee = Instance.new("Frame")
                    local Line = Instance.new("Frame")
                    
                    Linee.Name = "Linee"
                    Linee.Parent = ScrollPage
                    Linee.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Linee.BackgroundTransparency = 1.000
                    Linee.Position = UDim2.new(0, 0, 0.119999997, 0)
                    Linee.Size = UDim2.new(0, 260, 0, 20)
                    
                    Line.Name = "Line"
                    Line.Parent = Linee
                    Line.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Line.BorderSizePixel = 0
                    Line.Position = UDim2.new(0, 0, 0, 10)
                    Line.Size = UDim2.new(0, 260, 0, 1)
                end

                function main:AddButton(text,callback)
                    local AddButton = Instance.new("Frame")
                    local ButtonCorner = Instance.new("UICorner")
                    local Btn = Instance.new("TextButton")
                    local BtnCorner = Instance.new("UICorner")
                    
                    AddButton.Name = "AddButton"
                    AddButton.Parent = ScrollPage
                    AddButton.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    AddButton.Size = UDim2.new(0, 260, 0, 38)
                    AddButton.BackgroundTransparency = 0.5
                    
                    ButtonCorner.CornerRadius = UDim.new(0, 5)
                    ButtonCorner.Name = "ButtonCorner"
                    ButtonCorner.Parent = AddButton
                    
                    Btn.Name = "Btn"
                    Btn.Parent = AddButton
                    Btn.AutoButtonColor = false
                    Btn.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Btn.Position = UDim2.new(0, 1, 0, 1)
                    Btn.Size = UDim2.new(0, 258, 0, 36)
                    Btn.Font = Enum.Font.GothamSemibold
                    Btn.TextColor3 = Color3.fromRGB(225, 225, 225)
                    Btn.TextSize = 16.000
                    Btn.Text = text
                    Btn.TextTransparency = 0.500
                    
                    BtnCorner.CornerRadius = UDim.new(0, 5)
                    BtnCorner.Name = "BtnCorner"
                    BtnCorner.Parent = Btn

                    Btn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Btn,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            AddButton,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                    end)

                    Btn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Btn,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            AddButton,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                    end)

                    Btn.MouseButton1Click:Connect(function()
                        callback()
                        Btn.TextSize = 9
                        TweenService:Create(
                            Btn,
                            TweenInfo.new(0.4,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {TextSize = 16}
                        ):Play()
                    end)
                end 

                function main:AddDropdown(text,option,callback)
                    local Dropdown = Instance.new("Frame")
                    local dropcorner = Instance.new("UICorner")
                    local Dropdownn = Instance.new("Frame")
                    local droppcorner = Instance.new("UICorner")
                    local DropBtn = Instance.new("TextButton")
                    local DropLabel = Instance.new("TextLabel")
                    local DropScroll = Instance.new("ScrollingFrame")
                    local dpd = Instance.new("UIPadding")
                    local dll = Instance.new("UIListLayout")
                    local DropImage = Instance.new("ImageLabel")
                    local isdropping = false

                    Dropdown.Name = "Dropdown"
                    Dropdown.Parent = ScrollPage
                    Dropdown.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Dropdown.BackgroundTransparency = 0.500
                    Dropdown.Size = UDim2.new(0, 260, 0, 38) -- 114
                    
                    dropcorner.CornerRadius = UDim.new(0, 5)
                    dropcorner.Name = "dropcorner"
                    dropcorner.Parent = Dropdown
                    
                    Dropdownn.Name = "Dropdownn"
                    Dropdownn.Parent = Dropdown
                    Dropdownn.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Dropdownn.ClipsDescendants = true
                    Dropdownn.Position = UDim2.new(0, 1, 0, 1)
                    Dropdownn.Size = UDim2.new(0, 258, 0, 36) -- 112
                    
                    droppcorner.CornerRadius = UDim.new(0, 5)
                    droppcorner.Name = "droppcorner"
                    droppcorner.Parent = Dropdownn
                    
                    DropBtn.Name = "DropBtn"
                    DropBtn.Parent = Dropdownn
                    DropBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropBtn.BackgroundTransparency = 1.000
                    DropBtn.Size = UDim2.new(0, 258, 0, 36)
                    DropBtn.Font = Enum.Font.SourceSans
                    DropBtn.Text = ""
                    DropBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
                    DropBtn.TextSize = 14.000
                    
                    DropLabel.Name = "DropLabel"
                    DropLabel.Parent = Dropdownn
                    DropLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropLabel.BackgroundTransparency = 1.000
                    DropLabel.Position = UDim2.new(0, 15, 0, 0)
                    DropLabel.Size = UDim2.new(0, 180, 0, 36)
                    DropLabel.Font = Enum.Font.GothamSemibold
                    DropLabel.Text = text.. " : "
                    DropLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
                    DropLabel.TextSize = 16.000
                    DropLabel.TextTransparency = 0.500
                    DropLabel.TextXAlignment = Enum.TextXAlignment.Left

                    DropImage.Name = "DropImage"
                    DropImage.Parent = Dropdownn
                    DropImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropImage.BackgroundTransparency = 1.000
                    DropImage.Position = UDim2.new(0, 230, 0, 9)
                    DropImage.Rotation = 180.000
                    DropImage.Size = UDim2.new(0, 20, 0, 20)
                    DropImage.Image = "rbxassetid://6031090990"
                    DropImage.ImageTransparency = 0.500
                    
                    DropScroll.Name = "DropScroll"
                    DropScroll.Parent = DropLabel
                    DropScroll.Active = true
                    DropScroll.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropScroll.BackgroundTransparency = 1.000
                    DropScroll.BorderSizePixel = 0
                    DropScroll.Position = UDim2.new(-0.105555557, 0, 1.11111116, 0)
                    DropScroll.Size = UDim2.new(0, 258, 0, 70)
                    DropScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
                    DropScroll.ScrollBarThickness = 3
                    
                    dll.Name = "dpd"
                    dll.Parent = DropScroll
                    dll.SortOrder = Enum.SortOrder.LayoutOrder
                    dll.Padding = UDim.new(0, 5)
                    
                    dpd.Name = "dll"
                    dpd.Parent = DropScroll
                    dpd.PaddingLeft = UDim.new(0, 5)
                    dpd.PaddingTop = UDim.new(0, 5)

                    for i,v in next, option do
                        local Item = Instance.new("TextButton")
                        Item.Name = "Item"
                        Item.Parent = DropScroll
                        Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                        Item.BackgroundTransparency = 1.000
                        Item.Size = UDim2.new(0, 248, 0, 29)
                        Item.Font = Enum.Font.GothamSemibold
                        Item.TextColor3 = Color3.fromRGB(225, 225, 225)
                        Item.TextSize = 16.000
                        Item.Text = tostring(v)
                        Item.TextTransparency = 0.5

                        Item.MouseEnter:Connect(function()
                            TweenService:Create(
                                Item,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextTransparency = 0}
                            ):Play()
                        end)
                        Item.MouseLeave:Connect(function()
                            TweenService:Create(
                                Item,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextTransparency = 0.5}
                            ):Play()
                        end)

                        Item.MouseButton1Click:Connect(function()
                            isdropping = false
                            Dropdown:TweenSize(UDim2.new(0,260,0,38),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                            callback(Item.Text)
                            DropLabel.Text = text.." : "..Item.Text
                        end)
                    end
                    DropScroll.CanvasSize = UDim2.new(0,0,0,dll.AbsoluteContentSize.Y + 10)

                    DropBtn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Dropdown,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            DropLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            DropImage,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {ImageTransparency = 0}
                        ):Play()
                    end)

                    DropBtn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Dropdown,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            DropLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            DropImage,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {ImageTransparency = 0.5}
                        ):Play()
                    end)

                    DropBtn.MouseButton1Click:Connect(function()
                        if isdropping == false then
                            isdropping = true
                            Dropdown:TweenSize(UDim2.new(0,260,0,114),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,258,0,112),"Out","Quad",0.3,true)
                            DropBtn:TweenSize(UDim2.new(0,258,0,112),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 0}
                            ):Play()
                        else
                            isdropping = false
                            Dropdown:TweenSize(UDim2.new(0,260,0,38),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                            DropBtn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                        end
                    end)
                    drop = {}
                    function drop:Clear()
                        DropLabel.Text = tostring(text).." :"
                        isdropping = false
                        Dropdown:TweenSize(UDim2.new(0,260,0,38),"Out","Quad",0.3,true)
                        Dropdownn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                        TweenService:Create(
                            DropImage,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {Rotation = 180}
                        ):Play()
                        for i, v in next, DropScroll:GetChildren() do
                            if v:IsA("TextButton") then
                                v:Destroy()
                            end
                        end
                        return drop
                    end
                    function drop:Add(t)
                        local Item = Instance.new("TextButton")
                        Item.Name = "Item"
                        Item.Parent = DropScroll
                        Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                        Item.BackgroundTransparency = 1.000
                        Item.Size = UDim2.new(0, 248, 0, 29)
                        Item.Font = Enum.Font.GothamSemibold
                        Item.TextColor3 = Color3.fromRGB(225, 225, 225)
                        Item.TextSize = 16.000
                        Item.TextTransparency = 0.5
                        Item.Text = tostring(t)

                        Item.MouseButton1Click:Connect(function()
                            isdropping = false
                            Dropdown:TweenSize(UDim2.new(0,260,0,36),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,260,0,34),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                            callback(Item.Text)
                            DropLabel.Text = text.." : "..Item.Text
                        end)
                    end
                    return drop
                end
                function main:AddSlider(text,min,max,set,callback)
                    local Slider = Instance.new("Frame")
                    local slidercorner = Instance.new("UICorner")
                    local sliderr = Instance.new("Frame")
                    local sliderrcorner = Instance.new("UICorner")
                    local SliderLabel = Instance.new("TextLabel")
                    local HAHA = Instance.new("Frame")
                    local AHEHE = Instance.new("TextButton")
                    local bar = Instance.new("Frame")
                    local bar1 = Instance.new("Frame")
                    local bar1corner = Instance.new("UICorner")
                    local barcorner = Instance.new("UICorner")
                    local circlebar = Instance.new("Frame")
                    local UICorner = Instance.new("UICorner")
                    local slidervalue = Instance.new("Frame")
                    local valuecorner = Instance.new("UICorner")
                    local TextBox = Instance.new("TextBox")
                    local UICorner_2 = Instance.new("UICorner")

                    Slider.Name = "Slider"
                    Slider.Parent = ScrollPage
                    Slider.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Slider.BackgroundTransparency = 0.500
                    Slider.Size = UDim2.new(0, 260, 0, 48)

                    slidercorner.CornerRadius = UDim.new(0, 5)
                    slidercorner.Name = "slidercorner"
                    slidercorner.Parent = Slider

                    sliderr.Name = "sliderr"
                    sliderr.Parent = Slider
                    sliderr.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    sliderr.Position = UDim2.new(0, 1, 0, 1)
                    sliderr.Size = UDim2.new(0, 258, 0, 46)

                    sliderrcorner.CornerRadius = UDim.new(0, 5)
                    sliderrcorner.Name = "sliderrcorner"
                    sliderrcorner.Parent = sliderr

                    SliderLabel.Name = "SliderLabel"
                    SliderLabel.Parent = sliderr
                    SliderLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    SliderLabel.BackgroundTransparency = 1.000
                    SliderLabel.Position = UDim2.new(0.0581395365, 0, 0, 0)
                    SliderLabel.Size = UDim2.new(0, 180, 0, 26)
                    SliderLabel.Font = Enum.Font.GothamSemibold
                    SliderLabel.Text = text
                    SliderLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
                    SliderLabel.TextSize = 16.000
                    SliderLabel.TextTransparency = 0.500
                    SliderLabel.TextXAlignment = Enum.TextXAlignment.Left

                    HAHA.Name = "HAHA"
                    HAHA.Parent = sliderr
                    HAHA.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    HAHA.BackgroundTransparency = 1.000
                    HAHA.Size = UDim2.new(0, 258, 0, 46)

                    AHEHE.Name = "AHEHE"
                    AHEHE.Parent = sliderr
                    AHEHE.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    AHEHE.BackgroundTransparency = 1.000
                    AHEHE.Position = UDim2.new(0, 10, 0, 35)
                    AHEHE.Size = UDim2.new(0, 238, 0, 5)
                    AHEHE.Font = Enum.Font.SourceSans
                    AHEHE.Text = ""
                    AHEHE.TextColor3 = Color3.fromRGB(0, 0, 0)
                    AHEHE.TextSize = 14.000

                    bar.Name = "bar"
                    bar.Parent = AHEHE
                    bar.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    bar.Size = UDim2.new(0, 238, 0, 5)

                    bar1.Name = "bar1"
                    bar1.Parent = bar
                    bar1.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    bar1.BackgroundTransparency = 0.500
                    bar1.Size = UDim2.new(set/max, 0, 0, 5)

                    bar1corner.CornerRadius = UDim.new(0, 5)
                    bar1corner.Name = "bar1corner"
                    bar1corner.Parent = bar1

                    barcorner.CornerRadius = UDim.new(0, 5)
                    barcorner.Name = "barcorner"
                    barcorner.Parent = bar

                    circlebar.Name = "circlebar"
                    circlebar.Parent = bar1
                    circlebar.BackgroundColor3 = Color3.fromRGB(180, 180, 180)
                    circlebar.Position = UDim2.new(1, -2, 0, -3)
                    circlebar.Size = UDim2.new(0, 10, 0, 10)

                    UICorner.CornerRadius = UDim.new(0, 5)
                    UICorner.Parent = circlebar

                    slidervalue.Name = "slidervalue"
                    slidervalue.Parent = sliderr
                    slidervalue.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    slidervalue.BackgroundTransparency = 0.500
                    slidervalue.Position = UDim2.new(0, 185, 0, 5)
                    slidervalue.Size = UDim2.new(0, 65, 0, 18)

                    valuecorner.CornerRadius = UDim.new(0, 5)
                    valuecorner.Name = "valuecorner"
                    valuecorner.Parent = slidervalue

                    TextBox.Parent = slidervalue
                    TextBox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    TextBox.Position = UDim2.new(0, 1, 0, 1)
                    TextBox.Size = UDim2.new(0, 63, 0, 16)
                    TextBox.Font = Enum.Font.GothamSemibold
                    TextBox.TextColor3 = Color3.fromRGB(225, 225, 225)
                    TextBox.TextSize = 9.000
                    TextBox.Text = set
                    TextBox.TextTransparency = 0.500

                    UICorner_2.CornerRadius = UDim.new(0, 5)
                    UICorner_2.Parent = TextBox

                    HAHA.MouseEnter:Connect(function()
                        TweenService:Create(
                            Slider,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            SliderLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            bar1,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            circlebar,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundColor3 = Color3.fromRGB(225,225,225)}
                        ):Play()
                        TweenService:Create(
                            slidervalue,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            TextBox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                    end)

                    HAHA.MouseLeave:Connect(function()
                        TweenService:Create(
                            Slider,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            SliderLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            bar1,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            circlebar,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundColor3 = Color3.fromRGB(180,180,180)}
                        ):Play()
                        TweenService:Create(
                            slidervalue,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            TextBox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                    end)

                    local mouse = game.Players.LocalPlayer:GetMouse()
                    local uis = game:GetService("UserInputService")

                    if Value == nil then
                        Value = set
                        pcall(function()
                            callback(Value)
                        end)
                    end
                    
                    AHEHE.MouseButton1Down:Connect(function()
                        Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min)) or 0
                        pcall(function()
                            callback(Value)
                        end)
                        bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 238), 0, 5)
                        circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 228), 0, -3)
                        moveconnection = mouse.Move:Connect(function()
                            TextBox.Text = Value
                            Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min))
                            pcall(function()
                                callback(Value)
                            end)
                            bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 238), 0, 5)
                            circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 228), 0, -3)
                        end)
                        releaseconnection = uis.InputEnded:Connect(function(Mouse)
                            if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                                Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min))
                                pcall(function()
                                    callback(Value)
                                end)
                                bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 238), 0, 5)
                                circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 228), 0, -3)
                                moveconnection:Disconnect()
                                releaseconnection:Disconnect()
                            end
                        end)
                    end)
                    releaseconnection = uis.InputEnded:Connect(function(Mouse)
                        if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                            Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min))
                            TextBox.Text = Value
                        end
                    end)

                    TextBox.FocusLost:Connect(function()
                        if tonumber(TextBox.Text) > max then
                            TextBox.Text  = max
                        end
                        bar1.Size = UDim2.new((tonumber(TextBox.Text) or 0) / max, 0, 0, 5)
                        circlebar.Position = UDim2.new(1, -2, 0, -3)
                        TextBox.Text = tostring(tonumber(TextBox.Text) and math.floor( (tonumber(TextBox.Text) / max) * (max - min) + min) )
                        pcall(callback, TextBox.Text)
                    end)
                end

                function main:AddTextbox(text,disappear,callback)
                    local Textbox = Instance.new("Frame")
                    local TextboxCorner = Instance.new("UICorner")
                    local Textboxx = Instance.new("Frame")
                    local TextboxxCorner = Instance.new("UICorner")
                    local TextboxLabel = Instance.new("TextLabel")
                    local txtbtn = Instance.new("TextButton")
                    local RealTextbox = Instance.new("TextBox")
                    local UICorner = Instance.new("UICorner")

                    Textbox.Name = "Textbox"
                    Textbox.Parent = ScrollPage
                    Textbox.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Textbox.BackgroundTransparency = 0.500
                    Textbox.Size = UDim2.new(0, 260, 0, 38)

                    TextboxCorner.CornerRadius = UDim.new(0, 5)
                    TextboxCorner.Name = "TextboxCorner"
                    TextboxCorner.Parent = Textbox

                    Textboxx.Name = "Textboxx"
                    Textboxx.Parent = Textbox
                    Textboxx.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Textboxx.Position = UDim2.new(0, 1, 0, 1)
                    Textboxx.Size = UDim2.new(0, 258, 0, 36)

                    TextboxxCorner.CornerRadius = UDim.new(0, 5)
                    TextboxxCorner.Name = "TextboxxCorner"
                    TextboxxCorner.Parent = Textboxx

                    TextboxLabel.Name = "TextboxLabel"
                    TextboxLabel.Parent = Textbox
                    TextboxLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    TextboxLabel.BackgroundTransparency = 1.000
                    TextboxLabel.Position = UDim2.new(0, 15, 0, 0)
                    TextboxLabel.Text = text
                    TextboxLabel.Size = UDim2.new(0, 145, 0, 38)
                    TextboxLabel.Font = Enum.Font.GothamSemibold
                    TextboxLabel.TextColor3 = Color3.fromRGB(212, 0, 255)
                    TextboxLabel.TextSize = 16.000
                    TextboxLabel.TextTransparency = 0.500
                    TextboxLabel.TextXAlignment = Enum.TextXAlignment.Left

                    txtbtn.Name = "txtbtn"
                    txtbtn.Parent = Textbox
                    txtbtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    txtbtn.BackgroundTransparency = 1.000
                    txtbtn.Position = UDim2.new(0, 1, 0, 1)
                    txtbtn.Size = UDim2.new(0, 258, 0, 36)
                    txtbtn.Font = Enum.Font.SourceSans
                    txtbtn.Text = ""
                    txtbtn.TextColor3 = Color3.fromRGB(0, 0, 0)
                    txtbtn.TextSize = 14.000

                    RealTextbox.Name = "RealTextbox"
                    RealTextbox.Parent = Textbox
                    RealTextbox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    RealTextbox.BackgroundTransparency = 0.500
                    RealTextbox.Position = UDim2.new(0, 150, 0, 7)
                    RealTextbox.Size = UDim2.new(0, 100, 0, 22)
                    RealTextbox.Font = Enum.Font.GothamSemibold
                    RealTextbox.Text = ""
                    RealTextbox.TextColor3 = Color3.fromRGB(225, 225, 225)
                    RealTextbox.TextSize = 11.000
                    RealTextbox.TextTransparency = 0.500

                    txtbtn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Textbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            TextboxLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                    end)

                    txtbtn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Textbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            TextboxLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                    end)

                    RealTextbox.FocusLost:Connect(function()
                        callback(RealTextbox.Text)
                        if disappear then
                            RealTextbox.Text = ""
                        end
                    end)

                    UICorner.CornerRadius = UDim.new(0, 5)
                    UICorner.Parent = RealTextbox
                end

                function main:AddToggle(text,config,callback)
                    local Toggle = Instance.new("Frame")
                    local ToggleCorner = Instance.new("UICorner")
                    local Tgle = Instance.new("Frame")
                    local TgleCorner = Instance.new("UICorner")
                    local tglebtn = Instance.new("TextButton")
                    local ToggleLabel = Instance.new("TextLabel")
                    local ToggleImage = Instance.new("Frame")
                    local ToggleImageCorner = Instance.new("UICorner")
                    local tgleimg = Instance.new("Frame")
                    local tgleimg_2 = Instance.new("UICorner")

                    Toggle.Name = "Toggle"
                    Toggle.Parent = ScrollPage
                    Toggle.BackgroundColor3 = Color3.fromRGB(233, 63, 63)
                    Toggle.BackgroundTransparency = 0.500
                    Toggle.Size = UDim2.new(0, 260, 0, 38)

                    ToggleCorner.CornerRadius = UDim.new(0, 5)
                    ToggleCorner.Name = "ToggleCorner"
                    ToggleCorner.Parent = Toggle

                    Tgle.Name = "Tgle"
                    Tgle.Parent = Toggle
                    Tgle.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Tgle.Position = UDim2.new(0, 1, 0, 1)
                    Tgle.Size = UDim2.new(0, 258, 0, 36)

                    TgleCorner.CornerRadius = UDim.new(0, 5)
                    TgleCorner.Name = "TgleCorner"
                    TgleCorner.Parent = Tgle

                    tglebtn.Name = "tglebtn"
                    tglebtn.Parent = Tgle
                    tglebtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    tglebtn.BackgroundTransparency = 1.000
                    tglebtn.Size = UDim2.new(0, 258, 0, 36)
                    tglebtn.Font = Enum.Font.SourceSans
                    tglebtn.Text = ""
                    tglebtn.TextColor3 = Color3.fromRGB(0, 0, 0)
                    tglebtn.TextSize = 14.000

                    ToggleLabel.Name = "ToggleLabel"
                    ToggleLabel.Parent = Tgle
                    ToggleLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    ToggleLabel.BackgroundTransparency = 1.000
                    ToggleLabel.Position = UDim2.new(0, 15, 0, 0)
                    ToggleLabel.Size = UDim2.new(0, 190, 0, 36)
                    ToggleLabel.Font = Enum.Font.GothamSemibold
                    ToggleLabel.Text = text
                    ToggleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
                    ToggleLabel.TextSize = 16.000
                    ToggleLabel.TextTransparency = 0.500
                    ToggleLabel.TextXAlignment = Enum.TextXAlignment.Left

                    ToggleImage.Name = "ToggleImage"
                    ToggleImage.Parent = Tgle
                    ToggleImage.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    ToggleImage.BackgroundTransparency = 0.500
                    ToggleImage.Position = UDim2.new(0, 225, 0, 5)
                    ToggleImage.Size = UDim2.new(0, 26, 0, 26)

                    ToggleImageCorner.CornerRadius = UDim.new(0, 5)
                    ToggleImageCorner.Name = "ToggleImageCorner"
                    ToggleImageCorner.Parent = ToggleImage

                    tgleimg.Name = "tgleimg"
                    tgleimg.Parent = ToggleImage
                    tgleimg.AnchorPoint = Vector2.new(0.5, 0.5)
                    tgleimg.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    tgleimg.BackgroundTransparency = 0.500
                    tgleimg.Position = UDim2.new(0, 13, 0, 13)
                    tgleimg.Size = UDim2.new(0, 0, 0, 0)

                    tgleimg_2.CornerRadius = UDim.new(0, 5)
                    tgleimg_2.Name = "tgleimg_2"
                    tgleimg_2.Parent = tgleimg

                    tglebtn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Toggle,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            ToggleLabel,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            ToggleImage,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            tgleimg,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                    end)
                    tglebtn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Toggle,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            ToggleLabel,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            ToggleImage,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            tgleimg,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                    end)
                    if config == true then
                        istoggled = true
                        pcall(callback,istoggled)
                        tgleimg:TweenSize(UDim2.new(0, 26, 0, 26),"In","Bounce",0.1,true)
                        TweenService:Create(
                            Toggle,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundColor3 = Color3.fromRGB(212, 0, 255)}
                        ):Play()
                        TweenService:Create(
                            ToggleLabel,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextColor3 = Color3.fromRGB(212, 0, 255)}
                        ):Play()
                    end

                    local istoggled = config or false
                    tglebtn.MouseButton1Click:Connect(function()
                        if istoggled == false then
                            istoggled = true
                            tgleimg:TweenSize(UDim2.new(0, 26, 0, 26),"In","Quad",0.1,true)
                            TweenService:Create(
                                Toggle,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {BackgroundColor3 = Color3.fromRGB(212, 0, 255)}
                            ):Play()
                            TweenService:Create(
                                ToggleLabel,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextColor3 = Color3.fromRGB(212, 0, 255)}
                            ):Play()
                        else
                            istoggled = false
                            tgleimg:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.1,true)
                            TweenService:Create(
                                Toggle,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {BackgroundColor3 = Color3.fromRGB(233,63,63)}
                            ):Play()
                            TweenService:Create(
                                ToggleLabel,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextColor3 = Color3.fromRGB(255,255,255)}
                            ):Play()
                        end
                        pcall(callback,istoggled)
                    end)
                end

                function main:AddLabel(text)
                    local Label = Instance.new("TextLabel")
                    local PaddingLabel = Instance.new("UIPadding")
                    local labell = {}
            
                    Label.Name = "Label"
                    Label.Parent = ScrollPage
                    Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Label.BackgroundTransparency = 1.000
                    Label.Size = UDim2.new(0, 260, 0, 20)
                    Label.Font = Enum.Font.GothamSemibold
                    Label.TextColor3 = Color3.fromRGB(225, 225, 225)
                    Label.TextSize = 16.000
                    Label.Text = text
                    Label.TextXAlignment = Enum.TextXAlignment.Left
        
                    PaddingLabel.PaddingLeft = UDim.new(0,15)
                    PaddingLabel.Parent = Label
                    PaddingLabel.Name = "PaddingLabel"
            
                    function labell:Set(newtext)
                        Label.Text = newtext
                    end
        
                    return labell
                end

                return main
            end
            return uitab
        end
        return Ui
    end
    local function loading()
        local Loading = Instance.new("ScreenGui")
        local Blur = Instance.new("Frame")
        local Main = Instance.new("Frame")
        local UICorner = Instance.new("UICorner")
        local Logo = Instance.new("ImageLabel")
        local UICorner_2 = Instance.new("UICorner")
        local Load = Instance.new("Frame")
        local UICorner_3 = Instance.new("UICorner")
        local Bar = Instance.new("Frame")
        local UICorner_4 = Instance.new("UICorner")
        local BAR1 = Instance.new("Frame")
        local UICorner_5 = Instance.new("UICorner")
        local TextLabel = Instance.new("TextLabel")
        local Top = Instance.new("Frame")
        local UICorner_6 = Instance.new("UICorner")
        local TextLabel_2 = Instance.new("TextLabel")
        local TextLabel_3 = Instance.new("TextLabel")

        --Properties:

        Loading.Name = "Loading"
        Loading.Parent = game.CoreGui
        Loading.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

        Blur.Name = "Blur"
        Blur.Parent = Loading
        Blur.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
        Blur.BackgroundTransparency = 0.500
        Blur.Size = UDim2.new(1, 0, 1, 0)

        Main.Name = "Main"
        Main.Parent = Blur
        Main.AnchorPoint = Vector2.new(0.5, 0.5)
        Main.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
        Main.ClipsDescendants = true
        Main.Position = UDim2.new(0.5, 0, 0.499241263, 0)
        Main.Size = UDim2.new(0, 500, 0, 300)

        UICorner.Parent = Main

        Logo.Name = "Logo"
        Logo.Parent = Main
        Logo.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Logo.Position = UDim2.new(0.400000006, 0, 0.163333327, 0)
        Logo.Size = UDim2.new(0, 100, 0, 100)
        Logo.Image = "rbxassetid://10123314587"

        UICorner_2.CornerRadius = UDim.new(0, 100)
        UICorner_2.Parent = Logo

        Load.Name = "Load"
        Load.Parent = Main
        Load.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Load.Position = UDim2.new(0, 15, 0, 170)
        Load.Size = UDim2.new(0, 470, 0, 115)

        UICorner_3.Parent = Load

        Bar.Name = "Bar"
        Bar.Parent = Load
        Bar.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
        Bar.Position = UDim2.new(0, 15, 0, 80)
        Bar.Size = UDim2.new(0, 440, 0, 15)

        UICorner_4.CornerRadius = UDim.new(0, 5)
        UICorner_4.Parent = Bar

        BAR1.Name = "BAR1"
        BAR1.Parent = Bar
        BAR1.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
        BAR1.Size = UDim2.new(0, 0, 0, 15)

        UICorner_5.CornerRadius = UDim.new(0, 5)
        UICorner_5.Parent = BAR1

        TextLabel.Parent = Load
        TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextLabel.BackgroundTransparency = 1.000
        TextLabel.Position = UDim2.new(0.0319148935, 0, 0.173913032, 0)
        TextLabel.Size = UDim2.new(0, 440, 0, 25)
        TextLabel.Font = Enum.Font.GothamSemibold
        TextLabel.Text = "Loading"
        TextLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
        TextLabel.TextSize = 16.000
        spawn(function()
            for i = 1,5 do 
                wait(0.5)
                TextLabel.Text = "Loading."
                wait(0.5) 
                TextLabel.Text = "Loading.."
                wait(0.5)
                TextLabel.Text = "Loading..."
            end
        end)

        Top.Name = "Top"
        Top.Parent = Main
        Top.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Top.Size = UDim2.new(0, 500, 0, 30)

        UICorner_6.Parent = Top

        TextLabel_2.Parent = Top
        TextLabel_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextLabel_2.BackgroundTransparency = 1.000
        TextLabel_2.Position = UDim2.new(0.0299999993, 0, 0, 0)
        TextLabel_2.Size = UDim2.new(0, 61, 0, 30)
        TextLabel_2.Font = Enum.Font.GothamSemibold
        TextLabel_2.Text = "EDOG"
        TextLabel_2.TextColor3 = Color3.fromRGB(225, 225, 225)
        TextLabel_2.TextSize = 17.000

        TextLabel_3.Parent = Top
        TextLabel_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextLabel_3.BackgroundTransparency = 1.000
        TextLabel_3.Position = UDim2.new(0.151999995, 0, 0, 0)
        TextLabel_3.Size = UDim2.new(0, 61, 0, 30)
        TextLabel_3.Font = Enum.Font.GothamSemibold
        TextLabel_3.Text = "HUB"
        TextLabel_3.TextColor3 = Color3.fromRGB(212, 0, 255)
        TextLabel_3.TextSize = 17.000
        TextLabel_3.TextXAlignment = Enum.TextXAlignment.Left
        
        BAR1:TweenSize(UDim2.new(0,440,0,15),"Out","Linear",5,true)
        wait(5)
        Main:TweenSize(UDim2.new(0,0,0,0),"Out","Quad",0.4,true)
        wait(0.4)
        
        do 
            local Load = game.CoreGui:FindFirstChild("Loading")
            if Load then
                Load:Destroy()
            end
        end
    end
    loading()

    if string.lower(game:GetService("RbxAnalyticsService"):GetClientId()) == game:GetService("RbxAnalyticsService"):GetClientId() then
        local ScreenGui = Instance.new("ScreenGui")
        local ImageButton = Instance.new("ImageButton")

        ScreenGui.Parent = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

        ImageButton.Parent = ScreenGui
        ImageButton.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
        ImageButton.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
        ImageButton.Size = UDim2.new(0, 50, 0, 50)
        ImageButton.Image = "rbxassetid://10123314587"
        ImageButton.MouseButton1Down:connect(function()
            game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
            game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
        end)
    end

    local win = library:AddWindow("Edog")

    local MainTab = win:AddTab("Main")
    local Main1 = MainTab:AddPage()
    spawn(function ()
        setfflag("HumanoidParallelRemoveNoPhysics", "False")
        setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
        game:GetService("RunService").Stepped:Connect(function()
            pcall(function()
                if SaveSettings["Main"]["Autofarm"] or SaveSettings["Main"]["Auto Sea King"] or SaveSettings["Main"]["CollectChest"] or SaveSettings["Main"]["Auto GhostShip"] then
                    local plr = game:GetService("Players").LocalPlayer
                    local char = plr.Character or plr.CharacterAdded:Wait()
                    char.Humanoid:ChangeState(11)
                end
            end)
        end)
    end)
    local SaveSettings = {
        ["Main"] = {
            ["Autofarm"] = false,
            ['Autonewworld'] = false,
            ["Random Fruit"] = false,
            ["Auto Sea King"] = false,
            ["CollectChest"] = false,
            ["HopServer"] = false,
            ["Auto Seber"] = false,
            ["Auto Seber Hop"] = false,
            ["Auto GhostShip"] = false,
            ["Auto GhostShip Hop"] = false,
        },
        ['Mode'] = {
            ["Mode"] = 3,
            ["Distance"] = 5,
        },
        ["Stats"] = {
            ["Melee"] = false,
            ["MeleeCap"] = 4250,
            ["Defense"] = false,
            ["DefenseCap"] = 4250,
            ["Sword"] = false,
            ["SwordCap"] = 4250,
            ["PowerFruit"] = false,
            ["PowerFruitCap"] = 4250,
        },
        ["Main2"] = {
            ["SelectToolWeapon"] = "N/A",
            ["SelectMoney"] = "N/A",
        },
        ['Raid'] = {
            ["SelectRaid"] = "N/A",
            ["Start"] = false,
        },
        ['H'] = {
            ["Health"] = 60,
        },
        ["MISC"] = {
            ["Geppo Inf"] = false,
        },
        ["Settings"] = {
            ["SkilZ"] = true,
            ["SkilX"] = true,
            ["SkilC"] = true,
            ["SkilV"] = true,
            ["HAKI"] = true,
        },
    }
    function Load()
        if readfile and writefile and isfile and isfolder then
            if isfolder("Zenper Hub") == false then
                makefolder("Zenper Hub")
            end
            if isfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json") == false then
                writefile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(SaveSettings))
            else
                local Decode = game:GetService("HttpService"):JSONDecode(readfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json"))
                for i,v in pairs(Decode) do
                    SaveSettings[i] = v
                end
            end
        else
            warn("Failed Load")
            return false
        end
    end
    function Save()
        if readfile and writefile and isfile then
            if isfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json") == false then
                Load()
            else
                local Decode = game:GetService("HttpService"):JSONDecode(readfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json"))
                local Array = {}
                for i,v in pairs(SaveSettings) do
                    Array[i] = v
                end
                writefile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(Array))
            end
        else
            warn("Failed Save")
            return false
        end
    end
    Load()
    Save()
    local placeId = game.PlaceId
    local plr = game.Players.LocalPlayer
    local VirtualUser = game:GetService('VirtualUser')
    if placeId == 4520749081 then
        OldWorld = true
    elseif placeId == 6381829480 then
        NewWorld = true
    elseif placeId == 5931540094 then
        Raids = true
    else
        game.Players.LocalPlayer:Kick("รันผิดเกมป่าว")
    end

    Main1:AddDropdown("Select Mode",{'Easy', 'Difficult'},function(value)
        SaveSettings['Raid']["SelectRaid"] = value
        Save()
    end)
    Main1:AddToggle("Start Dungeon",SaveSettings["Raid"]["Start"], function(vu)
        SaveSettings["Raid"]["Start"] = vu
        Save()
    end)
    Main1:AddSlider('Health %', 1, 100, SaveSettings["H"]["Health"], function(value)
        SaveSettings["H"]["Health"] = value
        Save()
    end)
    function EquipRaid()
        for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
            if v.ClassName == "Tool" then
                if v.ToolTip == "Sword" or v.ToolTip == "Combat" or v.ToolTip == "Power" then
                    if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                        local ToolSe = tostring(v.Name)
                        local tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
                        wait(.2)
                        game.Players.LocalPlayer.Character.Humanoid:EquipTool(tool)
                    end
                end
            end
        end
    end
    spawn(function()
        while wait() do
            if SaveSettings["Raid"]["Start"] and OldWorld then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6725.5546875, 103.99608612060547, 957.6272583007812)  
            elseif SaveSettings["Raid"]["Start"] and NewWorld then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2696.10059, 223.119431, 2.25799251, -0.817431152, 2.25255032e-08, 0.57602632, -6.55847598e-09, 1, -4.84120335e-08, -0.57602632, -4.33513598e-08, -0.817431152)    
            end
        end 
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Raid"]["Start"] and Raids then
                    local args = {
                        [1] = SaveSettings['Raid']["SelectRaid"]
                    }
                    game:GetService("ReplicatedStorage").ChooseMapRemote:FireServer(unpack(args))
                    if game:GetService("Players").LocalPlayer.PlayerGui["GoldenArena GUI"].StartButton.Visible == true then
                        game:GetService("ReplicatedStorage").GoldenArenaEvents.StartEvent:FireServer()
                    elseif game:GetService("Players").LocalPlayer.PlayerGui["GoldenArena GUI"].StartButton.Visible == false then
                        if game:GetService("Workspace").MOB:GetDescendants("HumanoidRootPart") then
                            for i,v in pairs(game:GetService("Workspace").MOB:GetDescendants()) do
                                if v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") then
                                    repeat game:GetService("RunService").Heartbeat:wait()
                                        MinHealth = game.Players.LocalPlayer.Character.Humanoid.MaxHealth * SaveSettings["H"]["Health"] / 100
                                        if game.Players.LocalPlayer.Character.Humanoid.Health > MinHealth then
                                            if v.Humanoid.Health > 0 then
                                                EquipRaid()
                                                game:GetService'VirtualUser':CaptureController()
                                                game:GetService('VirtualUser'):ClickButton1(Vector2.new(50, 50), CFrame.new(Vector3.new(0, 0, 0)))
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.Angles(math.rad(-90), 0, 0) * CFrame.new(0,0,7)
                                            end
                                        else
                                            repeat game:GetService("RunService").Heartbeat:wait()
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0,500,0)
                                                local args = {
                                                    [1] = CFrame.new(0,500,0) * CFrame.Angles(0,500,0),
                                                    [2] = "Down"
                                                }
                                                game:GetService("Players").LocalPlayer.Character.Cyborg.E:InvokeServer(unpack(args))
                                            until SaveSettings["Raid"]["Start"] == false or game.Players.LocalPlayer.Character.Humanoid.Health == game.Players.LocalPlayer.Character.Humanoid.MaxHealth
                                        end
                                    until not v.Parent or v.Humanoid.Health <= 0 or SaveSettings["Raid"]["Start"] == false
                                end
                            end
                        else
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0,500,0)
                        end
                    end
                end
            end)
        end
    end)
else
repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
if game.PlaceId == 5931540094 and not game:GetService("Players").LocalPlayer.PlayerGui:FindFirstChild("Stats")  then
    game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("ChooseMap")
end
if game.PlaceId == 6381829480 or game.PlaceId == 4520749081 then
    game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("Stats")
    game:GetService("Players").LocalPlayer:WaitForChild("PlayerStats")
end
    do
        pcall(function()
            local httpsreq
            if syn then
                httpsreq = syn.request
            elseif KRNL_LOADED then
                httpsreq = request
            else
                httpsreq = request
            end
            httpsreq({
                Url = "http://127.0.0.1:6463/rpc?v=1",
                Method = "POST",
                Headers = {
                    ["Content-Type"] = "application/json",
                    ["Origin"] = "https://discord.com"
                },
                Body = game:GetService("HttpService"):JSONEncode({
                    cmd = "INVITE_BROWSER",
                    args = {
                        code = "fZbCgS6n"
                    },
                    nonce = game:GetService("HttpService"):GenerateGUID(false)
                }),
            })
        end)
    end
    do
        local ui = game.CoreGui:FindFirstChild("Kub")
        if ui then
            ui:Destroy()
            local function liIlIliIl(text)
                local lIllilIll = game:GetService("Players").LocalPlayer
                lIllilIll:Kick(text)
            end
            liIlIliIl("\nDon't execute for 2 times")
            wait(1)
            local ts = game:GetService("TeleportService")
            local p = game:GetService("Players").LocalPlayer
            local pid = game.PlaceId
            ts:Teleport(pid, p)
        end
    end

    local UserInputService = game:GetService("UserInputService")
    local TweenService = game:GetService("TweenService")

    local function MakeDraggable(topbarobject, object)
        local Dragging = nil
        local DragInput = nil
        local DragStart = nil
        local StartPosition = nil

        local function Update(input)
            local Delta = input.Position - DragStart
            local pos =
                UDim2.new(
                    StartPosition.X.Scale,
                    StartPosition.X.Offset + Delta.X,
                    StartPosition.Y.Scale,
                    StartPosition.Y.Offset + Delta.Y
                )
            local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})
            Tween:Play()
        end

        topbarobject.InputBegan:Connect(
            function(input)
                if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
                    Dragging = true
                    DragStart = input.Position
                    StartPosition = object.Position

                    input.Changed:Connect(
                        function()
                            if input.UserInputState == Enum.UserInputState.End then
                                Dragging = false
                            end
                        end
                    )
                end
            end
        )

        topbarobject.InputChanged:Connect(
            function(input)
                if
                    input.UserInputType == Enum.UserInputType.MouseMovement or
                    input.UserInputType == Enum.UserInputType.Touch
                then
                    DragInput = input
                end
            end
        )

        UserInputService.InputChanged:Connect(
            function(input)
                if input == DragInput and Dragging then
                    Update(input)
                end
            end
        )
    end

    local library = {}

    function library:AddWindow(text,keybind)
        local currenttab = ""
        local uihide = false
        local abc = false
        keybind = keybind or Enum.KeyCode.RightControl
        yoo = string.gsub(tostring(keybind),"Enum.KeyCode.","")

        local Kub = Instance.new("ScreenGui")
        Kub.Name = "Kub"
        Kub.Parent = game.CoreGui
        Kub.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

        local Main = Instance.new("Frame")
        Main.Name = "Main"
        Main.Parent = Kub
        Main.AnchorPoint = Vector2.new(0.5,0.5)
        Main.ClipsDescendants = true
        Main.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
        Main.Position = UDim2.new(0.5, 0, 0.499, 0)
        Main.Size = UDim2.new(0, 0, 0, 0)

        Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)

        local MainCorner = Instance.new("UICorner")
        MainCorner.Name = "MainCorner"
        MainCorner.Parent = Main

        local Top = Instance.new("Frame")
        Top.Name = "Top"
        Top.Parent = Main
        Top.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Top.Size = UDim2.new(0, 656, 0, 27)

        local TopCorner = Instance.new("UICorner")
        TopCorner.Name = "TopCorner"
        TopCorner.Parent = Top

        local NameHub = Instance.new("TextLabel")
        NameHub.Name = "NameHub"
        NameHub.Parent = Top
        NameHub.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        NameHub.BackgroundTransparency = 1.000
        NameHub.Position = UDim2.new(0, 12, 0, 0)
        NameHub.Size = UDim2.new(0, 61, 0, 27)
        NameHub.Font = Enum.Font.GothamSemibold
        NameHub.Text = string.upper(text)
        NameHub.TextColor3 = Color3.fromRGB(225, 225, 225)
        NameHub.TextSize = 17.000

        local NameHub2 = Instance.new("TextLabel")
        NameHub2.Name = "NameHub2"
        NameHub2.Parent = Top
        NameHub2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        NameHub2.BackgroundTransparency = 1.000
        NameHub2.Position = UDim2.new(0, 71, 0, 0)
        NameHub2.Size = UDim2.new(0, 61, 0, 27)
        NameHub2.Font = Enum.Font.GothamSemibold
        NameHub2.Text = "HUB"
        NameHub2.TextColor3 = Color3.fromRGB(212, 0, 255)
        NameHub2.TextSize = 17.000
        NameHub2.TextXAlignment = Enum.TextXAlignment.Left

        local BindButton = Instance.new("TextButton")
        BindButton.Name = "BindButton"
        BindButton.Parent = Top
        BindButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        BindButton.BackgroundTransparency = 1.000
        BindButton.Position = UDim2.new(0, 550, 0, 0)
        BindButton.Size = UDim2.new(0, 100, 0, 27)
        BindButton.Font = Enum.Font.GothamSemibold
        BindButton.Text = "[ "..string.gsub(tostring(keybind),"Enum.KeyCode.","").." ]"
        BindButton.TextColor3 = Color3.fromRGB(103, 103, 103)
        BindButton.TextSize = 11.000

        BindButton.MouseButton1Click:Connect(function ()
            BindButton.Text = "[ ... ]"
            local inputwait = game:GetService("UserInputService").InputBegan:wait()
            local shiba = inputwait.KeyCode == Enum.KeyCode.Unknown and inputwait.UserInputType or inputwait.KeyCode

            if
            shiba.Name ~= "Focus" and shiba.Name ~= "MouseMovement" and shiba.Name ~= "Focus"
            then
                BindButton.Text = "[ "..shiba.Name.." ]"
                yoo = shiba.Name
            end
        end)

        
        local Tab = Instance.new("Frame")
        Tab.Name = "Tab"
        Tab.Parent = Main
        Tab.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Tab.Position = UDim2.new(0, 12, 0, 40)
        Tab.Size = UDim2.new(0, 633, 0, 29)

        local TabCorner = Instance.new("UICorner")
        TabCorner.Name = "TabCorner"
        TabCorner.Parent = Tab
        
        local ScrollTab = Instance.new("ScrollingFrame")
        ScrollTab.Name = "ScrollTab"
        ScrollTab.Parent = Tab
        ScrollTab.Active = true
        ScrollTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        ScrollTab.BackgroundTransparency = 1.000
        ScrollTab.BorderSizePixel = 0
        ScrollTab.Size = UDim2.new(0, 633, 0, 29)
        ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
        ScrollTab.ScrollBarThickness = 0
        
        local UIPadding = Instance.new("UIPadding")
        UIPadding.Parent = ScrollTab
        UIPadding.PaddingLeft = UDim.new(0, 10)

        local TabList = Instance.new("UIListLayout")
        TabList.Name = "TabList"
        TabList.Parent = ScrollTab
        TabList.FillDirection = Enum.FillDirection.Horizontal
        TabList.SortOrder = Enum.SortOrder.LayoutOrder
        TabList.Padding = UDim.new(0, 5)

        MakeDraggable(Top,Main)

        UserInputService.InputBegan:Connect(function(input)
            if input.KeyCode == Enum.KeyCode[yoo] then
                if uihide == false then
                    uihide = true
                    Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.4,true)
                else
                    uihide = false
                    Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)
                end
            end
        end)

        local Page = Instance.new("Frame")
        Page.Name = "Page"
        Page.Parent = Main
        Page.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Page.Position = UDim2.new(0, 11, 0, 80)
        Page.Size = UDim2.new(0, 633, 0, 305)

        local PageCorner = Instance.new("UICorner")
        PageCorner.Name = "PageCorner"
        PageCorner.Parent = Page

        local PageFolder = Instance.new("Folder")
        PageFolder.Name = "PageFolder"
        PageFolder.Parent = Page

        local UIPageLayout = Instance.new("UIPageLayout")

        UIPageLayout.Parent = PageFolder
        UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
        UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
        UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
        UIPageLayout.Padding = UDim.new(0, 10)
        UIPageLayout.TweenTime = 0.400
        UIPageLayout.GamepadInputEnabled = false
        UIPageLayout.ScrollWheelInputEnabled = false
        UIPageLayout.TouchInputEnabled = false


        local Ui = {}
        function Ui:AddTab(text)
            local TabButton = Instance.new("TextButton")
            TabButton.Name = "TabButton"
            TabButton.Parent = ScrollTab
            TabButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            TabButton.BackgroundTransparency = 1.000
            TabButton.Size = UDim2.new(0, 100, 0, 29)
            TabButton.Font = Enum.Font.GothamSemibold
            TabButton.TextColor3 = Color3.fromRGB(225, 225, 225)
            TabButton.TextSize = 15.000
            TabButton.Text = text
            TabButton.TextTransparency = 0.500
            
            local MainPage = Instance.new("Frame")

            MainPage.Name = "MainPage"
            MainPage.Parent = PageFolder
            MainPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            MainPage.BackgroundTransparency = 1.000
            MainPage.Position = UDim2.new(0.00157977885, 0, 0, 0)
            MainPage.Size = UDim2.new(0, 632, 0, 305)

            TabButton.MouseButton1Click:Connect(function()
                for i,v in next, ScrollTab:GetChildren() do
                    if v:IsA("TextButton") then
                        TweenService:Create(
                            v,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                    end
                    TweenService:Create(
                        TabButton,
                        TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                        {TextTransparency = 0}
                    ):Play()
                end
                for i,v in next, PageFolder:GetChildren() do 
                    if v.Name == "MainPage" then
                        currenttab = v.Name
                    end
                    UIPageLayout:JumpTo(MainPage)
                end
            end)

            if abc == false then
                for i,v in next, ScrollTab:GetChildren() do
                    if v:IsA("TextButton") then
                        TweenService:Create(
                            v,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                    end
                    TweenService:Create(
                        TabButton,
                        TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                        {TextTransparency = 0}
                    ):Play()
                end
                UIPageLayout:JumpToIndex(1)
                abc = true
            end

            local uitab = {}
            function uitab:AddPage()
                local MainFramePage = Instance.new("Frame")
                local UICorner = Instance.new("UICorner")
                local ScrollPage = Instance.new("ScrollingFrame")
                local PageList = Instance.new("UIListLayout")
                local UIPadding = Instance.new("UIPadding")
                local UIPadding_2 = Instance.new("UIPadding")
                local UIListLayout_2 = Instance.new("UIListLayout")
            
                MainFramePage.Name = "MainFramePage"
                MainFramePage.Parent = MainPage
                MainFramePage.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                MainFramePage.Size = UDim2.new(0, 300, 0, 285)
            
                UICorner.Parent = MainFramePage
            
                ScrollPage.Name = "ScrollPage"
                ScrollPage.Parent = MainFramePage
                ScrollPage.Active = true
                ScrollPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                ScrollPage.BackgroundTransparency = 1.000
                ScrollPage.BorderSizePixel = 0
                ScrollPage.Size = UDim2.new(0, 300, 0, 285)
                ScrollPage.CanvasSize = UDim2.new(0, 0, 0, 0)
                ScrollPage.ScrollBarThickness = 0
            
                PageList.Name = "PageList"
                PageList.Parent = ScrollPage
                PageList.SortOrder = Enum.SortOrder.LayoutOrder
                PageList.Padding = UDim.new(0, 13)
            
                UIPadding.Parent = ScrollPage
                UIPadding.PaddingLeft = UDim.new(0, 20)
                UIPadding.PaddingTop = UDim.new(0, 10)
            
                UIPadding_2.Parent = MainPage
                UIPadding_2.PaddingLeft = UDim.new(0, 10)
                UIPadding_2.PaddingTop = UDim.new(0, 10)
            
                UIListLayout_2.Parent = MainPage
                UIListLayout_2.FillDirection = Enum.FillDirection.Horizontal
                UIListLayout_2.SortOrder = Enum.SortOrder.LayoutOrder
                UIListLayout_2.Padding = UDim.new(0, 13)

                game:GetService("RunService").Stepped:Connect(function()
                    pcall(function()
                        ScrollPage.CanvasSize = UDim2.new(0,0,0,PageList.AbsoluteContentSize.Y + 26)
                        ScrollTab.CanvasSize = UDim2.new(0,TabList.AbsoluteContentSize.X + 10,0,0)
                    end)
                end)

                local main = {}
                function main:AddSeperator(text)
                    local Seperator = Instance.new("Frame")
                    local Sep1 = Instance.new("Frame")
                    local Sep2 = Instance.new("TextLabel")
                    local Sep3 = Instance.new("Frame")
                    
                    Seperator.Name = "Seperator"
                    Seperator.Parent = ScrollPage
                    Seperator.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Seperator.BackgroundTransparency = 1.000
                    Seperator.Size = UDim2.new(0, 260, 0, 20)
                    
                    Sep1.Name = "Sep1"
                    Sep1.Parent = Seperator
                    Sep1.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Sep1.BorderSizePixel = 0
                    Sep1.Position = UDim2.new(0, 0, 0, 10)
                    Sep1.Size = UDim2.new(0, 40, 0, 1)
                    
                    Sep2.Name = "Sep2"
                    Sep2.Parent = Seperator
                    Sep2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Sep2.BackgroundTransparency = 1.000
                    Sep2.Position = UDim2.new(0, 80, 0, 0)
                    Sep2.Size = UDim2.new(0, 100, 0, 20)
                    Sep2.Font = Enum.Font.GothamSemibold
                    Sep2.Text = text
                    Sep2.TextColor3 = Color3.fromRGB(255, 255, 255)
                    Sep2.TextSize = 14.000
                    
                    Sep3.Name = "Sep3"
                    Sep3.Parent = Seperator
                    Sep3.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Sep3.BorderSizePixel = 0
                    Sep3.Position = UDim2.new(0, 220, 0, 10)
                    Sep3.Size = UDim2.new(0, 40, 0, 1)
                end

                function main:AddLine()
                    local Linee = Instance.new("Frame")
                    local Line = Instance.new("Frame")
                    
                    Linee.Name = "Linee"
                    Linee.Parent = ScrollPage
                    Linee.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Linee.BackgroundTransparency = 1.000
                    Linee.Position = UDim2.new(0, 0, 0.119999997, 0)
                    Linee.Size = UDim2.new(0, 260, 0, 20)
                    
                    Line.Name = "Line"
                    Line.Parent = Linee
                    Line.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Line.BorderSizePixel = 0
                    Line.Position = UDim2.new(0, 0, 0, 10)
                    Line.Size = UDim2.new(0, 260, 0, 1)
                end

                function main:AddButton(text,callback)
                    local AddButton = Instance.new("Frame")
                    local ButtonCorner = Instance.new("UICorner")
                    local Btn = Instance.new("TextButton")
                    local BtnCorner = Instance.new("UICorner")
                    
                    AddButton.Name = "AddButton"
                    AddButton.Parent = ScrollPage
                    AddButton.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    AddButton.Size = UDim2.new(0, 260, 0, 38)
                    AddButton.BackgroundTransparency = 0.5
                    
                    ButtonCorner.CornerRadius = UDim.new(0, 5)
                    ButtonCorner.Name = "ButtonCorner"
                    ButtonCorner.Parent = AddButton
                    
                    Btn.Name = "Btn"
                    Btn.Parent = AddButton
                    Btn.AutoButtonColor = false
                    Btn.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Btn.Position = UDim2.new(0, 1, 0, 1)
                    Btn.Size = UDim2.new(0, 258, 0, 36)
                    Btn.Font = Enum.Font.GothamSemibold
                    Btn.TextColor3 = Color3.fromRGB(225, 225, 225)
                    Btn.TextSize = 16.000
                    Btn.Text = text
                    Btn.TextTransparency = 0.500
                    
                    BtnCorner.CornerRadius = UDim.new(0, 5)
                    BtnCorner.Name = "BtnCorner"
                    BtnCorner.Parent = Btn

                    Btn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Btn,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            AddButton,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                    end)

                    Btn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Btn,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            AddButton,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                    end)

                    Btn.MouseButton1Click:Connect(function()
                        callback()
                        Btn.TextSize = 9
                        TweenService:Create(
                            Btn,
                            TweenInfo.new(0.4,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                            {TextSize = 16}
                        ):Play()
                    end)
                end 

                function main:AddDropdown(text,option,callback)
                    local Dropdown = Instance.new("Frame")
                    local dropcorner = Instance.new("UICorner")
                    local Dropdownn = Instance.new("Frame")
                    local droppcorner = Instance.new("UICorner")
                    local DropBtn = Instance.new("TextButton")
                    local DropLabel = Instance.new("TextLabel")
                    local DropScroll = Instance.new("ScrollingFrame")
                    local dpd = Instance.new("UIPadding")
                    local dll = Instance.new("UIListLayout")
                    local DropImage = Instance.new("ImageLabel")
                    local isdropping = false

                    Dropdown.Name = "Dropdown"
                    Dropdown.Parent = ScrollPage
                    Dropdown.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Dropdown.BackgroundTransparency = 0.500
                    Dropdown.Size = UDim2.new(0, 260, 0, 38) -- 114
                    
                    dropcorner.CornerRadius = UDim.new(0, 5)
                    dropcorner.Name = "dropcorner"
                    dropcorner.Parent = Dropdown
                    
                    Dropdownn.Name = "Dropdownn"
                    Dropdownn.Parent = Dropdown
                    Dropdownn.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Dropdownn.ClipsDescendants = true
                    Dropdownn.Position = UDim2.new(0, 1, 0, 1)
                    Dropdownn.Size = UDim2.new(0, 258, 0, 36) -- 112
                    
                    droppcorner.CornerRadius = UDim.new(0, 5)
                    droppcorner.Name = "droppcorner"
                    droppcorner.Parent = Dropdownn
                    
                    DropBtn.Name = "DropBtn"
                    DropBtn.Parent = Dropdownn
                    DropBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropBtn.BackgroundTransparency = 1.000
                    DropBtn.Size = UDim2.new(0, 258, 0, 36)
                    DropBtn.Font = Enum.Font.SourceSans
                    DropBtn.Text = ""
                    DropBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
                    DropBtn.TextSize = 14.000
                    
                    DropLabel.Name = "DropLabel"
                    DropLabel.Parent = Dropdownn
                    DropLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropLabel.BackgroundTransparency = 1.000
                    DropLabel.Position = UDim2.new(0, 15, 0, 0)
                    DropLabel.Size = UDim2.new(0, 180, 0, 36)
                    DropLabel.Font = Enum.Font.GothamSemibold
                    DropLabel.Text = text.. " : "
                    DropLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
                    DropLabel.TextSize = 16.000
                    DropLabel.TextTransparency = 0.500
                    DropLabel.TextXAlignment = Enum.TextXAlignment.Left

                    DropImage.Name = "DropImage"
                    DropImage.Parent = Dropdownn
                    DropImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropImage.BackgroundTransparency = 1.000
                    DropImage.Position = UDim2.new(0, 230, 0, 9)
                    DropImage.Rotation = 180.000
                    DropImage.Size = UDim2.new(0, 20, 0, 20)
                    DropImage.Image = "rbxassetid://6031090990"
                    DropImage.ImageTransparency = 0.500
                    
                    DropScroll.Name = "DropScroll"
                    DropScroll.Parent = DropLabel
                    DropScroll.Active = true
                    DropScroll.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    DropScroll.BackgroundTransparency = 1.000
                    DropScroll.BorderSizePixel = 0
                    DropScroll.Position = UDim2.new(-0.105555557, 0, 1.11111116, 0)
                    DropScroll.Size = UDim2.new(0, 258, 0, 70)
                    DropScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
                    DropScroll.ScrollBarThickness = 3
                    
                    dll.Name = "dpd"
                    dll.Parent = DropScroll
                    dll.SortOrder = Enum.SortOrder.LayoutOrder
                    dll.Padding = UDim.new(0, 5)
                    
                    dpd.Name = "dll"
                    dpd.Parent = DropScroll
                    dpd.PaddingLeft = UDim.new(0, 5)
                    dpd.PaddingTop = UDim.new(0, 5)

                    for i,v in next, option do
                        local Item = Instance.new("TextButton")
                        Item.Name = "Item"
                        Item.Parent = DropScroll
                        Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                        Item.BackgroundTransparency = 1.000
                        Item.Size = UDim2.new(0, 248, 0, 29)
                        Item.Font = Enum.Font.GothamSemibold
                        Item.TextColor3 = Color3.fromRGB(225, 225, 225)
                        Item.TextSize = 16.000
                        Item.Text = tostring(v)
                        Item.TextTransparency = 0.5

                        Item.MouseEnter:Connect(function()
                            TweenService:Create(
                                Item,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextTransparency = 0}
                            ):Play()
                        end)
                        Item.MouseLeave:Connect(function()
                            TweenService:Create(
                                Item,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextTransparency = 0.5}
                            ):Play()
                        end)

                        Item.MouseButton1Click:Connect(function()
                            isdropping = false
                            Dropdown:TweenSize(UDim2.new(0,260,0,38),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                            callback(Item.Text)
                            DropLabel.Text = text.." : "..Item.Text
                        end)
                    end
                    DropScroll.CanvasSize = UDim2.new(0,0,0,dll.AbsoluteContentSize.Y + 10)

                    DropBtn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Dropdown,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            DropLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            DropImage,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {ImageTransparency = 0}
                        ):Play()
                    end)

                    DropBtn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Dropdown,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            DropLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            DropImage,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {ImageTransparency = 0.5}
                        ):Play()
                    end)

                    DropBtn.MouseButton1Click:Connect(function()
                        if isdropping == false then
                            isdropping = true
                            Dropdown:TweenSize(UDim2.new(0,260,0,114),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,258,0,112),"Out","Quad",0.3,true)
                            DropBtn:TweenSize(UDim2.new(0,258,0,112),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 0}
                            ):Play()
                        else
                            isdropping = false
                            Dropdown:TweenSize(UDim2.new(0,260,0,38),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                            DropBtn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                        end
                    end)
                    drop = {}
                    function drop:Clear()
                        DropLabel.Text = tostring(text).." :"
                        isdropping = false
                        Dropdown:TweenSize(UDim2.new(0,260,0,38),"Out","Quad",0.3,true)
                        Dropdownn:TweenSize(UDim2.new(0,258,0,36),"Out","Quad",0.3,true)
                        TweenService:Create(
                            DropImage,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {Rotation = 180}
                        ):Play()
                        for i, v in next, DropScroll:GetChildren() do
                            if v:IsA("TextButton") then
                                v:Destroy()
                            end
                        end
                        return drop
                    end
                    function drop:Add(t)
                        local Item = Instance.new("TextButton")
                        Item.Name = "Item"
                        Item.Parent = DropScroll
                        Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                        Item.BackgroundTransparency = 1.000
                        Item.Size = UDim2.new(0, 248, 0, 29)
                        Item.Font = Enum.Font.GothamSemibold
                        Item.TextColor3 = Color3.fromRGB(225, 225, 225)
                        Item.TextSize = 16.000
                        Item.TextTransparency = 0.5
                        Item.Text = tostring(t)

                        Item.MouseButton1Click:Connect(function()
                            isdropping = false
                            Dropdown:TweenSize(UDim2.new(0,260,0,36),"Out","Quad",0.3,true)
                            Dropdownn:TweenSize(UDim2.new(0,260,0,34),"Out","Quad",0.3,true)
                            TweenService:Create(
                                DropImage,
                                TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {Rotation = 180}
                            ):Play()
                            callback(Item.Text)
                            DropLabel.Text = text.." : "..Item.Text
                        end)
                    end
                    return drop
                end
                function main:AddSlider(text,min,max,set,callback)
                    local Slider = Instance.new("Frame")
                    local slidercorner = Instance.new("UICorner")
                    local sliderr = Instance.new("Frame")
                    local sliderrcorner = Instance.new("UICorner")
                    local SliderLabel = Instance.new("TextLabel")
                    local HAHA = Instance.new("Frame")
                    local AHEHE = Instance.new("TextButton")
                    local bar = Instance.new("Frame")
                    local bar1 = Instance.new("Frame")
                    local bar1corner = Instance.new("UICorner")
                    local barcorner = Instance.new("UICorner")
                    local circlebar = Instance.new("Frame")
                    local UICorner = Instance.new("UICorner")
                    local slidervalue = Instance.new("Frame")
                    local valuecorner = Instance.new("UICorner")
                    local TextBox = Instance.new("TextBox")
                    local UICorner_2 = Instance.new("UICorner")

                    Slider.Name = "Slider"
                    Slider.Parent = ScrollPage
                    Slider.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Slider.BackgroundTransparency = 0.500
                    Slider.Size = UDim2.new(0, 260, 0, 48)

                    slidercorner.CornerRadius = UDim.new(0, 5)
                    slidercorner.Name = "slidercorner"
                    slidercorner.Parent = Slider

                    sliderr.Name = "sliderr"
                    sliderr.Parent = Slider
                    sliderr.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    sliderr.Position = UDim2.new(0, 1, 0, 1)
                    sliderr.Size = UDim2.new(0, 258, 0, 46)

                    sliderrcorner.CornerRadius = UDim.new(0, 5)
                    sliderrcorner.Name = "sliderrcorner"
                    sliderrcorner.Parent = sliderr

                    SliderLabel.Name = "SliderLabel"
                    SliderLabel.Parent = sliderr
                    SliderLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    SliderLabel.BackgroundTransparency = 1.000
                    SliderLabel.Position = UDim2.new(0.0581395365, 0, 0, 0)
                    SliderLabel.Size = UDim2.new(0, 180, 0, 26)
                    SliderLabel.Font = Enum.Font.GothamSemibold
                    SliderLabel.Text = text
                    SliderLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
                    SliderLabel.TextSize = 16.000
                    SliderLabel.TextTransparency = 0.500
                    SliderLabel.TextXAlignment = Enum.TextXAlignment.Left

                    HAHA.Name = "HAHA"
                    HAHA.Parent = sliderr
                    HAHA.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    HAHA.BackgroundTransparency = 1.000
                    HAHA.Size = UDim2.new(0, 258, 0, 46)

                    AHEHE.Name = "AHEHE"
                    AHEHE.Parent = sliderr
                    AHEHE.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    AHEHE.BackgroundTransparency = 1.000
                    AHEHE.Position = UDim2.new(0, 10, 0, 35)
                    AHEHE.Size = UDim2.new(0, 238, 0, 5)
                    AHEHE.Font = Enum.Font.SourceSans
                    AHEHE.Text = ""
                    AHEHE.TextColor3 = Color3.fromRGB(0, 0, 0)
                    AHEHE.TextSize = 14.000

                    bar.Name = "bar"
                    bar.Parent = AHEHE
                    bar.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    bar.Size = UDim2.new(0, 238, 0, 5)

                    bar1.Name = "bar1"
                    bar1.Parent = bar
                    bar1.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    bar1.BackgroundTransparency = 0.500
                    bar1.Size = UDim2.new(set/max, 0, 0, 5)

                    bar1corner.CornerRadius = UDim.new(0, 5)
                    bar1corner.Name = "bar1corner"
                    bar1corner.Parent = bar1

                    barcorner.CornerRadius = UDim.new(0, 5)
                    barcorner.Name = "barcorner"
                    barcorner.Parent = bar

                    circlebar.Name = "circlebar"
                    circlebar.Parent = bar1
                    circlebar.BackgroundColor3 = Color3.fromRGB(180, 180, 180)
                    circlebar.Position = UDim2.new(1, -2, 0, -3)
                    circlebar.Size = UDim2.new(0, 10, 0, 10)

                    UICorner.CornerRadius = UDim.new(0, 5)
                    UICorner.Parent = circlebar

                    slidervalue.Name = "slidervalue"
                    slidervalue.Parent = sliderr
                    slidervalue.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    slidervalue.BackgroundTransparency = 0.500
                    slidervalue.Position = UDim2.new(0, 185, 0, 5)
                    slidervalue.Size = UDim2.new(0, 65, 0, 18)

                    valuecorner.CornerRadius = UDim.new(0, 5)
                    valuecorner.Name = "valuecorner"
                    valuecorner.Parent = slidervalue

                    TextBox.Parent = slidervalue
                    TextBox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    TextBox.Position = UDim2.new(0, 1, 0, 1)
                    TextBox.Size = UDim2.new(0, 63, 0, 16)
                    TextBox.Font = Enum.Font.GothamSemibold
                    TextBox.TextColor3 = Color3.fromRGB(225, 225, 225)
                    TextBox.TextSize = 9.000
                    TextBox.Text = set
                    TextBox.TextTransparency = 0.500

                    UICorner_2.CornerRadius = UDim.new(0, 5)
                    UICorner_2.Parent = TextBox

                    HAHA.MouseEnter:Connect(function()
                        TweenService:Create(
                            Slider,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            SliderLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            bar1,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            circlebar,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundColor3 = Color3.fromRGB(225,225,225)}
                        ):Play()
                        TweenService:Create(
                            slidervalue,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            TextBox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                    end)

                    HAHA.MouseLeave:Connect(function()
                        TweenService:Create(
                            Slider,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            SliderLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            bar1,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            circlebar,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundColor3 = Color3.fromRGB(180,180,180)}
                        ):Play()
                        TweenService:Create(
                            slidervalue,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            TextBox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                    end)

                    local mouse = game.Players.LocalPlayer:GetMouse()
                    local uis = game:GetService("UserInputService")

                    if Value == nil then
                        Value = set
                        pcall(function()
                            callback(Value)
                        end)
                    end
                    
                    AHEHE.MouseButton1Down:Connect(function()
                        Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min)) or 0
                        pcall(function()
                            callback(Value)
                        end)
                        bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 238), 0, 5)
                        circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 228), 0, -3)
                        moveconnection = mouse.Move:Connect(function()
                            TextBox.Text = Value
                            Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min))
                            pcall(function()
                                callback(Value)
                            end)
                            bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 238), 0, 5)
                            circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 228), 0, -3)
                        end)
                        releaseconnection = uis.InputEnded:Connect(function(Mouse)
                            if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                                Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min))
                                pcall(function()
                                    callback(Value)
                                end)
                                bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 238), 0, 5)
                                circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 228), 0, -3)
                                moveconnection:Disconnect()
                                releaseconnection:Disconnect()
                            end
                        end)
                    end)
                    releaseconnection = uis.InputEnded:Connect(function(Mouse)
                        if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                            Value = math.floor((((tonumber(max) - tonumber(min)) / 238) * bar1.AbsoluteSize.X) + tonumber(min))
                            TextBox.Text = Value
                        end
                    end)

                    TextBox.FocusLost:Connect(function()
                        if tonumber(TextBox.Text) > max then
                            TextBox.Text  = max
                        end
                        bar1.Size = UDim2.new((tonumber(TextBox.Text) or 0) / max, 0, 0, 5)
                        circlebar.Position = UDim2.new(1, -2, 0, -3)
                        TextBox.Text = tostring(tonumber(TextBox.Text) and math.floor( (tonumber(TextBox.Text) / max) * (max - min) + min) )
                        pcall(callback, TextBox.Text)
                    end)
                end

                function main:AddTextbox(text,disappear,callback)
                    local Textbox = Instance.new("Frame")
                    local TextboxCorner = Instance.new("UICorner")
                    local Textboxx = Instance.new("Frame")
                    local TextboxxCorner = Instance.new("UICorner")
                    local TextboxLabel = Instance.new("TextLabel")
                    local txtbtn = Instance.new("TextButton")
                    local RealTextbox = Instance.new("TextBox")
                    local UICorner = Instance.new("UICorner")

                    Textbox.Name = "Textbox"
                    Textbox.Parent = ScrollPage
                    Textbox.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    Textbox.BackgroundTransparency = 0.500
                    Textbox.Size = UDim2.new(0, 260, 0, 38)

                    TextboxCorner.CornerRadius = UDim.new(0, 5)
                    TextboxCorner.Name = "TextboxCorner"
                    TextboxCorner.Parent = Textbox

                    Textboxx.Name = "Textboxx"
                    Textboxx.Parent = Textbox
                    Textboxx.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Textboxx.Position = UDim2.new(0, 1, 0, 1)
                    Textboxx.Size = UDim2.new(0, 258, 0, 36)

                    TextboxxCorner.CornerRadius = UDim.new(0, 5)
                    TextboxxCorner.Name = "TextboxxCorner"
                    TextboxxCorner.Parent = Textboxx

                    TextboxLabel.Name = "TextboxLabel"
                    TextboxLabel.Parent = Textbox
                    TextboxLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    TextboxLabel.BackgroundTransparency = 1.000
                    TextboxLabel.Position = UDim2.new(0, 15, 0, 0)
                    TextboxLabel.Text = text
                    TextboxLabel.Size = UDim2.new(0, 145, 0, 38)
                    TextboxLabel.Font = Enum.Font.GothamSemibold
                    TextboxLabel.TextColor3 = Color3.fromRGB(212, 0, 255)
                    TextboxLabel.TextSize = 16.000
                    TextboxLabel.TextTransparency = 0.500
                    TextboxLabel.TextXAlignment = Enum.TextXAlignment.Left

                    txtbtn.Name = "txtbtn"
                    txtbtn.Parent = Textbox
                    txtbtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    txtbtn.BackgroundTransparency = 1.000
                    txtbtn.Position = UDim2.new(0, 1, 0, 1)
                    txtbtn.Size = UDim2.new(0, 258, 0, 36)
                    txtbtn.Font = Enum.Font.SourceSans
                    txtbtn.Text = ""
                    txtbtn.TextColor3 = Color3.fromRGB(0, 0, 0)
                    txtbtn.TextSize = 14.000

                    RealTextbox.Name = "RealTextbox"
                    RealTextbox.Parent = Textbox
                    RealTextbox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    RealTextbox.BackgroundTransparency = 0.500
                    RealTextbox.Position = UDim2.new(0, 150, 0, 7)
                    RealTextbox.Size = UDim2.new(0, 100, 0, 22)
                    RealTextbox.Font = Enum.Font.GothamSemibold
                    RealTextbox.Text = ""
                    RealTextbox.TextColor3 = Color3.fromRGB(225, 225, 225)
                    RealTextbox.TextSize = 11.000
                    RealTextbox.TextTransparency = 0.500

                    txtbtn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Textbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            TextboxLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                    end)

                    txtbtn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Textbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            TextboxLabel,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            RealTextbox,
                            TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                    end)

                    RealTextbox.FocusLost:Connect(function()
                        callback(RealTextbox.Text)
                        if disappear then
                            RealTextbox.Text = ""
                        end
                    end)

                    UICorner.CornerRadius = UDim.new(0, 5)
                    UICorner.Parent = RealTextbox
                end

                function main:AddToggle(text,config,callback)
                    local Toggle = Instance.new("Frame")
                    local ToggleCorner = Instance.new("UICorner")
                    local Tgle = Instance.new("Frame")
                    local TgleCorner = Instance.new("UICorner")
                    local tglebtn = Instance.new("TextButton")
                    local ToggleLabel = Instance.new("TextLabel")
                    local ToggleImage = Instance.new("Frame")
                    local ToggleImageCorner = Instance.new("UICorner")
                    local tgleimg = Instance.new("Frame")
                    local tgleimg_2 = Instance.new("UICorner")

                    Toggle.Name = "Toggle"
                    Toggle.Parent = ScrollPage
                    Toggle.BackgroundColor3 = Color3.fromRGB(233, 63, 63)
                    Toggle.BackgroundTransparency = 0.500
                    Toggle.Size = UDim2.new(0, 260, 0, 38)

                    ToggleCorner.CornerRadius = UDim.new(0, 5)
                    ToggleCorner.Name = "ToggleCorner"
                    ToggleCorner.Parent = Toggle

                    Tgle.Name = "Tgle"
                    Tgle.Parent = Toggle
                    Tgle.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
                    Tgle.Position = UDim2.new(0, 1, 0, 1)
                    Tgle.Size = UDim2.new(0, 258, 0, 36)

                    TgleCorner.CornerRadius = UDim.new(0, 5)
                    TgleCorner.Name = "TgleCorner"
                    TgleCorner.Parent = Tgle

                    tglebtn.Name = "tglebtn"
                    tglebtn.Parent = Tgle
                    tglebtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    tglebtn.BackgroundTransparency = 1.000
                    tglebtn.Size = UDim2.new(0, 258, 0, 36)
                    tglebtn.Font = Enum.Font.SourceSans
                    tglebtn.Text = ""
                    tglebtn.TextColor3 = Color3.fromRGB(0, 0, 0)
                    tglebtn.TextSize = 14.000

                    ToggleLabel.Name = "ToggleLabel"
                    ToggleLabel.Parent = Tgle
                    ToggleLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    ToggleLabel.BackgroundTransparency = 1.000
                    ToggleLabel.Position = UDim2.new(0, 15, 0, 0)
                    ToggleLabel.Size = UDim2.new(0, 190, 0, 36)
                    ToggleLabel.Font = Enum.Font.GothamSemibold
                    ToggleLabel.Text = text
                    ToggleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
                    ToggleLabel.TextSize = 16.000
                    ToggleLabel.TextTransparency = 0.500
                    ToggleLabel.TextXAlignment = Enum.TextXAlignment.Left

                    ToggleImage.Name = "ToggleImage"
                    ToggleImage.Parent = Tgle
                    ToggleImage.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
                    ToggleImage.BackgroundTransparency = 0.500
                    ToggleImage.Position = UDim2.new(0, 225, 0, 5)
                    ToggleImage.Size = UDim2.new(0, 26, 0, 26)

                    ToggleImageCorner.CornerRadius = UDim.new(0, 5)
                    ToggleImageCorner.Name = "ToggleImageCorner"
                    ToggleImageCorner.Parent = ToggleImage

                    tgleimg.Name = "tgleimg"
                    tgleimg.Parent = ToggleImage
                    tgleimg.AnchorPoint = Vector2.new(0.5, 0.5)
                    tgleimg.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
                    tgleimg.BackgroundTransparency = 0.500
                    tgleimg.Position = UDim2.new(0, 13, 0, 13)
                    tgleimg.Size = UDim2.new(0, 0, 0, 0)

                    tgleimg_2.CornerRadius = UDim.new(0, 5)
                    tgleimg_2.Name = "tgleimg_2"
                    tgleimg_2.Parent = tgleimg

                    tglebtn.MouseEnter:Connect(function()
                        TweenService:Create(
                            Toggle,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            ToggleLabel,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            ToggleImage,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                        TweenService:Create(
                            tgleimg,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0}
                        ):Play()
                    end)
                    tglebtn.MouseLeave:Connect(function()
                        TweenService:Create(
                            Toggle,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            ToggleLabel,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            ToggleImage,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                        TweenService:Create(
                            tgleimg,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundTransparency = 0.5}
                        ):Play()
                    end)
                    if config == true then
                        istoggled = true
                        pcall(callback,istoggled)
                        tgleimg:TweenSize(UDim2.new(0, 26, 0, 26),"In","Bounce",0.1,true)
                        TweenService:Create(
                            Toggle,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {BackgroundColor3 = Color3.fromRGB(212, 0, 255)}
                        ):Play()
                        TweenService:Create(
                            ToggleLabel,
                            TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                            {TextColor3 = Color3.fromRGB(212, 0, 255)}
                        ):Play()
                    end

                    local istoggled = config or false
                    tglebtn.MouseButton1Click:Connect(function()
                        if istoggled == false then
                            istoggled = true
                            tgleimg:TweenSize(UDim2.new(0, 26, 0, 26),"In","Quad",0.1,true)
                            TweenService:Create(
                                Toggle,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {BackgroundColor3 = Color3.fromRGB(212, 0, 255)}
                            ):Play()
                            TweenService:Create(
                                ToggleLabel,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextColor3 = Color3.fromRGB(212, 0, 255)}
                            ):Play()
                        else
                            istoggled = false
                            tgleimg:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.1,true)
                            TweenService:Create(
                                Toggle,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {BackgroundColor3 = Color3.fromRGB(233,63,63)}
                            ):Play()
                            TweenService:Create(
                                ToggleLabel,
                                TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                                {TextColor3 = Color3.fromRGB(255,255,255)}
                            ):Play()
                        end
                        pcall(callback,istoggled)
                    end)
                end

                function main:AddLabel(text)
                    local Label = Instance.new("TextLabel")
                    local PaddingLabel = Instance.new("UIPadding")
                    local labell = {}
            
                    Label.Name = "Label"
                    Label.Parent = ScrollPage
                    Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    Label.BackgroundTransparency = 1.000
                    Label.Size = UDim2.new(0, 260, 0, 20)
                    Label.Font = Enum.Font.GothamSemibold
                    Label.TextColor3 = Color3.fromRGB(225, 225, 225)
                    Label.TextSize = 16.000
                    Label.Text = text
                    Label.TextXAlignment = Enum.TextXAlignment.Left
        
                    PaddingLabel.PaddingLeft = UDim.new(0,15)
                    PaddingLabel.Parent = Label
                    PaddingLabel.Name = "PaddingLabel"
            
                    function labell:Set(newtext)
                        Label.Text = newtext
                    end
        
                    return labell
                end

                return main
            end
            return uitab
        end
        return Ui
    end
    local function loading()
        local Loading = Instance.new("ScreenGui")
        local Blur = Instance.new("Frame")
        local Main = Instance.new("Frame")
        local UICorner = Instance.new("UICorner")
        local Logo = Instance.new("ImageLabel")
        local UICorner_2 = Instance.new("UICorner")
        local Load = Instance.new("Frame")
        local UICorner_3 = Instance.new("UICorner")
        local Bar = Instance.new("Frame")
        local UICorner_4 = Instance.new("UICorner")
        local BAR1 = Instance.new("Frame")
        local UICorner_5 = Instance.new("UICorner")
        local TextLabel = Instance.new("TextLabel")
        local Top = Instance.new("Frame")
        local UICorner_6 = Instance.new("UICorner")
        local TextLabel_2 = Instance.new("TextLabel")
        local TextLabel_3 = Instance.new("TextLabel")

        --Properties:

        Loading.Name = "Loading"
        Loading.Parent = game.CoreGui
        Loading.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

        Blur.Name = "Blur"
        Blur.Parent = Loading
        Blur.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
        Blur.BackgroundTransparency = 0.500
        Blur.Size = UDim2.new(1, 0, 1, 0)

        Main.Name = "Main"
        Main.Parent = Blur
        Main.AnchorPoint = Vector2.new(0.5, 0.5)
        Main.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
        Main.ClipsDescendants = true
        Main.Position = UDim2.new(0.5, 0, 0.499241263, 0)
        Main.Size = UDim2.new(0, 500, 0, 300)

        UICorner.Parent = Main

        Logo.Name = "Logo"
        Logo.Parent = Main
        Logo.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Logo.Position = UDim2.new(0.400000006, 0, 0.163333327, 0)
        Logo.Size = UDim2.new(0, 100, 0, 100)
        Logo.Image = "rbxassetid://10123314587"

        UICorner_2.CornerRadius = UDim.new(0, 100)
        UICorner_2.Parent = Logo

        Load.Name = "Load"
        Load.Parent = Main
        Load.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Load.Position = UDim2.new(0, 15, 0, 170)
        Load.Size = UDim2.new(0, 470, 0, 115)

        UICorner_3.Parent = Load

        Bar.Name = "Bar"
        Bar.Parent = Load
        Bar.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
        Bar.Position = UDim2.new(0, 15, 0, 80)
        Bar.Size = UDim2.new(0, 440, 0, 15)

        UICorner_4.CornerRadius = UDim.new(0, 5)
        UICorner_4.Parent = Bar

        BAR1.Name = "BAR1"
        BAR1.Parent = Bar
        BAR1.BackgroundColor3 = Color3.fromRGB(212, 0, 255)
        BAR1.Size = UDim2.new(0, 0, 0, 15)

        UICorner_5.CornerRadius = UDim.new(0, 5)
        UICorner_5.Parent = BAR1

        TextLabel.Parent = Load
        TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextLabel.BackgroundTransparency = 1.000
        TextLabel.Position = UDim2.new(0.0319148935, 0, 0.173913032, 0)
        TextLabel.Size = UDim2.new(0, 440, 0, 25)
        TextLabel.Font = Enum.Font.GothamSemibold
        TextLabel.Text = "Loading"
        TextLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
        TextLabel.TextSize = 16.000
        spawn(function()
            for i = 1,5 do 
                wait(0.5)
                TextLabel.Text = "Loading."
                wait(0.5) 
                TextLabel.Text = "Loading.."
                wait(0.5)
                TextLabel.Text = "Loading..."
            end
        end)

        Top.Name = "Top"
        Top.Parent = Main
        Top.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        Top.Size = UDim2.new(0, 500, 0, 30)

        UICorner_6.Parent = Top

        TextLabel_2.Parent = Top
        TextLabel_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextLabel_2.BackgroundTransparency = 1.000
        TextLabel_2.Position = UDim2.new(0.0299999993, 0, 0, 0)
        TextLabel_2.Size = UDim2.new(0, 61, 0, 30)
        TextLabel_2.Font = Enum.Font.GothamSemibold
        TextLabel_2.Text = "EDOG"
        TextLabel_2.TextColor3 = Color3.fromRGB(225, 225, 225)
        TextLabel_2.TextSize = 17.000

        TextLabel_3.Parent = Top
        TextLabel_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextLabel_3.BackgroundTransparency = 1.000
        TextLabel_3.Position = UDim2.new(0.151999995, 0, 0, 0)
        TextLabel_3.Size = UDim2.new(0, 61, 0, 30)
        TextLabel_3.Font = Enum.Font.GothamSemibold
        TextLabel_3.Text = "HUB"
        TextLabel_3.TextColor3 = Color3.fromRGB(212, 0, 255)
        TextLabel_3.TextSize = 17.000
        TextLabel_3.TextXAlignment = Enum.TextXAlignment.Left
        
        BAR1:TweenSize(UDim2.new(0,440,0,15),"Out","Linear",5,true)
        wait(5)
        Main:TweenSize(UDim2.new(0,0,0,0),"Out","Quad",0.4,true)
        wait(0.4)
        
        do 
            local Load = game.CoreGui:FindFirstChild("Loading")
            if Load then
                Load:Destroy()
            end
        end
    end
    loading()

    if string.lower(game:GetService("RbxAnalyticsService"):GetClientId()) == game:GetService("RbxAnalyticsService"):GetClientId() then
        local ScreenGui = Instance.new("ScreenGui")
        local ImageButton = Instance.new("ImageButton")

        ScreenGui.Parent = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

        ImageButton.Parent = ScreenGui
        ImageButton.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
        ImageButton.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
        ImageButton.Size = UDim2.new(0, 50, 0, 50)
        ImageButton.Image = "rbxassetid://10123314587"
        ImageButton.MouseButton1Down:connect(function()
            game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
            game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
        end)
    end

    local win = library:AddWindow("Edog")

    local MainTab = win:AddTab("Main")
    local Main1 = MainTab:AddPage()
    local Main2 = MainTab:AddPage()

    Main1:AddSeperator("Welcome to Hub")

    Main1:AddLabel("Game : King Legacy")

    local Time = Main1:AddLabel("Server Time")

    function UpdateTime()
        local GameTime = math.floor(workspace.DistributedGameTime+0.5)
        local Hour = math.floor(GameTime/(60^2))%24
        local Minute = math.floor(GameTime/(60^1))%60
        local Second = math.floor(GameTime/(60^0))%60
        Time:Set("Server Time :".." H "..Hour.." M : "..Minute.." S : "..Second)
    end

    spawn(function()
        while true do
            UpdateTime()
            wait()
        end
    end)
    local Time1 = Main1:AddLabel("N/A")
    Time1:Set("Date : "..os.date("%d ")..os.date("%A ")..os.date("%B ")..os.date("%Y"))
    Main1:AddSeperator("Main")

    local SaveSettings = {
        ["Main"] = {
            ["Autofarm"] = false,
            ['Autonewworld'] = false,
            ["Random Fruit"] = false,
            ["Auto Sea King"] = false,
            ["CollectChest"] = false,
            ["HopServer"] = false,
            ["Auto Seber"] = false,
            ["Auto Seber Hop"] = false,
            ["Auto GhostShip"] = false,
            ["Auto GhostShip Hop"] = false,
            ["Auto Eama Hop"] = false,
            ["Auto Eama"] = false,
            ["Auto Bisento"] = false,
            ["Auto Anubis Axe"] = false,
            ["Auto Adventure Knife"] = false,
            ["Auto BigMom"] = false,
            ["Auto Sunken Blade"] = false,
            ["Auto Koko Sword"] = false,
        },
        ['Mode'] = {
            ["Mode"] = 3,
            ["Distance"] = 5,
        },
        ['Players'] = {
            ['All Players'] = false,
        },
        ["Stats"] = {
            ["Melee"] = false,
            ["MeleeCap"] = 4250,
            ["Defense"] = false,
            ["DefenseCap"] = 4250,
            ["Sword"] = false,
            ["SwordCap"] = 4250,
            ["PowerFruit"] = false,
            ["PowerFruitCap"] = 4250,
        },
        ["Main2"] = {
            ["SelectToolWeapon"] = "N/A",
            ["SelectMoney"] = "N/A",
        },
        ['Raid'] = {
            ["SelectRaid"] = "N/A",
            ["Start"] = false,
        },
        ['H'] = {
            ["Health"] = 60,
        },
        ["MISC"] = {
            ["Geppo Inf"] = false,
        },
        ["Settings"] = {
            ["SkilZ"] = true,
            ["SkilX"] = true,
            ["SkilC"] = true,
            ["SkilV"] = true,
            ["HAKI"] = true,
        },
    }
    function Load()
        if readfile and writefile and isfile and isfolder then
            if isfolder("Zenper Hub") == false then
                makefolder("Zenper Hub")
            end
            if isfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json") == false then
                writefile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(SaveSettings))
            else
                local Decode = game:GetService("HttpService"):JSONDecode(readfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json"))
                for i,v in pairs(Decode) do
                    SaveSettings[i] = v
                end
            end
        else
            warn("Failed Load")
            return false
        end
    end
    function Save()
        if readfile and writefile and isfile then
            if isfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json") == false then
                Load()
            else
                local Decode = game:GetService("HttpService"):JSONDecode(readfile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json"))
                local Array = {}
                for i,v in pairs(SaveSettings) do
                    Array[i] = v
                end
                writefile("/Zenper Hub/King Legacy-" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(Array))
            end
        else
            warn("Failed Save")
            return false
        end
    end
    Load()
    Save()
    local placeId = game.PlaceId
    local plr = game.Players.LocalPlayer
    local VirtualUser = game:GetService('VirtualUser')
    if placeId == 4520749081 then
        OldWorld = true
    elseif placeId == 6381829480 then
        NewWorld = true
    elseif placeId == 5931540094 then
        Raids = true
    else
        game.Players.LocalPlayer:Kick("รันผิดเกมป่าว")
    end
    local RunService = game:GetService("RunService")
    function antiSit()
    if game.Players.LocalPlayer.Character.Humanoid:GetState() == Enum.HumanoidStateType.Seated then 
    game.Players.LocalPlayer.Character.Humanoid.Jump = true
    end
    end

    Main1:AddToggle("Auto Farm Level",SaveSettings["Main"]["Autofarm"],function(value)
        SaveSettings["Main"]["Autofarm"] = value
        Save()
    end)

    coroutine.wrap(function()
        game:getService("RunService"):UnbindFromRenderStep("noclOppl")
            game:getService("RunService"):BindToRenderStep("noclOppl",0,function()
            if SaveSettings["Main"]["Autofarm"] then
                pcall(function()
                    for i2,v in pairs(plr.PlayerGui:GetChildren()) do
                        if string.find(v.Name,"QuestLvl") or string.find(v.Name,"SwordShop") then 
                        v.Dialogue.Accept.Position = UDim2.new(0, -800 ,0, -700)
                        v.Dialogue.Accept.Size = UDim2.new(5000, 5000, 5000, 5000)
                        v.Dialogue.Accept.BackgroundTransparency = 1
                        v.Dialogue.Accept.ImageTransparency = 1
                        click()
                    end
                end
            end)
            end
            
        end)
    end)()
    spawn(function()
        while wait(.1) do
            if SaveSettings["Mode"]["Mode"] == 1 then
                FARM = CFrame.new(0, 0, SaveSettings["Mode"]["Distance"])
            elseif SaveSettings["Mode"]["Mode"] == 2 then
                FARM = CFrame.Angles(math.rad(90),0,0) * CFrame.new(0, 0, SaveSettings["Mode"]["Distance"])
            elseif SaveSettings["Mode"]["Mode"] == 3 then
                FARM = CFrame.Angles(math.rad(-90),0,0) * CFrame.new(0, 0, SaveSettings["Mode"]["Distance"])
            end
        end
    end)

    spawn(function ()
        setfflag("HumanoidParallelRemoveNoPhysics", "False")
        setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
        game:GetService("RunService").Stepped:Connect(function()
            pcall(function()
            if SaveSettings["Main"]["Autofarm"] or SaveSettings["Main"]["Auto Sea King"] or SaveSettings["Main"]["CollectChest"] or SaveSettings["Main"]["Auto GhostShip"] then
                local plr = game:GetService("Players").LocalPlayer
                local char = plr.Character or plr.CharacterAdded:Wait()
                char.Humanoid:ChangeState(11)
            end
        end)
    end)
    end)
    local function click()
        game:GetService'VirtualUser':Button1Down(Vector2.new(1,1))
        game:GetService'VirtualUser':Button1Up(Vector2.new(1,1))
    end
    function CheckQuest()
        QuestTable = {}
        LevelTable = {}
        local MyLevel = game.Players.LocalPlayer.PlayerStats.lvl.Value
        for i,v in pairs(game:GetService("Workspace").AllNPC:GetChildren()) do 
            if string.find(v.Name,"QuestLvl") then
                table.insert(QuestTable,v.Name)
            end
        end
        for i,v in pairs(game:GetService("ReplicatedStorage").MAP:GetChildren()) do 
            if string.find(v.Name,"QuestLvl") then
                table.insert(QuestTable,v.Name)
            end
        end
        for i,v in pairs(QuestTable) do
            LVL = v:split("QuestLvl")[2]
            if MyLevel >= tonumber(LVL) then
                table.insert(LevelTable,LVL)
            end
        end
        return math.max(table.unpack(LevelTable))
    end


    local mtg = getrawmetatable(game)
    setreadonly(mtg,false)
    local Old = mtg.__newindex
    mtg.__newindex = newcclosure(function(self,a,b)
        if self == game.Players.LocalPlayer.Character.HumanoidRootPart and a == "CFrame" and not checkcaller() then
            return nil 
        end
        return Old(self,a,b)
    end
    )
    setreadonly(mtg,true)

    function WTF(x,y,z)
        if x and y and z then
            if not game:GetService("Workspace").AllNPC:FindFirstChild("QuestLvl"..CheckQuest()) then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("ReplicatedStorage").MAP["QuestLvl"..CheckQuest()].HumanoidRootPart.CFrame * CFrame.new(0,0,-2.5)
            else 
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").AllNPC["QuestLvl"..CheckQuest()].HumanoidRootPart.CFrame * CFrame.new(0,0,-2.5)
            end
            VirtualUser:CaptureController()
            VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
            wait(1)
            for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                if v.Name == "Dialogue" then
                    v.Accept.Size = UDim2.new(100,100,100,100)
                    v.Accept.Position = UDim2.new(-5,0,-9,0)
                    v.Accept.ImageTransparency = 1
                    VirtualUser:CaptureController()
                    VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                end
            end
        end
    end

    function EquipWeapon(ToolSe)
        if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
            tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
            wait()
            game.Players.LocalPlayer.Character.Humanoid:EquipTool(tool)
        end
    end


    spawn(function()
        while wait() do
            if SaveSettings["Main"]["Autofarm"] then
                pcall(function()
                    game.Players.LocalPlayer.Character.Humanoid.Sit = false
                    if game.Players.LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == false then
                        if not game:GetService("Workspace").AllNPC:FindFirstChild("QuestLvl"..CheckQuest()) then
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("ReplicatedStorage").MAP["QuestLvl"..CheckQuest()].HumanoidRootPart.CFrame * CFrame.new(0,0,-2.5)
                        else 
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").AllNPC["QuestLvl"..CheckQuest()].HumanoidRootPart.CFrame * CFrame.new(0,0,-2.5)
                        end
                        VirtualUser:CaptureController()
                        VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                        wait(1)
                        for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                            if v.Name == "Dialogue" then
                                v.Accept.Size = UDim2.new(100,100,100,100)
                                v.Accept.Position = UDim2.new(-5,0,-9,0)
                                v.Accept.ImageTransparency = 1
                                VirtualUser:CaptureController()
                                VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                            end
                        end
                    elseif game.Players.LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == true then
                        Ms = string.sub(game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text,5,#game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text)
                        if game:GetService("Workspace").Monster.Mon:FindFirstChild(Ms) or game:GetService("Workspace").Monster.Boss:FindFirstChild(Ms) then
                            for _,v in pairs(game:GetService("Workspace").Monster:GetDescendants()) do
                                if v.Name == Ms and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat wait()
                                        EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                        VirtualUser:CaptureController()
                                        VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                                        autoskillheehee()
                                    until not v.Parent or v.Humanoid.Health <= 0 or not SaveSettings["Main"]["Autofarm"] or game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == false
                                end
                            end
                        else
                            if not game:GetService("Workspace").AllNPC:FindFirstChild("QuestLvl"..CheckQuest()) then
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("ReplicatedStorage").MAP["QuestLvl"..CheckQuest()].HumanoidRootPart.CFrame * CFrame.new(0,300,0)
                            else 
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").AllNPC["QuestLvl"..CheckQuest()].HumanoidRootPart.CFrame * CFrame.new(0,300,0)
                            end
                        end
                    else
                        print("111")
                        WTF(true,true,true)
                    end
                end
                )
            end
        end
    end
    )
    Main1:AddToggle("Auto New World",SaveSettings["Main"]["Autonewworld"],function(value)
        SaveSettings["Main"]["Autonewworld"] = value
        Save()
    end)
    spawn(function ()
        while true do
            if SaveSettings["Main"]["Autonewworld"] then
                if plr.PlayerStats.lvl.Value >= 2350 and game.PlaceId == 4520749081 then
                    local ts = game:GetService("TeleportService") local p = game.Players.LocalPlayer ts:Teleport(6381829480, p) 
                end
            end
            wait()
        end
    end)
    Main1:AddSeperator("Random Fruit")
    Main1:AddDropdown("Select Bile / Gem",{"Beil","Gem"}, function(Value)
        SaveSettings["Main2"]["SelectMoney"] = Value
        Save()
    end)
    Main1:AddToggle("Auto Rendom Fruit",SaveSettings["Main"]["Random Fruit"],function(value)
        SaveSettings["Main"]["Random Fruit"] = value
        Save()
    end)
    spawn(function()
        while wait() do
            if SaveSettings["Main"]["Random Fruit"] then
                pcall(function()
                    if SaveSettings["Main2"]["SelectMoney"] == "Beil" then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2361.66528, 57.5571632, 266.519135, 0.998433173, 1.22706521e-08, 0.0559570901, -1.50126596e-08, 1, 4.85816187e-08, -0.0559570901, -4.93455623e-08, 0.998433173)
                        wait(1)
                        game:GetService'VirtualUser':Button1Down(Vector2.new(1,1))
                        game:GetService'VirtualUser':Button1Up(Vector2.new(1,1))
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Beli.Size = UDim2.new(100,100,100,100)
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Beli.Position = UDim2.new(-5,0,-9,0)
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Beli.ImageTransparency = 1
                        VirtualUser:CaptureController()
                        VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                    elseif SaveSettings["Main2"]["SelectMoney"] == "Gem" then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2361.66528, 57.5571632, 266.519135, 0.998433173, 1.22706521e-08, 0.0559570901, -1.50126596e-08, 1, 4.85816187e-08, -0.0559570901, -4.93455623e-08, 0.998433173)
                        wait(1)
                        game:GetService'VirtualUser':Button1Down(Vector2.new(1,1))
                        game:GetService'VirtualUser':Button1Up(Vector2.new(1,1))
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Gem.Size = UDim2.new(100,100,100,100)
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Gem.Position = UDim2.new(-5,0,-9,0)
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Gem.ImageTransparency = 1
                        VirtualUser:CaptureController()
                        VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                    else
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2361.66528, 57.5571632, 266.519135, 0.998433173, 1.22706521e-08, 0.0559570901, -1.50126596e-08, 1, 4.85816187e-08, -0.0559570901, -4.93455623e-08, 0.998433173)
                        wait(1)
                        game:GetService'VirtualUser':Button1Down(Vector2.new(1,1))
                        game:GetService'VirtualUser':Button1Up(Vector2.new(1,1))
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Beli.Size = UDim2.new(100,100,100,100)
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Beli.Position = UDim2.new(-5,0,-9,0)
                        game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Beli.ImageTransparency = 1
                        VirtualUser:CaptureController()
                        VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                    end
                end)
            end
        end
    end)
    local Weapon = {}
    for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
        if v:IsA('Tool') then
            table.insert(Weapon,v.Name)
        end
    end
    local SelectedWeapon = Main2:AddDropdown("Select Weapon",Weapon,function(value)
        SaveSettings["Main2"]["SelectToolWeapon"] = value
        Save()
    end)

    Main2:AddButton("Reset Weapon",function()
        SelectedWeapon:Clear()
        for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
            if v:IsA('Tool') then
                table.insert(Weapon,v.Name)
                SelectedWeapon:Add(v)
            end
        end
    end)

    Main2:AddSlider('Auto Farm Modes', 1, 3, SaveSettings["Mode"]["Mode"], function(value)
        SaveSettings["Mode"]["Mode"] = value
        Save()
    end)
    Main2:AddSlider('Distance', 1, 100, SaveSettings["Mode"]["Distance"], function(value)
        SaveSettings["Mode"]["Distance"] = value
        Save()
    end)
    ----------------------------------------------

    local MainTab = win:AddTab("items & Quest")
    local Main3 = MainTab:AddPage()
    local Main4 = MainTab:AddPage()
    Main3:AddToggle("Auto Seber",SaveSettings["Main"]["Auto Seber"], function(vu)
        SaveSettings["Main"]["Auto Seber"] = vu
        Save()
    end)
    Main4:AddToggle("Auto Seber Hop",SaveSettings["Main"]["Auto Seber Hop"], function(vu)
        SaveSettings["Main"]["Auto Seber Hop"] = vu
        Save()
    end)
    game:GetService("RunService").RenderStepped:Connect(function()
        if SaveSettings["Main"]["Auto Seber"] then
          game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
    spawn(function()
        while wait() do
            if SaveSettings["Main"]["Auto Seber"] then
                pcall(function()
                    if game:GetService("Workspace").Monster.Boss:FindFirstChild("Expert Swordman [Lv. 3000]") or game:GetService("ReplicatedStorage").MOB:FindFirstChild("Expert Swordman [Lv. 3000]") then
                        for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                            if v.Name == "Expert Swordman [Lv. 3000]" and v.Humanoid.Health > 0 then
                                repeat wait()
                                    pcall(function()
                                        EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                        game:GetService'VirtualUser':Button1Down(Vector2.new(1,1))
                                        game:GetService'VirtualUser':Button1Up(Vector2.new(1,1))
                                        autoskillheehee()
                                    end)
                                until not SaveSettings["Main"]["Auto Seber"] or v.Humanoid.Health == 0
                            end
                        end
                    else
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9725.2412109375, 36.836204528809, -3905.3288574219)
                    end
                end)
            end
        end
        wait()
    end)
    spawn(function()
        while wait() do
            if not game:GetService("Workspace").Monster.Boss:FindFirstChild("Expert Swordman [Lv. 3000]") then
                if SaveSettings["Main"]["Auto Seber Hop"] then
                    print("HOP !!")
                    local module = loadstring(game:HttpGet"https://raw.githubusercontent.com/LeoKholYt/roblox/main/lk_serverhop.lua")()
                    module:Teleport(game.PlaceId)
                end
            end
        end
    end)
    Main3:AddToggle("Auto Sea King",SaveSettings["Main"]["Auto Sea King"], function(vu)
        SaveSettings["Main"]["Auto Sea King"] = vu
        SaveSettings["Main"]["CollectChest"] = vu
        Save()
    end)
    Main4:AddToggle("Auto Sea King Hop",SaveSettings["Main"]["HopServer"], function(vu)
        SaveSettings["Main"]["HopServer"] = vu
        Save()
    end)


    local plr = game.Players.LocalPlayer
    local function LegacyIsland()
        if game:GetService("Workspace").Island:FindFirstChild("Legacy Island1") then
            return {true,"1"}
        elseif game:GetService("Workspace").Island:FindFirstChild("Legacy Island2") then
            return {true,"2"}
        elseif game:GetService("Workspace").Island:FindFirstChild("Legacy Island3") then
            return {true,"3"}
        elseif game:GetService("Workspace").Island:FindFirstChild("Legacy Island4") then
            return {true,"4"}
        elseif game:GetService("Workspace").Island:FindFirstChild("Legacy Island5") then
            return {true,"5"}
        else 
            return {false,"nil"}
        end
    end






    spawn(function()
        while true do
            if SaveSettings["Main"]["Auto Sea King"] then
                if LegacyIsland()[1] == true then
                    pcall(function()
                        if game:GetService("Workspace").SeaMonster:FindFirstChild("SeaKing") then
                            autoskillheehee()
                            spawn(function ()
                                click()
                            end)
                            spawn(function()
                                plr.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").SeaMonster:FindFirstChild("SeaKing") .HumanoidRootPart.CFrame * CFrame.new(0,-5,0) 
                                EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"]) 
                            end)
                        else
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Island["Legacy Island" .. LegacyIsland()[2]].ChestSpawner.CFrame
                        end
                    end)
                else
                    if SaveSettings["Main"]["HopServer"] then
                        local module = loadstring(game:HttpGet"https://raw.githubusercontent.com/LeoKholYt/roblox/main/lk_serverhop.lua")()
                        module:Teleport(game.PlaceId)
                    end
                end
            end
            wait()
        end
    end)
    spawn(function()
        while true do
            if SaveSettings["Main"]["CollectChest"] then
                if LegacyIsland()[1] == true then
                    pcall(function()
                        if game:GetService("Workspace").SeaMonster:FindFirstChild("SeaKing").Humanoid.Health <= 0 then
                            SaveSettings["Main"]["Auto Sea King"] = false
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Island["Legacy Island" .. LegacyIsland()[2]].ChestSpawner.CFrame
                        end
                    end)
                end
            end
            wait(1)
        end
    end)
    Main3:AddToggle("Auto Ghost Ship",SaveSettings["Main"]["Auto GhostShip"], function(vu)
        SaveSettings["Main"]["Auto GhostShip"] = vu
        Save()
    end)
    Main4:AddToggle("Auto Ghost Ship Hop",SaveSettings["Main"]["Auto GhostShip Hop"], function(vu)
        SaveSettings["Main"]["Auto GhostShip Hop"] = vu
        Save()
    end)

    spawn(function()
        while true do
            if SaveSettings["Main"]["Auto GhostShip"] then
                if game:GetService("Workspace"):FindFirstChild("Chest1") then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("Chest1").RootPart.CFrame
                    end)
                end
                if game:GetService("Workspace"):FindFirstChild("Chest2") then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("Chest2").RootPart.CFrame
                    end)
                end
                if game:GetService("Workspace"):FindFirstChild("Chest3") then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("Chest3").RootPart.CFrame
                    end)
                end
                if game:GetService("Workspace"):FindFirstChild("Chest4") then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("Chest4").RootPart.CFrame
                    end)
                end
                if game:GetService("Workspace"):FindFirstChild("Chest5") then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("Chest5").RootPart.CFrame
                    end)
                end
                if game:GetService("Workspace"):FindFirstChild("Chest6") then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("Chest1").RootPart.CFrame
                    end)
                end
                if game:GetService("Workspace"):FindFirstChild("Chest7") then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("Chest2").RootPart.CFrame
                    end)
                end
            end
            wait()
        end
    end)
    spawn(function()
        while wait() do
            if SaveSettings["Main"]["Auto GhostShip"] then
                if game:GetService("Workspace").GhostMonster:FindFirstChild("Ghost Ship") then
                    pcall(function ()
                        autoskillheehee()
                            spawn(function ()
                            click()
                            end)
                        spawn(function()
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").GhostMonster["Ghost Ship"].HumanoidRootPart.CFrame
                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                        end)
                    end)
                else
                    if SaveSettings["Main"]["Auto GhostShip Hop"] then
                        if not game:GetService("Workspace"):FindFirstChild("Chest1") then
                            local module = loadstring(game:HttpGet"https://raw.githubusercontent.com/LeoKholYt/roblox/main/lk_serverhop.lua")()
                            module:Teleport(game.PlaceId)
                        end
                    end
                end
            end
        end
    end)
    Main3:AddToggle("Auto Eama",SaveSettings["Main"]["Auto Eama"], function(vu)
        SaveSettings["Main"]["Auto Eama"] = vu
        Save()
    end)
    Main4:AddToggle("Auto Eama Hop",SaveSettings["Main"]["Auto Eama Hop"], function(vu)
        SaveSettings["Main"]["Auto Eama Hop"] = vu
        Save()
    end)

    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Eama"] then
                    if game:GetService("Workspace").Monster.Boss:FindFirstChild('King Samurai [Lv. 3500]') then
                        for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                            if v.Name == 'King Samurai [Lv. 3500]' then
                                if v:FindFirstChild("Humanoid") or v.Humanoid.Health > 0 then
                                    repeat wait()
                                        autoskillheehee()
                                        spawn(function()
                                            click()
                                        end)
                                        spawn(function()
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        end)
                                    until not v.Parent or v.Humanoid.Health <= 0 or not SaveSettings["Main"]["Auto Eama"] or not v:FindFirstChild("Humanoid")
                                end
                            end
                        end
                    else
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1484.14795, 354.849396, 148.316101, 0.0326676071, -2.0748903e-08, -0.9994663, -5.45792105e-08, 1, -2.25439081e-08, 0.9994663, 5.52865345e-08, 0.0326676071)
                    end
                end
            end)
        end
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Eama Hop"] then
                    for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1484.14795, 354.849396, 148.316101, 0.0326676071, -2.0748903e-08, -0.9994663, -5.45792105e-08, 1, -2.25439081e-08, 0.9994663, 5.52865345e-08, 0.0326676071)
                        wait(1)
                        if SaveSettings["Main"]["Auto Eama Hop"] and not game:GetService("Workspace").Monster.Boss:FindFirstChild("King Samurai [Lv. 3500]") or not v:FindFirstChild("Humanoid") then
                            local module = loadstring(game:HttpGet"https://raw.githubusercontent.com/LeoKholYt/roblox/main/lk_serverhop.lua")()
                            module:Teleport(game.PlaceId)
                            print('Hop !!!')
                        end
                    end
                end
            end)
        end
    end)
    game:GetService("RunService").RenderStepped:Connect(function()
        if SaveSettings["Main"]["Auto Eama"] then
          game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
    Main3:AddToggle("Auto Bisento",SaveSettings["Main"]["Auto Bisento"], function(vu)
        SaveSettings["Main"]["Auto Bisento"] = vu
        Save()
    end)
    game:GetService("RunService").RenderStepped:Connect(function()
        if SaveSettings["Main"]["Auto Bisento"] then
            game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Bisento"] then
                    if game:GetService("Workspace").Monster.Mon:FindFirstChild('Quake Woman [Lv. 1925]') or game:GetService("Workspace").Monster.Boss:FindFirstChild('Quake Woman [Lv. 1925]') then
                        for i, v in pairs(game:GetService("Workspace").Monster:GetDescendants()) do
                            if v.Name == 'Quake Woman [Lv. 1925]' then
                                repeat wait()
                                    if v:FindFirstChild("Humanoid") or v.Humanoid.Health > 0 then
                                        autoskillheehee()
                                        spawn(function()
                                            click()
                                        end)
                                        spawn(function()
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        end) 
                                    end
                                until v.Humanoid.Health <= 0 or SaveSettings["Main"]["Auto Bisento"] == false
                            end
                        end
                    else
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6371.06396484375, 3.0651307106018066, 950.4378051757812)
                    end
                end
            end)
        end
    end)
    Main4:AddToggle("Auto Anubis Axe",SaveSettings["Main"]["Auto Anubis Axe"], function(vu)
        SaveSettings["Main"]["Auto Anubis Axe"] = vu
        Save()
    end)
    game:GetService("RunService").RenderStepped:Connect(function()
        if SaveSettings["Main"]["Auto Anubis Axe"] or SaveSettings["Main"]["Auto Adventure Knife"] then
            game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Anubis Axe"] then
                    if game:GetService("Workspace").Monster.Mon:FindFirstChild('Anubis [Lv.3150]') or game:GetService("Workspace").Monster.Boss:FindFirstChild('Anubis [Lv.3150]') then
                        for i, v in pairs(game:GetService("Workspace").Monster:GetDescendants()) do
                            if v.Name == 'Anubis [Lv.3150]' then
                                repeat wait()
                                    if v:FindFirstChild("Humanoid") or v.Humanoid.Health > 0 then
                                        autoskillheehee()
                                        spawn(function()
                                            click()
                                        end)
                                        spawn(function()
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        end) 
                                    end
                                until v.Humanoid.Health <= 0 or SaveSettings["Main"]["Auto Anubis Axe"] == false
                            end
                        end
                    else
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9534.728515625, 132.2279510498, 1017.6542358398)
                    end
                end
            end)
        end
    end)
    Main3:AddToggle("Auto Adventure Knife",SaveSettings["Main"]["Auto Adventure Knife"], function(vu)
        SaveSettings["Main"]["Auto Adventure Knife"] = vu
        Save()
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Adventure Knife"] then
                    if game:GetService("Workspace").Monster.Mon:FindFirstChild('Flame User [Lv.3200]') or game:GetService("Workspace").Monster.Boss:FindFirstChild('Flame User [Lv.3200]') then
                        for i, v in pairs(game:GetService("Workspace").Monster:GetDescendants()) do
                            if v.Name == 'Flame User [Lv.3200]' then
                                repeat wait()
                                    if v:FindFirstChild("Humanoid") or v.Humanoid.Health > 0 then
                                        autoskillheehee()
                                        spawn(function()
                                            click()
                                        end)
                                        spawn(function()
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        end) 
                                    end
                                until v.Humanoid.Health <= 0 or SaveSettings["Main"]["Auto Adventure Knife"] == false
                            end
                        end
                    else
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9959.751953125, 211.72598266602, 1910.8186035156)
                    end
                end
            end)
        end
    end)
    Main4:AddToggle("Auto Kaido",SaveSettings["Main"]["Auto Kaido"], function(vu)
        SaveSettings["Main"]["Auto Kaido"] = vu
        Save()
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Kaido"] then
                    if not game.Players.LocalPlayer.Backpack:FindFirstChild("DragonGem") or not game.Players.LocalPlayer.Character:FindFirstChild("DragonGem") and not game:GetService("Workspace").Monster.Boss:FindFirstChild('Dragon [Lv. 5000]') then
                        if game:GetService("Workspace").Monster.Boss:FindFirstChild('Elite Skeleton [Lv. 3100]') then
                            for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                if v.Name == "Elite Skeleton [Lv. 3100]" and v.Humanoid.Health > 0 then
                                    repeat wait()
                                        autoskillheehee()
                                        spawn(function()
                                            click()
                                        end)
                                        EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                        game:GetService('VirtualUser'):CaptureController()
                                        game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                    until SaveSettings["Main"]["Auto Kaido"] == false or v.Humanoid.Health <= 0
                                end
                            end
                        else
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1378.60546875, 139.00987243652, 7331.2514648438)
                        end
                        if game:GetService("Workspace").Monster.Boss:FindFirstChild('Dragon [Lv. 5000]') then
                            if game:GetService("Workspace").Monster.Boss:FindFirstChild('Dragon [Lv. 5000]') then
                                for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                    if v.Name == "Dragon [Lv. 5000]" and v.Humanoid.Health > 0 then
                                        repeat wait()
                                            autoskillheehee()
                                            spawn(function()
                                                click()
                                            end)
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                        until SaveSettings["Main"]["Auto Kaido"] == false or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1411.7918701171875, 461.6090393066406, 7639.1748046875)
                            end
                        end
                    else
                        EquipWeapon("DragonGem")
                        game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1294.99878, 462.692261, 7367.66113, 0.981259882, 8.6877499e-08, 0.192690104, -8.79254216e-08, 1, -3.11276405e-09, -0.192690104, -1.38879104e-08, 0.981259882)
                    end 
                end
            end)
        end
    end)
    game:GetService("RunService").RenderStepped:Connect(function()
        if SaveSettings["Main"]["Auto Kaido"] or SaveSettings["Main"]["Auto BigMom"] then
            game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
    Main3:AddToggle("Auto Big Mom",SaveSettings["Main"]["Auto BigMom"], function(vu)
        SaveSettings["Main"]["Auto BigMom"] = vu
        Save()
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto BigMom"] then
                    if not game.Players.LocalPlayer.Backpack:FindFirstChild("Gem") or not game.Players.LocalPlayer.Character:FindFirstChild("Gem") and not game:GetService("Workspace").Monster.Boss:FindFirstChild('Monster [Lv. 2500]') then
                        if game:GetService("Workspace").Monster.Boss:FindFirstChild('Shadow Master [Lv. 1600]') then
                            for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                if v.Name == "Shadow Master [Lv. 1600]" and v.Humanoid.Health > 0 then
                                    repeat wait()
                                        autoskillheehee()
                                        spawn(function()
                                            click()
                                        end)
                                        EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                        game:GetService('VirtualUser'):CaptureController()
                                        game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                    until SaveSettings["Main"]["Auto BigMom"] == false or v.Humanoid.Health <= 0
                                end
                            end
                        else
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1339.34009, 120.819733, 7206.00586, 0.855517566, 1.29821986e-09, -0.517773807, 5.52668078e-10, 1, 3.42048434e-09, 0.517773807, -3.21244142e-09, 0.855517566)
                        end
                    elseif game:GetService("Workspace").Monster.Boss:FindFirstChild('Monster [Lv. 2500]') then
                        if game:GetService("Workspace").Monster.Boss:FindFirstChild('Monster [Lv. 2500]') then
                            for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                if v.Name == "Monster [Lv. 2500]" and v.Humanoid.Health > 0 then
                                    repeat wait()
                                        autoskillheehee()
                                        spawn(function()
                                            click()
                                        end)
                                        EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                        game:GetService('VirtualUser'):CaptureController()
                                        game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                    until SaveSettings["Main"]["Auto BigMom"] == false or v.Humanoid.Health <= 0
                                end
                            end
                        else
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1195.203, 87.360672, 7446.87451, -0.374030232, -0.544412017, 0.750810862, 0.0333943404, 0.801141441, 0.597542644, -0.926815093, 0.248571843, -0.281470835)
                        end
                    else
                        EquipWeapon("Gem")
                        game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1258.09558, 16.0895634, 7333.875, 0.925694406, -3.08031396e-08, -0.378272206, 6.38590336e-08, 1, 7.48424256e-08, 0.378272206, -9.34373148e-08, 0.925694406)
                    end 
                end
            end)
        end
    end)
    Main4:AddToggle("Auto Sunken Blade",SaveSettings["Main"]["Auto Sunken Blade"], function(vu)
        SaveSettings["Main"]["Auto Sunken Blade"] = vu
        Save()
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Sunken Blade"] then
                    if game:GetService("Workspace").Monster.Boss:FindFirstChild('Sunken Vessel [Lv.3225]') then
                        for _,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                            if v.Name == 'Sunken Vessel [Lv.3225]' then
                                repeat wait()
                                    autoskillheehee()
                                    spawn(function()
                                        click()
                                    end)
                                    EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                    game:GetService('VirtualUser'):CaptureController()
                                    game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                until SaveSettings["Main"]["Auto Sunken Blade"] == false or v.Humanoid.Health <= 0
                            end
                        end
                    else
                        game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6195.27002, 121.842346, 8310.65039, -0.674651802, 0.268866062, -0.687427044, -0.000963829458, 0.93097955, 0.365070075, 0.738135457, 0.246957749, -0.627827883)
                    end
                end
            end)
        end
    end)
    game:GetService("RunService").RenderStepped:Connect(function()
        if SaveSettings["Main"]["Auto Sunken Blade"] then
            game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
    Main3:AddToggle("Auto Cookie Sword",SaveSettings["Main"]["Auto Cookie Sword"], function(vu)
        SaveSettings["Main"]["Auto Cookie Sword"] = vu
        Save()
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Cookie Sword"] then
                    if game:GetService("Workspace").Monster.Boss:FindFirstChild('Biscuit Man [Lv.3250]') then
                        for _,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                            if v.Name == 'Biscuit Man [Lv.3250]' then
                                repeat wait()
                                    autoskillheehee()
                                    spawn(function()
                                        click()
                                    end)
                                    EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                    game:GetService('VirtualUser'):CaptureController()
                                    game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                until SaveSettings["Main"]["Auto Cookie Sword"] == false or v.Humanoid.Health <= 0
                            end
                        end
                    else
                        game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(5751.75977, 260.669098, 8931.26562, -0.937544644, 0.0968098119, -0.334122628, 0.000299910025, 0.960719645, 0.277520597, 0.347864896, 0.260087729, -0.900746584)
                    end
                end
            end)
        end
    end)
    game:GetService("RunService").RenderStepped:Connect(function()
        if SaveSettings["Main"]["Auto Cookie Sword"] then
            game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
    end)
    Main3:AddToggle("Auto Koko Sword",SaveSettings["Main"]["Auto Koko Sword"], function(vu)
        SaveSettings["Main"]["Auto Koko Sword"] = vu
        Save()
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings["Main"]["Auto Koko Sword"] then
                    if game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == false then
                        game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6910.14697, 56.5788574, 8153.56787, 0.159139976, -2.20316991e-08, -0.98725605, -4.04122886e-08, 1, -2.88303212e-08, 0.98725605, 4.44853328e-08, 0.159139976)
                        wait(1)
                        VirtualUser:CaptureController()
                        VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                        wait(1)
                        for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                            if v.Name == "Dialogue" then
                                v.Accept.Size = UDim2.new(100,100,100,100)
                                v.Accept.Position = UDim2.new(-5,0,-9,0)
                                v.Accept.ImageTransparency = 1
                                VirtualUser:CaptureController()
                                VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                            end
                        end
                    else
                        if game:GetService("Players").localPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text == '0/1 Kappa [Lv. 2950]' then
                            if game:GetService("Workspace").Monster.Boss:FindFirstChild('Kappa [Lv. 2950]') then
                                for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                    if v.Name == 'Kappa [Lv. 2950]' then
                                        repeat wait()
                                            autoskillheehee()
                                            spawn(function()
                                                click()
                                            end)
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                        until SaveSettings["Main"]["Auto Koko Sword"] == false or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2396.61328, 74.2253876, 2015.17456, -0.991864324, -7.99078043e-06, -0.127299592, -1.17403351e-05, 1, 2.87042512e-05, 0.127299592, 2.9965262e-05, -0.991864324)
                            end
                        elseif game:GetService("Players").localPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text == '0/1 Anubis [Lv.3150]' then
                            if game:GetService("Workspace").Monster.Boss:FindFirstChild('Anubis [Lv.3150]') then
                                for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                    if v.Name == 'Anubis [Lv.3150]' then
                                        repeat wait()
                                            autoskillheehee()
                                            spawn(function()
                                                click()
                                            end)
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                        until SaveSettings["Main"]["Auto Koko Sword"] == false or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9525.49609, 14.4560375, 1041.96155, 0.39982149, -2.53500821e-05, -0.916592836, -3.69382207e-07, 1, -2.78179868e-05, 0.916592836, 1.14608065e-05, 0.39982149)
                            end
                        elseif game:GetService("Players").localPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text == '0/1 Flame User [Lv.3200]' then
                            if game:GetService("Workspace").Monster.Boss:FindFirstChild('Flame User [Lv.3200]') then
                                for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                    if v.Name == 'Flame User [Lv.3200]' then
                                        repeat wait()
                                            autoskillheehee()
                                            spawn(function()
                                                click()
                                            end)
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                        until SaveSettings["Main"]["Auto Koko Sword"] == false or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9992.98438, 14.4613342, 1887.48804, -0.767125189, 4.76313424e-08, -0.641497433, -3.20915294e-09, 1, 7.80878651e-08, 0.641497433, 6.19618277e-08, -0.767125189)
                            end
                        elseif game:GetService("Players").localPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text == '0/1 Sunken Vessel [Lv.3225]' then
                            if game:GetService("Workspace").Monster.Boss:FindFirstChild('Sunken Vessel [Lv.3225]') then
                                for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                    if v.Name == 'Sunken Vessel [Lv.3225]' then
                                        repeat wait()
                                            autoskillheehee()
                                            spawn(function()
                                                click()
                                            end)
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                        until SaveSettings["Main"]["Auto Koko Sword"] == false or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6195.27002, 121.842346, 8310.65039, -0.674651802, 0.268866062, -0.687427044, -0.000963829458, 0.93097955, 0.365070075, 0.738135457, 0.246957749, -0.627827883)
                            end
                        elseif game:GetService("Players").localPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text == '0/1 Biscuit Man [Lv.3250]' then
                            if game:GetService("Workspace").Monster.Boss:FindFirstChild('Biscuit Man [Lv.3250]') then
                                for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                    if v.Name == 'Biscuit Man [Lv.3250]' then
                                        repeat wait()
                                            autoskillheehee()
                                            spawn(function()
                                                click()
                                            end)
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                        until SaveSettings["Main"]["Auto Koko Sword"] == false or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(5751.75977, 260.669098, 8931.26562, -0.937544644, 0.0968098119, -0.334122628, 0.000299910025, 0.960719645, 0.277520597, 0.347864896, 0.260087729, -0.900746584)
                            end
                        elseif game:GetService("Players").localPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text == '0/1 Dough Master [Lv.3275]' then
                            if game:GetService("Workspace").Monster.Boss:FindFirstChild('Dough Master [Lv.3275]') then
                                for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                    if v.Name == 'Dough Master [Lv.3275]' then
                                        repeat wait()
                                            autoskillheehee()
                                            spawn(function()
                                                click()
                                            end)
                                            EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * FARM
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):Button1Down(Vector2.new(9999, 9999))
                                        until SaveSettings["Main"]["Auto Koko Sword"] == false or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(30384.8535, 47.5213966, 93514.6719, 0.918531418, -4.65251766e-08, 0.395348072, 5.52475434e-08, 1, -1.06777467e-08, -0.395348072, 3.16498543e-08, 0.918531418)
                            end
                        end
                    end
                end
            end)
        end
    end)

    -------------------------------------

    local MainTab = win:AddTab("Stats")
    local Main5 = MainTab:AddPage()
    local Main6 = MainTab:AddPage()


    Main5:AddToggle("Melee",SaveSettings["Stats"]["Melee"], function(vu)
        SaveSettings["Stats"]["Melee"] = vu
        Save()
    end)
    Main5:AddSlider("Melee Cap",0,4250,SaveSettings["Stats"]["MeleeCap"],function(t)
        SaveSettings["Stats"]["MeleeCap"] = t
        Save()
    end)
    Main5:AddToggle("Defense",SaveSettings["Stats"]["Defense"], function(vu)
        SaveSettings["Stats"]["Defense"] = vu
        Save()
    end)
    Main5:AddSlider("Defense Cap",0,4250,SaveSettings["Stats"]["DefenseCap"],function(t)
        SaveSettings["Stats"]["DefenseCap"] = t
        Save()
    end)
    Main5:AddToggle("Sword",SaveSettings["Stats"]["Sword"], function(vu)
        SaveSettings["Stats"]["Sword"] = vu
        Save()
    end)
    Main5:AddSlider("Sword Cap",0,4250,SaveSettings["Stats"]["SwordCap"],function(t)
        SaveSettings["Stats"]["SwordCap"] = t
        Save()
    end)
    Main5:AddToggle("PowerFruit",SaveSettings["Stats"]["PowerFruit"], function(vu)
        SaveSettings["Stats"]["PowerFruit"] = vu
        Save()
    end)
    Main5:AddSlider("Power Fruit Cap",0,4250,SaveSettings["Stats"]["PowerFruitCap"],function(t)
        SaveSettings["Stats"]["PowerFruitCap"] = t
        Save()
    end)
    Main6:AddSeperator("Stats Player")
    local Melee = Main6:AddLabel("Melee")

    spawn(function() 
        pcall(function()
            while wait() do
                Melee:Set("Melee : "..game:GetService("Players").LocalPlayer.PlayerStats.Melee.Value)
            end
        end)
    end)

    local Defense = Main6:AddLabel("Defense")

    spawn(function() 
        pcall(function()
            while wait() do
                Defense:Set("Defense : "..game:GetService("Players").LocalPlayer.PlayerStats.Defense.Value)
            end
        end)
    end)

    local Sword = Main6:AddLabel("Sword")

    spawn(function() 
        pcall(function()
            while wait() do
                Sword:Set("Sword : "..game:GetService("Players").LocalPlayer.PlayerStats.sword.Value)
            end
        end)
    end)

    local Power_Fruit = Main6:AddLabel("Power Fruit")

    spawn(function() 
        pcall(function()
            while wait() do
                Power_Fruit:Set("Power Fruit : "..game:GetService("Players").LocalPlayer.PlayerStats.DF.Value)
            end
        end)
    end)
    spawn(function()
        while wait() do
            if SaveSettings["Stats"]["Melee"] then
                pcall(function()
                    if tonumber(game.Players.LocalPlayer.PlayerStats.Melee.Value) <= math.floor(SaveSettings["Stats"]["MeleeCap"]) then
                        game.Players.LocalPlayer.PlayerGui.Stats.AddButton.StatsFrame.RemoteEvent:FireServer("Melee",1)
                    end
                end)
            end
            if SaveSettings["Stats"]["Defense"] then
                pcall(function()
                    if tonumber(game.Players.LocalPlayer.PlayerStats.Defense.Value) <= math.floor(SaveSettings["Stats"]["DefenseCap"]) then
                        game.Players.LocalPlayer.PlayerGui.Stats.AddButton.StatsFrame.RemoteEvent:FireServer("Defense",1)
                    end
                end)
            end
            if SaveSettings["Stats"]["Sword"] then
                pcall(function()
                    if tonumber(game.Players.LocalPlayer.PlayerStats.sword.Value) <= math.floor(SaveSettings["Stats"]["SwordCap"]) then
                        game.Players.LocalPlayer.PlayerGui.Stats.AddButton.StatsFrame.RemoteEvent:FireServer("Sword",1)
                    end
                end)
            end
            if SaveSettings["Stats"]["PowerFruit"] then
                pcall(function()
                    if tonumber(game.Players.LocalPlayer.PlayerStats.DF.Value) <= math.floor(SaveSettings["Stats"]["PowerFruitCap"]) then
                        game.Players.LocalPlayer.PlayerGui.Stats.AddButton.StatsFrame.RemoteEvent:FireServer("Devil Fruit",1)
                    end
                end)
            end
        end
    end)
    -------------------------
    local MainTab = win:AddTab("Players")
    local Main7 = MainTab:AddPage()
    local Main8 = MainTab:AddPage()
    function isnil(thing)
        return (thing == nil)
      end
      local function round(n)
        return math.floor(tonumber(n) + 0.5)
      end
      Number = math.random(1, 1000000)
      function UpdatePlayerChaMonster()
        for i,v in pairs(game:GetService'Players':GetChildren()) do
           pcall(function()
             if not isnil(v.Character) then
               if ESPPlayer then
                 if not isnil(v.Character.Head) and not v.Character.Head:FindFirstChild('NameEsp'..Number) then
                    local bill = Instance.new('BillboardGui',v.Character.Head)
                    bill.Name = 'NameEsp'..Number
                    bill.ExtentsOffset = Vector3.new(0, 1, 0)
                    bill.Size = UDim2.new(1,200,1,30)
                    bill.Adornee = v.Character.Head
                    bill.AlwaysOnTop = true
                    local name = Instance.new('TextLabel',bill)
                    name.Font = "GothamBold"
                    name.FontSize = "Size14"
                    name.TextWrapped = true
                    name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
                    name.Size = UDim2.new(1,0,1,0)
                    name.TextYAlignment = 'Top'
                    name.BackgroundTransparency = 1
                    name.TextStrokeTransparency = 0.5
                    if v.Team == game.Players.LocalPlayer.Team then
                      name.TextColor3 = Color3.new(255,0,0)
                    else
                      name.TextColor3 = Color3.new(0,0,255)
                    end
                 else
                    v.Character.Head['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
                 end
               else
                 if v.Character.Head:FindFirstChild('NameEsp'..Number) then
                    v.Character.Head:FindFirstChild('NameEsp'..Number):Destroy()
                 end
               end
             end
           end)
        end
      end
      function UpdateDevilChaMonster() 
        for i,v in pairs(game.Workspace:GetChildren()) do
           pcall(function()
             if DevilFruitESP then
               if string.find(v.Name, "Fruit") then   
                 if not v.Handle:FindFirstChild('NameEsp'..Number) then
                    local bill = Instance.new('BillboardGui',v.Handle)
                    bill.Name = 'NameEsp'..Number
                    bill.ExtentsOffset = Vector3.new(0, 1, 0)
                    bill.Size = UDim2.new(1,200,1,30)
                    bill.Adornee = v.Handle
                    bill.AlwaysOnTop = true
                    local name = Instance.new('TextLabel',bill)
                    name.Font = "GothamBold"
                    name.FontSize = "Size14"
                    name.TextWrapped = true
                    name.Size = UDim2.new(1,0,1,0)
                    name.TextYAlignment = 'Top'
                    name.BackgroundTransparency = 1
                    name.TextStrokeTransparency = 0.5
                    name.TextColor3 = Color3.fromRGB(10, 224, 153)
                    name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
                 else
                    v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
                 end
               end
             else
               if v.Handle:FindFirstChild('NameEsp'..Number) then
                 v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
               end
             end
           end)
        end
      end
    PlayerName = {}
    for i,v in pairs(game.Players:GetChildren()) do  
      table.insert(PlayerName ,v.Name)
    end
    SelectedKillPlayer = ""
    local rdropdwonddd = Main7:AddDropdown("Select Players",PlayerName,function(value)
        SelectedKillPlayer = value
    end)
    Main7:AddButton("Refrsh Player",function()
        PlayerName = {}
        rdropdwonddd:Clear()
        for i,v in pairs(game.Players:GetChildren()) do  
           rdropdwonddd:Add(v.Name)
        end
    end)
    Main7:AddSeperator("Teleport Player")
    Main7:AddButton("Teleport Player",function()
        local plr1 = game.Players.LocalPlayer.Character
        local plr2 = game.Players:FindFirstChild(SelectedKillPlayer)
        plr1.HumanoidRootPart.CFrame = plr2.Character.HumanoidRootPart.CFrame
    end)
    Main7:AddToggle("Spectate Player",false,function(bool)
        Sp = bool
        local plr1 = game.Players.LocalPlayer.Character.Humanoid
        local plr2 = game.Players:FindFirstChild(SelectedKillPlayer)
        repeat wait(.1)
           game.Workspace.Camera.CameraSubject = plr2.Character.Humanoid
        until Sp == false 
        game.Workspace.Camera.CameraSubject = game.Players.LocalPlayer.Character.Humanoid
    end)
    Main8:AddToggle("ESP Player",false,function(a)
        ESPPlayer = a
        while ESPPlayer do wait()
           UpdatePlayerChaMonster()
        end
    end)
    Main8:AddToggle("Auto Farm Bounty OP ",SaveSettings['Players']['All Players'],function(value)
        SaveSettings['Players']['All Players'] = value
        Save()
    end)
    spawn(function()
        while wait() do
            pcall(function()
                if SaveSettings['Players']['All Players'] then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0,10000000,0)
                    wait(1)
                    if game:GetService("Workspace").PlayerCharacters[game.Players.LocalPlayer.Name]:FindFirstChild('LowerTorso') then
                        game:GetService("Workspace").PlayerCharacters[game.Players.LocalPlayer.Name].LowerTorso:Destroy()
                    else
                        eiei = game.Players.LocalPlayer
                        for i, v in pairs(game.Players:GetChildren()) do
                            if v.Name ~= eiei.Name then
                                repeat wait()
                                    NameRandom = v.Name
                                    EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Character.HumanoidRootPart.CFrame * CFrame.new(0,0,5)
                                    autoskillheehee()
                                    wait()
                                    spawn(function()
                                        click()
                                    end)
                                    v.Character.HumanoidRootPart.Size = Vector3.new(5,5,5)
                                    game:GetService'VirtualUser':CaptureController()
                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                until SaveSettings['Players']['All Players'] == false or _G.Change1 == true or not v.Parent or v.Character.Humanoid.Health == 0 or not v.Character
                                v.Character.HumanoidRootPart.Size = Vector3.new(2, 2, 1)
                                _G.Change1 = false
                            end
                        end
                    end
                end
            end)
        end
    end)
    spawn(function()
        game:GetService('RunService').Stepped:connect(function()
            if SaveSettings['Players']['All Players'] == true then
                game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
            end
        end)
    end)
    spawn(function ()
        while wait(6) do
            pcall(function()
                if SaveSettings['Players']['All Players'] then
                    for i, v in pairs(game:GetService("Workspace"):GetChildren()) do
                        if v.Name == NameRandom and v.Humanoid.Health == v.Humanoid.MaxHealth then
                            _G.Change1 = true
                        end
                    end
                end
            end)	
        end
    end)
    _G.Hoppppee = false
	spawn(function()
        while wait() do
            if SaveSettings['Players']['All Players']  then
                wait(60)
                _G.Hoppppee = true
            end
        end
	end)
	spawn(function()
        while wait() do
           if _G.Hoppppee == true then
            wait(1)
                local module = loadstring(game:HttpGet"https://raw.githubusercontent.com/LeoKholYt/roblox/main/lk_serverhop.lua")()
                module:Teleport(game.PlaceId)
                print('Hop !!!')
            end
        end
    end)
    Main8:AddToggle("Kill Players ",false,function(value)
        KillPlayer = value
    end)
    spawn(function()
        while wait() do
            if KillPlayer then
                pcall(function()
                    if KillPlayer == false then
                        game.Players:FindFirstChild(SelectedKillPlayer).Character.HumanoidRootPart.Size = Vector3.new(2, 2, 1)
                    end
                    while KillPlayer do wait()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players:FindFirstChild(SelectedKillPlayer).Character.HumanoidRootPart.CFrame * CFrame.new(0,0,7)
                        autoskillheehee()
                        EquipWeapon(SaveSettings["Main2"]["SelectToolWeapon"])
                        wait(2)
                        spawn(function()
                            click()
                        end)
                        game.Players:FindFirstChild(SelectedKillPlayer).Character.HumanoidRootPart.Size = Vector3.new(5,5,5)
                        game:GetService'VirtualUser':CaptureController()
                        game:GetService'VirtualUser':B1Down(Vector2.new(1280, 672))
                    end
                end)
            end
        end
    end)
    local MainTab = win:AddTab("Teleport")
    local Teleport = MainTab:AddPage()
    local Main7 = MainTab:AddPage()
    if OldWorld then
        Teleport:AddButton("Stone Rain Sea",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6157.8969726563, 257.10565185547, -2055.2817382813)
        end)
        Teleport:AddButton("Town",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1914.3870849609, 16.39058303833, -1499.3818359375)
        end)
        Teleport:AddButton("Pirate Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3589.8996582031, 38.009464263916, -534.47290039063)
        end)
        Teleport:AddButton("Soldier Town",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1816.4361572266, 39.931896209717, 151.49806213379)
        end)
        Teleport:AddButton("Shark Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3258.72265625, 10.659820556641, 1478.6558837891)
        end)
        Teleport:AddButton("Chef Ship",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-36.736728668213, 49.899345397949, 148.02322387695)
        end)
        Teleport:AddButton("Snow Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1290.9379882813, 18.407562255859, 1544.3410644531)
        end)
        Teleport:AddButton("Desert Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1465.0296630859, 13.005693435669, 2080.2541503906)
        end)
        Teleport:AddButton("Skyland",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(29.492475509644, 386.59158325195, 4081.8803710938)
        end)
        Teleport:AddButton("Bubbleland",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(5834.935546875, 12.333806991577, 3565.673828125)
        end)
        Teleport:AddButton("Lobby Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2990.255859375, 13.208541870117, 5101.4956054688)
        end)
        Teleport:AddButton("War Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6481.0458984375, 51.469699859619, 959.49676513672)
        end)
        Teleport:AddButton("Stone Arena",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9672.5810546875, 37.840091705322, -3748.7685546875)
        end)
        Teleport:AddButton("Fishland",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2376.3774414063, 40.366146087646, 9148.59375)
        end)
        Teleport:AddButton("Zombie Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(496.62362670898, 226.86659240723, 6346.6674804688)
        end)
        end
        if NewWorld then
        Teleport:AddButton("Japan",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3530.58203125, 57.335056304932, 230.64198303223)
        end)
        Teleport:AddButton("Desert",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(9823.3857421875, 14.436893463135, 1637.6741943359)
        end)
        Teleport:AddButton("Loaf Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6803.677734375, 31.405124664307, 8190.4956054688)
        end)
        Teleport:AddButton("Mirror Room",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(30434.181640625, 24.792255401611, 93295.171875)
        end)
        Teleport:AddButton("Skull Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1456.9604492188, 370.4836730957, 7256.5791015625)
        end)
        Teleport:AddButton("Halloween Island",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(11856.908203125, 258.35546875, 6284.6787109375)
        end)
        Teleport:AddButton("SummonAltar",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1299.5186767578, 462.16180419922, 7379.3012695313)
        end)
        end
        Main7:AddSeperator("All Sea")
        Main7:AddButton("Teleport OldWorld",function()
            TeleporttoOldWorld = true
        end)
        spawn(function()
            while wait() do
                if TeleporttoOldWorld then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3947.696044921875, 16.74089813232422, 324.06292724609375)
                        click()
                        wait(.5)
                        for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                            if v.Name == "Dialogue" then
                                v.Accept.Size = UDim2.new(0, 10000, 0, 10000)
                                v.Accept.Position = UDim2.new(-2, 0, -5, 0)
                                v.Accept.ImageTransparency = 1
                                game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer()
                            end
                        end
                    end)
                end
            end
        end)
        Main7:AddButton("Teleport Newworld",function()
            TeleporttoNewWorld = true
        end)
        spawn(function()
            while wait() do
                if TeleporttoNewWorld then
                    pcall(function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3947.696044921875, 16.74089813232422, 324.06292724609375)
                        click()
                        wait(.5)
                        for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                            if v.Name == "Dialogue" then
                                v.Accept.Size = UDim2.new(0, 10000, 0, 10000)
                                v.Accept.Position = UDim2.new(-2, 0, -5, 0)
                                v.Accept.ImageTransparency = 1
                                game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer()
                            end
                        end
                    end)
                end
            end
        end)
    -------------------------
    local MainTab = win:AddTab("Shop")
    local Main8 = MainTab:AddPage()
    local Main9 = MainTab:AddPage()

    function TP(CFrame)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame
    end


    Main8:AddSeperator("Fighting Style")
    if NewWorld then
        Main8:AddButton("Dark Leg",function()
            TP(CFrame.new(2366.47, 57.5062, 128.7))
        end)
        Main8:AddButton("Half Robot",function()
            TP(CFrame.new(2320.13, 56.8765, 235.885))
        end)
        Main8:AddButton("Water Style",function()
            TP(CFrame.new(2454.34, 57.5311, 229.735))
        end)
        Main8:AddButton("Dragon Claw",function()
            TP(CFrame.new(2718.39, 430.89, 728.692))
        end)
    end
    if OldWorld then
        Main8:AddButton("Dark Leg",function()
            TP(CFrame.new())
        end)
        Main8:AddButton("Half Robot",function()
            TP(CFrame.new())
        end)
        Main8:AddButton("Water Style",function()
            TP(CFrame.new())
        end)
        Main8:AddButton("Dragon Claw",function()
            TP(CFrame.new())
        end)
    end
    Main9:AddSeperator("NPC")
    if NewWorld then
        Main9:AddButton("Teleport To Quest",function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("ReplicatedStorage").MAP["QuestLvl"..CheckQuest()].HumanoidRootPart.CFrame * CFrame.new(0,0,-2.5)
        end)
        Main9:AddButton("DF Shop",function()
            TP(CFrame.new(3515.84, 61.8651, 320.459))
        end)
        Main9:AddButton("Hint Sky Jump",function()
            TP(CFrame.new(3561.66, 57.3768, 274.28))
        end)
        Main9:AddButton("Ship",function()
            TP(CFrame.new(3950.97, 16.8469, 155.337))
        end)
        Main9:AddButton("Elite Pirate",function()
            TP(CFrame.new(3951.08, 16.8522, 323.971))
        end)
        Main9:AddButton("Reset Stats Shop",function()
            TP(CFrame.new(2433.93, 57.4331, 137.138))
        end)
    end
    if OldWorld then
        Main9:AddButton("Dark Leg",function()
            TP(CFrame.new())
        end)
        Main9:AddButton("Half Robot",function()
            TP(CFrame.new())
        end)
        Main9:AddButton("Water Style",function()
            TP(CFrame.new())
        end)
        Main9:AddButton("Dragon Claw",function()
            TP(CFrame.new())
        end)
    end
    -------------------------
    local MainTab = win:AddTab("Setting")
    local SET = MainTab:AddPage()
    local SET2 = MainTab:AddPage()


    SET:AddToggle("Skill Z",SaveSettings["Settings"]["SkilZ"], function(vu)
        SaveSettings["Settings"]["Skil Z"] = vu
        Save()
    end)
    SET:AddToggle("Skill X",SaveSettings["Settings"]["SkilX"], function(vu)
        SaveSettings["Settings"]["Skil X"] = vu
        Save()
    end)
    SET:AddToggle("Skill C",SaveSettings["Settings"]["SkilC"], function(vu)
        SaveSettings["Settings"]["Skil C"] = vu
        Save()
    end)
    SET:AddToggle("Skill V",SaveSettings["Settings"]["SkilV"], function(vu)
        SaveSettings["Settings"]["Skil V"] = vu
        Save()
    end)

    SET2:AddToggle("Auto Haki",SaveSettings["Settings"]["HAKI"], function(vu)
        SaveSettings["Settings"]["HAKI"] = vu
        Save()
    end)
    function autoskillheehee()
        if SaveSettings["Settings"]["Skil Z"] == true then
           game:GetService("VirtualInputManager"):SendKeyEvent(true,122,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
           game:GetService("VirtualInputManager"):SendKeyEvent(false,122,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
        end
        if SaveSettings["Settings"]["Skil X"] == true then
           game:GetService("VirtualInputManager"):SendKeyEvent(true,120,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
           game:GetService("VirtualInputManager"):SendKeyEvent(false,120,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
        end
        if SaveSettings["Settings"]["Skil C"] == true then
           game:GetService("VirtualInputManager"):SendKeyEvent(true,99,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
           game:GetService("VirtualInputManager"):SendKeyEvent(false,99,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
        end
        if SaveSettings["Settings"]["Skil V"] == true then
           game:GetService("VirtualInputManager"):SendKeyEvent(true,118,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
           game:GetService("VirtualInputManager"):SendKeyEvent(false,118,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
        end
    end
    spawn(function()
        while wait(.1) do
            pcall(function()
                if SaveSettings["Settings"]["HAKI"] then
                    if game.Players.LocalPlayer.Character.Haki.Value == 0 then
                        game.Players.LocalPlayer.Character.Haki.Value = 1
                        game:GetService("Players").LocalPlayer.Character.Services.Client.Armament:FireServer()
                    end
                end
            end)
        end
    end)
end
