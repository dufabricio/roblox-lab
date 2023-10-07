# Block change color on jump

```LUA
local iceblock = script.Parent

local leftAnchor = iceblock.Parent.leftAnchor
local rightAnchor = iceblock.Parent.rightAnchor

local bodyPos = Instance.new("BodyPosition")
bodyPos.Parent = iceblock

-- Cria um evento para detectar quando o bloco é tocado
iceblock.Touched:Connect(function(hit)
	-- Verifica se o hit é um personagem
	if hit.Parent:FindFirstChild("Humanoid") then
		-- Muda a cor do Part
		iceblock.BrickColor = BrickColor.Blue()
	end
end)


while wait() do

	bodyPos.Position = leftAnchor.Position
	wait(2)
	bodyPos.Position = rightAnchor.Position
	wait(2)

end
```

## Enemy With Damage

```LUA
local npc = script.Parent
local hrpOfNPC = npc:WaitForChild("HumanoidRootPart")
local plrsHit = {}
local maxDistance = math.huge

local leftBarrier = script.Parent.Parent.Parent.leftBarrier
local rightBarrier = script.Parent.Parent.Parent.rightBarrier

npc.Humanoid.Touched:Connect(function(touch)
 
    if game.Players:GetPlayerFromCharacter(touch.Parent) and not plrsHit[game.Players:GetPlayerFromCharacter(touch.Parent)] then
 
        plrsHit[game.Players:GetPlayerFromCharacter(touch.Parent)] = true
       
        touch.Parent.Humanoid:TakeDamage(20)
       
        wait(1)
 
        plrsHit[game.Players:GetPlayerFromCharacter(touch.Parent)] = false 
    end
end)


while wait() do
	npc.Humanoid:MoveTo(leftBarrier.Position)
	wait(10)
	npc.Humanoid:MoveTo(rightBarrier.Position)
	wait(10)
end

--while wait() do

--    local plrs = game.Players:GetPlayers()
--    local closestHRP
   
--    for i, plr in pairs(plrs) do
--        if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and plr.Character.Humanoid.Health > 0 then          
--            local hrp = plr.Character.HumanoidRootPart         
--            local distanceBetween = (hrpOfNPC.Position - hrp.Position).Magnitude              
--            if not closestHRP then closestHRP = hrp end        
--            if (hrpOfNPC.Position - closestHRP.Position).Magnitude > distanceBetween then            
--                closestHRP = hrp             
--            end
--        end
--    end
   
--    if closestHRP and (hrpOfNPC.Position - closestHRP.Position).Magnitude <= maxDistance then npc.Humanoid:MoveTo(closestHRP.Position) end
--end

```
