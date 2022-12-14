>#### Definition
>
>Komponenten sind wiederverwendete [Schaltungen](./Entites.md) innerhalb einer [Architektur](./Architecture.md) einer neuen Schaltung. Das Ziel dahinter ist die `Devide and Conquer`. Dies macht es uns einfach common Behavior zu realisieren und serialisieren. 
>Dabei ist wichtig, dass Komponenten eine fertige Architektur bestitzen müssen.

<br>

>Die Komponente muss denselben Namen tragen wie ihr Entity und darf keine abweichenden Ports besitzen.

<br>

```vhdl
architecture behave of TwoBitComparator is

component Comparator is
	port (
		a, b                : in  std_logic;
		cout1, cout2, cout3 : out std_logic
	);
end component Comparator;

-- intern signals --
...
```
