# M4NIX
FIVEM

### Installation, Replace at line 528 on server.lua of your gcphone the function getBourse()

```LUA
--====================================================================================
--  App bourse
--====================================================================================
function getBourse()    
    item = {}
    prix = {}
    medio = {}
    difference = {}
    local result = MySQL.Sync.fetchAll("SELECT * FROM Bourse",{})
    local qnt = #result
    for i=1, qnt, 1 do
        item[i] = result[i].Label
        prix[i] = result[i].Actuel
        medio[i] = result[i].Med
        difference[i] = prix[i] - medio[i]
    end
    local result = {}
    for i=1, qnt, 1 do
        local line = {libelle = item[i], price = prix[i], difference = difference[i]}
        table.insert(result, line)
    end
    return result
end
```
### Fix for arrow in Gcphone - Replace in app.js at line 2300

### this
```JavaScript
return 0 === t.difference ? ["fa-arrow-right", "iblue"] : t.difference < 0 ? ["fa-arrow-up", "ired"] : ["fa-arrow-down", "igreen"]
```
### whit this
```JavaScript
return 0 === t.difference ? ["fa-arrow-right", "iblue"] : t.difference < 0 ? ["fa-arrow-down", "igreen"] : ["fa-arrow-up", "ired"]
