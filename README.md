-- Script untuk efek asap di badan karakter
local function createSmokeEffect()
    -- Pastikan pemain telah dimuat
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    -- Cari bagian torso sebagai pusat efek
    local torso = character:FindFirstChild("HumanoidRootPart")
    if not torso then
        warn("Bagian torso tidak ditemukan!")
        return
    end

    -- Buat Partikel Asap
    local smokeEffect = Instance.new("ParticleEmitter")
    smokeEffect.Name = "BodySmokeEffect"
    smokeEffect.Texture = "rbxassetid://244221613" -- ID tekstur asap
    smokeEffect.Size = NumberSequence.new(1) -- Ukuran partikel tetap
    smokeEffect.Transparency = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.5), NumberSequenceKeypoint.new(1, 1)})
    smokeEffect.Lifetime = NumberRange.new(2) -- Durasi hidup partikel
    smokeEffect.Rate = 100 -- Jumlah partikel per detik
    smokeEffect.Speed = NumberRange.new(0.5) -- Kecepatan partikel
    smokeEffect.Rotation = NumberRange.new(0, 360) -- Rotasi acak
    smokeEffect.RotSpeed = NumberRange.new(0) -- Rotasi partikel tetap
    smokeEffect.Color = ColorSequence.new(Color3.new(1, 1, 1)) -- Warna putih
    smokeEffect.Parent = torso -- Efek asap melekat pada torso
end

-- Jalankan efek asap
createSmokeEffect()
