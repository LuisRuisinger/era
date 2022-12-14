>#### Defintion
>
>Entities beschreiben eine Schaltung als Art Blackbox. Es sind nur die Eingänge und Ausgänge ersichtlich. Es kann eine zugehörige [Architektur](./Architecture.md) als logisches Verhalten dazu definiert werden.

<br>

```vhdl
entity <name> is 
	port (
		a, b, c : in  std_logic;
		y       : out std_logic
	);
end entity <name>;
```

<br>

- `<name>` :=  Entityname
- `port(...)`  beinhaltet die Eingänge und Ausgänge der Schaltung
- ```... : in```  beschreibt die Eingänge
- `... : out`  beschreibt die Ausgänge
