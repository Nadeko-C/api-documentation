# Internal Radar

> Author: [@Neverlose](https://github.com/neverlosecc)  
>
> Name: `Internal Radar`  
>
> Description: `In-Game radar, with all enemies spotted`

```lua
local function on_cm()
    local_idx = g_EngineClient.GetLocalPlayer()
    for idx=1, g_GlobalVars.maxClients + 1 do
        local player = g_EntityList.GetClientEntity(idx)
        if (local_idx ~= idx and player and player ~= nil and player:IsPlayer()) then
            player = player:GetPlayer()
            if(not player:IsTeamMate()) then
                local health = player:m_iHealth()
                if (health > 0) then
                    player:SetProp("DT_BaseEntity", "m_bSpotted", 1)
                end
            end
        end
    end
end

cheat.RegisterCallback("createmove", on_cm)
```

