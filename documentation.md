# Prehľad
Aplikácia zobrazuje kiná, divadlá, knižnice, kasína, galérie a iné objekty súvisiace s kultúrou alebo voľnočasovými aktivitami.
Hlavné vymoženosti sú:
- filtrovanie zobrazovaných objektov
- zobrazovanie vybraných typov objektov v určitej vzdialenosti od iného objektu
- možnosť zadania vlastnej hodnoty pre rozsah vyhľadávania
- po kliknutí na značku sa tento rozsah graficky znázorní

Okno aplikácie:
![Screenshot](screenshot.png)

# Frontend
Frontend aplikácie je prezentovaný statickou HTML stránkou (`index.html`), ktorá zobrazuje mapu a taktiež panel s ovládacími prvkami, ktoré umožňujú filtrovanie a nastavovanie rozsahu pre vyhľadávanie. Samotná mapa je interaktívna a kliknutím na ľubovoľnú zo zobrazených značiek sa spustí vyhľadávanie podľa rozsahu a aktuálne zvoleného filtrovania. Prejdením myšou cez jednotlivé značky zobrazí ich stručný popis.
Kaskádový štýl mapy bol vytvorený v prostredí aplikácie Mapbox Studio Classic - jedná sa o upravenú verziu Streets štýlu (neobsahuje formátovanie elementov, ktoré sa nenachádzajú v použitých dátach). Na vykreslenie prvkov do mapy bola použitá JavaScriptová knižnica Leaflet.

Všetok frontendový zdrojový kód sa nachádza v súbore `script.js`, na ktorý sa odkazuje stránka `index.html`. JavaScriptový kód zabezpečuje:
- inicializovanie mapy
- spracovanie dát z HTML formulárov
- volanie PHP skriptov
- zobrazovanie elementov na mape

# Backend
Backend aplikácie je vytvorený v jazyku PHP a má na starosť pristupovanie a spracovanie dopytov na databázu. Všetok backendový zdrojový kód sa nachádza v súboroch `getAmenity.php` a `getAmenitiesInRadius.php`.

## Údaje
Všetky údaje uložené v databáze pochádzajú z Open Street Maps, pričom z nich bola vybraná iba Bratislava. Údaje boli importované pomocou nástroja `osm2pgsql`podľa štandardnej OSM schémy vo formáte WGS84 s aktivovaným hstore.
