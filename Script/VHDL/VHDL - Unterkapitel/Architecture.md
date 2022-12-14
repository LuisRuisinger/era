>#### Definition
>
>Die Architecture beschreibt das Verhalten eines [Entity](./Entites.md). Dabei gilt es logisch miteiander Eingänge und Ausgänge zu verknüpfen. Zur Vereinfachung einer neuen Architektur können bereits designte Schaltkreise in Form von [Components](./Components.md) wiederverwendet werden.

<br>

```vhdl
architecture behave of TwoBitComparator is
...

begin

cout <= input1 and input2

end architecture behave;
```

<br>

- [Conditional Assignments](./Conditional Assignments.md) führen zu einer dynamischen Wertzuweisung
- [Generics](./Generics.md) führen zu einer dynamischen Schaltungen
- eine Signalzwischenspeicherung kann durch [Interne Signale](./Interne Signale.md) erfolgen
- eine logische Instruktion kann dabei `AND, NAND, OR, NOR, XOR, NXOR` sein

<br>

>Das Wiederverwenden einer Komponente erfordert das Mappen der jeweiligen Eingänge und Ausgänge dieser Schaltung. Die Komponente muss dabei instanziiert werden. Dies kann ein frei gewählter Name sein.

<br>

```vhdl
architecture <a-name> of <name> is

component Comparator is
	port (
		a, b                : in  std_logic;
		cout1, cout2, cout3 : out std_logic
	);
end component Comparator;

begin

compInstance1: Comparator port map(...)
```

<br>

>Das mapping selbst erfolgt dabei so:

<br>

```vhdl
... map(a => a_c2_1, cout1 => cout_c2_1, ...);
```

<br>

- durch `open` wird der Ouput des Komponents "verworfen"
- logische Terme müssen innerhalb des mappens mit `"..."` umschlossen werden

<br>

```vhdl
... map(cout3 => open);
```

