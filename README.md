# map-assets

## Beispielkarte
Beispiel svg Datei für Karte: classical.svg

Empfohlenes Programm: inkscape

Anmerkungen zu Layers:
- unit-positions (Falls irgendwelche Referenzpunkte für die Unitpositionierung gebraucht werden sollten. Sind nur für ein paar britische SCs eingefügt.)

## Farben

50% Opacity bei Province, 100% Opacity bei Unit (bisher)

|Power|Color|
|---|---|
|GB|`#CE3772`|
|FR|`#22A7F0`|
|DR|`#7A3A11`|
|IT|`#1FA800`|
|ÖU|`#F22613`|
|OR|`#F7CA18`|
|RU|`#AAAAAA`|

## Units

Bei den Units gibt es immer zwei Pfade. Einer ist der Schatten, der andere wird dann in der jeweiligen Farbe eingefärbt.

### Abmessungen

Bei einer Kartenabmessung von B=1244px und H=1359px (nicht zu verwechseln mit der viewBox) sind folgende Pixelmaße für die Units vorgesehen:

|Unit|B[px]|H[px]|
|---|---|---|
|Fleet|53.8|15|
|Army|39|20|


## Vorgeschlagene Schnittstelle

Bspw. php8 (bevorzugt, weil Anwendung in PHP 8 geschrieben werden soll)
Validierung ob eine Order gültig ist müssen mMn nicht durchgeführt werden. Wenn da was generiert wird, dann stimmt der Zustand

```php
$map = new Map('variant_name')

$map->colorProvinces(['stp', 'mos', 'ukr'], 'RUSSIA')
$map->colorProvinces(['fgf', 'dfg', 'ert'], 'GERMANY')

$map->addFleet('stp/sc', 'RUSSIA')->move('bot')
$map->addArmy('mun', 'GERMANY')->supportHold(unit_in: 'tyr')->fail() // if order succeeded or not
$map->addArmy('mun', 'GERMANY')->supportMove(unit_from: 'tyr', unit_to: 'bul')->succeeded() 


$map->addArmy('par', 'FRANCE')->build()
$map->addArmy('par', 'FRANCE')->disband()



 
$map->createSvgWithoutOrdersBeforeExecution()
$map->createSvgWithOrdersBeforeExecution()
$map->createSvgWithOrdersAfterExecution()
$map->createSvgWithoutOrdersAfterExecution()
```
