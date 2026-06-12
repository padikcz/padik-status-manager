# Padik Status Manager

WordPress plugin pro zobrazení stavů služeb z veřejné stránky **Uptime Kuma**.

Plugin umožňuje:

- připojit WordPress k Uptime Kuma,
- automaticky načíst dostupné monitory,
- vytvořit více vlastních seznamů,
- vybrat monitory pomocí zaškrtávacích polí,
- seznamy upravovat a mazat,
- zobrazit seznam pomocí shortcodu,
- použít vlastní Elementor widget,
- obejít CORS pomocí WordPress REST proxy.

## Stažení

Nejnovější instalační ZIP najdete v sekci **Releases**:

1. Otevřete stránku repozitáře na GitHubu.
2. Vpravo klikněte na **Releases**.
3. Otevřete nejnovější verzi.
4. Stáhněte soubor `padik-status-manager-2.1.2.zip`.

Nestahujte automatický GitHub soubor `Source code`, pokud chcete plugin rovnou instalovat ve WordPressu.

## Požadavky

- WordPress 6.0 nebo novější
- PHP 7.4 nebo novější
- veřejná Uptime Kuma Status Page
- Elementor je volitelný

## Instalace

1. Ve WordPressu otevřete **Pluginy → Instalace pluginů**.
2. Klikněte na **Nahrát plugin**.
3. Vyberte soubor `padik-status-manager-2.1.2.zip`.
4. Klikněte na **Instalovat**.
5. Po instalaci klikněte na **Aktivovat plugin**.

## Nastavení Uptime Kuma

Ve WordPressu otevřete:

**Nastavení → Padik Status Manager**

Vyplňte:

```text
Adresa Uptime Kuma: https://status.example.com
Slug status stránky: default
Obnovení stavu: 30 sekund
```

Ve vašem případě může být například:

```text
Adresa Uptime Kuma: https://status.padik.eu
Slug status stránky: default
```

Potom klikněte na **Uložit připojení**.

## Vytvoření seznamu

1. V části **Vytvořit vlastní seznam** zadejte název.
2. Klikněte na **Načíst monitory z Uptime Kuma**.
3. Zaškrtněte služby, které chcete zobrazit.
4. Klikněte na **Vytvořit seznam**.

Každý seznam dostane vlastní shortcode.

Příklad:

```text
[padik_status list="list_abcdefgh"]
```

## Úprava seznamu

V části **Uložené seznamy** klikněte na **Upravit**.

Plugin načte zpět:

- název seznamu,
- dostupné monitory,
- dříve vybrané položky.

Po změně klikněte na **Aktualizovat seznam**.

## Použití shortcodu

Shortcode vložte do stránky nebo příspěvku:

```text
[padik_status list="list_abcdefgh"]
```

Doporučeno je použít blok **Shortcode**.

## Elementor

Plugin obsahuje vlastní Elementor widget:

```text
Padik Status List
```

Postup:

1. Otevřete stránku v Elementoru.
2. Vyhledejte `Padik Status List`.
3. Přetáhněte widget na stránku.
4. Vyberte uložený seznam.
5. V záložce **Styl** upravte vzhled.

Podporované úpravy:

- zarovnání,
- šířka karet,
- mezery,
- barva pozadí,
- barva okraje,
- zaoblení,
- vnitřní odsazení,
- barva a typografie textu,
- velikost stavové tečky,
- barvy online, offline a načítání.

## Stavové barvy

- zelená: online
- červená: offline
- oranžová: pending
- šedá: neznámý stav nebo chyba
- žlutá: načítání

## Jak plugin funguje

Prohlížeč nevolá Uptime Kuma API přímo.

WordPress načte data na serveru a zpřístupní je přes vlastní REST endpoint:

```text
/wp-json/padik-status/v1/heartbeat
```

Díky tomu se neobjevuje chyba CORS mezi WordPressem a Uptime Kuma.

## Aktualizace pluginu

Při vydání nové verze:

1. Stáhněte nový ZIP z GitHub Releases.
2. Ve WordPressu otevřete **Pluginy → Instalace pluginů → Nahrát plugin**.
3. Nahrajte novou verzi.
4. WordPress nabídne nahrazení stávající verze.

Uložené seznamy a nastavení zůstanou zachované.

## Řešení problémů

### WordPress zobrazí závažnou chybu

Přejmenujte složku pluginu přes konzoli nebo správce souborů:

```bash
mv /var/www/html/wordpress/wp-content/plugins/padik-status-manager \
   /var/www/html/wordpress/wp-content/plugins/padik-status-manager-off
```

Tím se plugin deaktivuje.

### Seznam se nezobrazuje

Zkontrolujte:

- zda seznam stále existuje,
- zda používáte správný shortcode,
- zda je Uptime Kuma status stránka veřejná,
- zda funguje REST endpoint pluginu.

### Elementor widget není vidět

Zkontrolujte, zda je Elementor aktivní. Potom znovu načtěte editor.

## Struktura pluginu

```text
padik-status-manager/
├── assets/
│   ├── admin.css
│   ├── admin.js
│   ├── widget.css
│   └── widget.js
├── includes/
│   ├── class-psm-elementor-widget.php
│   └── class-psm-plugin.php
├── padik-status-manager.php
└── README.md
```

## Licence

Projekt je dostupný pod licencí GPL-2.0-or-later.
