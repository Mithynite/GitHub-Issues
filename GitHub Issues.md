
# Chyby

### Nefunkční tlačítko

##### Název: 
*Vyhledávátko u událostí*
##### Definice problému: 
*U událostí po vymazání vyhledávaného slova se nic nestane se sezname firem. Zrušit tam        pamatování uloženého*

##### Řešení
- upravený skript: *table.js*
- úprava:
	- přidání chybějící funkce **SetCookie(value)** a její příslušné nastavení
- přidaný/upravený kód:
```
function Setcookie(value) {
	const d = new Date();
	d.setTime(d.getTime() + (0.5 * 24 * 60 * 60 * 1000));
	let expires = "expires=" + d.toUTCString();
	document.cookie = "search=" + value + ";" +expires;
}

var serachInput = $("#basic_filter label input");
serachInput.keyup(function(){
	var value = serachInput.val();
	document.cookie = "search="+ value;
	if (window.history.replaceState) {
		window.history.replaceState("", "CRM", window.location.origin+ "?search="+ value);
	 }
});
```

---
# Autoři

- Ondra Kačírek - **SCRUM master**, **Kodér**
- Michal Charvát - **JS programátor**
- Kuba Hofman - **PO**, **Kodér**
- Pavel Edl - **JS programátor**