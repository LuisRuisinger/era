>#### Definition
>
>Zum Realisieren von sequentiellen Prozessen sind `process`-Blöcke erforderlich. 
>Dabei gibt die `sensitivity list` eines Prozesses an auf welches Signal der Prozess reagieren soll. Eine Änderung in diesen Signalen löst den Prozess erneut aus.

<br>

- `rising_edge` und `falling_edge` um auf Clock Signale zu reagieren
- ohne `sensitivity list` wird `process` immer getriggert
- `process (all)` retriggert `process` falls irgendein Port eine Änderung erhält
- kombinatorische Prozesse durch [Zwischenspeicherung](.l/Interne Signale.md)

<br>

```vhdl
signal a, b, c, y : std_logic;

process (c,...)
begin
	y <= a and b;
end process;
```

<br>

> Eine Zustandsänderung wird nur reevaluiert wenn der Prozess (hier durch nur `c`) getriggert wird
