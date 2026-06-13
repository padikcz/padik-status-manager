# Padik Status Manager

![Padik Status Manager](https://padik.eu/wp-content/uploads/2026/06/Bez-nazvu-2048x1017-1.png)

# Jak nastavit Padik Status Manager ve WordPressu

Chcete na svém WordPress webu zobrazovat aktuální stav serverů, webových stránek nebo dalších služeb monitorovaných pomocí **Uptime Kuma**?

Plugin **Padik Status Manager** propojí WordPress s veřejnou stavovou stránkou Uptime Kuma. Vybrané služby poté můžete zobrazit několika způsoby:

- shortcodu,

- vlastního widgetu pro Elementor,

- automatického obnovování stavu,

- několika samostatných seznamů služeb.

## 📑 Obsah návodu

- Stažení a instalace pluginu

- Nastavení veřejné Status Page v Uptime Kuma

- Propojení WordPressu s Uptime Kuma

- Vytvoření a vložení seznamu služeb

- Použití v Elementoru

- Správa seznamů a aktualizace pluginu

- Řešení nejčastějších problémů

## 📋 Co budete potřebovat

Než začnete, ujistěte se, že máte k dispozici:

Uptime Kuma můžete nainstalovat například pomocí komunitního skriptu pro Proxmox:

```
https://community-scripts.org/scripts?q=Uptime+Kuma
```

## 📦 1. Stažení pluginu

Plugin stáhnete z GitHubu:

```
https://github.com/padikcz/padik-status-manager/releases
```

Na stránce repozitáře otevřete sekci **Releases** a stáhněte nejnovější instalační ZIP soubor.

>
⚠️ Nestahujte soubor označený jako **Source code**. Pro instalaci do WordPressu použijte připravený ZIP soubor pluginu.

### 🛡️ Doporučení

Před instalací nebo aktualizací pluginu doporučuji vytvořit kompletní zálohu WordPressu.

## 🔌 2. Instalace pluginu do WordPressu

Přihlaste se do administrace WordPressu a pokračujte následovně:

- Otevřete **Pluginy → Instalace pluginů**.

- Klikněte na **Nahrát plugin**.

- Vyberte stažený ZIP soubor.

- Klikněte na **Instalovat**.

- Po dokončení instalace klikněte na **Aktivovat plugin**.

Po aktivaci se v administraci WordPressu zobrazí nastavení pluginu.

## 🌐 3. Vytvoření veřejné Status Page v Uptime Kuma

Nejprve je potřeba v Uptime Kuma vytvořit veřejnou stavovou stránku.

V administraci Uptime Kuma:

- Otevřete sekci **Status Pages**.

- Vytvořte novou stavovou stránku.

- Přidejte na ni monitory, které chcete zobrazovat ve WordPressu.

- Uložte změny.

- Zkontrolujte, že je stránka veřejně dostupná.

### 🔎 Jak zjistit slug stránky

Pokud má vaše stavová stránka adresu:

```
https://status.example.cz/status/default
```

nastavení bude následující:

```
Adresa Uptime Kuma: https://status.example.czSlug Status Page: default
```

Slug je tedy poslední část adresy za /status/.

>
⚠️ Status Page musí být veřejná. Pokud je chráněná přihlášením, plugin nebude moci monitory načíst.

## ⚙️ 4. Propojení WordPressu s Uptime Kuma

Ve WordPressu otevřete **Nastavení → Padik Status Manager**.

Vyplňte potřebné údaje.

### Adresa Uptime Kuma

Zadejte základní adresu serveru:

```
https://status.example.cz
```

Do adresy nepřidávejte /status/default.

### Slug Status Page

Zadejte pouze slug veřejné stránky:

```
default
```

### Interval obnovení

Nastavte, jak často se má stav služeb automaticky aktualizovat.

Například:

```
30 sekund
```

Nakonec klikněte na tlačítko **💾 Uložit připojení**.

Plugin používá WordPress jako prostředníka mezi návštěvníkem a Uptime Kuma. Díky tomu není potřeba složitě nastavovat CORS.

## 🗂️ 5. Vytvoření seznamu služeb

Po úspěšném uložení připojení můžete vytvořit vlastní seznam monitorů.

Postup:

- Zadejte název seznamu.

- Klikněte na **Načíst monitory z Uptime Kuma**.

- Vyberte služby, které chcete zobrazovat.

- Klikněte na **Vytvořit seznam**.

### Příklad názvu seznamu

```
Stav našich služeb
```

Můžete vytvořit více různých seznamů.

Například:

- 🌐 webové stránky,

- 🎮 herní servery,

- 🗄️ databáze,

- ☁️ cloudové služby,

- 🔐 interní systémy.

Každý seznam má vlastní shortcode.

Například:

```
[padik_status list="list_abcdefgh"]
```

>
ℹ️ Identifikátor seznamu bude u každého vytvořeného seznamu jiný. Používejte vždy shortcode zobrazený přímo v administraci pluginu.

## 📝 6. Vložení seznamu na web

Otevřete stránku nebo příspěvek, na kterém chcete zobrazit stav služeb.

V editoru WordPressu:

- Přidejte blok **Shortcode**.

- Vložte vygenerovaný shortcode.

- Stránku uložte nebo publikujte.

Příklad:

```
[padik_status list="list_abcdefgh"]
```

Po načtení stránky se zobrazí vybrané služby a jejich aktuální stav.

## 🎨 7. Použití v Elementoru

Padik Status Manager obsahuje vlastní widget pro Elementor.

Widget najdete pod názvem:

```
Padik Status List
```

### Postup vložení

- Otevřete stránku v editoru Elementor.

- Do vyhledávání widgetů napište **Padik Status List**.

- Přetáhněte widget na stránku.

- Vyberte uložený seznam.

- Upravte vzhled v záložce **Styl**.

### V Elementoru můžete upravit například:

- šířku karet,

- mezery mezi kartami,

- barvu pozadí,

- rámečky,

- zaoblení rohů,

- vnitřní odsazení,

- velikost textu,

- typografii,

- velikost stavové tečky,

- barvy jednotlivých stavů.

## 🚦 Význam stavových barev

Plugin rozlišuje stav služeb pomocí barevných indikátorů.

### 🟢 Zelená

Služba je online a funguje správně.

### 🔴 Červená

Služba je offline nebo není dostupná.

### 🟠 Oranžová

Stav služby čeká na vyhodnocení.

### ⚪ Šedá

Stav není známý nebo se nepodařilo načíst data.

### 🟡 Žlutá

Probíhá načítání aktuálního stavu.

## ✏️ 8. Úprava seznamu

V nastavení pluginu najděte sekci **Uložené seznamy**.

U požadovaného seznamu klikněte na **Upravit**.

Plugin následně načte:

- název seznamu,

- dostupné monitory,

- dříve vybrané služby.

Po provedení změn klikněte na **💾 Aktualizovat seznam**.

Shortcode zůstane stejný, takže jej nemusíte znovu vkládat na stránku.

## 🗑️ 9. Odstranění seznamu

Pokud již seznam nepotřebujete, můžete jej odstranit v sekci **Uložené seznamy**.

U vybraného seznamu klikněte na **Odstranit seznam**.

>
⚠️ Po odstranění přestane shortcode daného seznamu fungovat. Zkontrolujte proto, zda shortcode není použitý na některé stránce.

## 🔄 10. Aktualizace pluginu

Novou verzi pluginu stáhněte ze sekce **Releases** na GitHubu.

Poté ve WordPressu otevřete **Pluginy → Instalace pluginů → Nahrát plugin**.

Nahrajte nový ZIP soubor. WordPress nabídne nahrazení aktuální verze pluginu novější verzí.

Nastavení a uložené seznamy by měly zůstat zachované.

>
🛡️ Před každou aktualizací doporučuji vytvořit zálohu webu.

## 🛠️ Řešení nejčastějších problémů

## ❌ Monitory se nenačtou

Zkontrolujte:

- zda je správně zadaná adresa Uptime Kuma,

- zda je správně zadaný slug,

- zda je Status Page veřejná,

- zda je Uptime Kuma dostupná z internetu,

- zda jsou monitory přidané na vybrané Status Page,

- zda adresa obsahuje https://.

Správný příklad:

```
https://status.example.cz
```

Nesprávný příklad:

```
https://status.example.cz/status/default
```

## ❌ Seznam se na stránce nezobrazuje

Ověřte:

- zda je plugin aktivní,

- zda seznam nebyl odstraněn,

- zda používáte správný shortcode,

- zda Uptime Kuma funguje,

- zda je veřejná Status Page dostupná,

- zda WordPress neblokuje REST API.

Plugin používá vlastní REST endpoint:

```
/wp-json/padik-status/v1/heartbeat
```

## ❌ Elementor widget není vidět

Zkontrolujte, zda je Elementor aktivní.

Poté můžete vyzkoušet:

- zavřít editor Elementoru,

- obnovit stránku,

- znovu otevřít Elementor,

- vymazat cache WordPressu,

- vymazat cache prohlížeče.

## ❌ Stav služby se neaktualizuje

Zkontrolujte nastavený interval obnovení a dostupnost Uptime Kuma.

Pomoci může také:

- vymazání cache webu,

- vypnutí cache pro danou stránku,

- kontrola konzole prohlížeče,

- kontrola REST API WordPressu.

## ✅ Závěr

**Padik Status Manager** umožňuje jednoduše zobrazit stav služeb z Uptime Kuma přímo na WordPress webu.

Plugin nabízí:

## 📥 Stažení pluginu

```
https://github.com/padikcz/padik-status-manager
```

>
💡 Plugin jsem vytvořil jako jednoduché řešení pro propojení WordPressu s Uptime Kuma. Před instalací nebo aktualizací si vždy vytvořte zálohu webu.

---

[Přečíst článek na webu](https://padik.eu/padik-status-manager/)
