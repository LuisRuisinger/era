>#### Definition
>
>Generics erlauben die Definition und Verwendung von [Komponenten](./Components.md) mit beliebiger Bitbreite. Die Defintion des Generic Fields erfolgt innerhalb des [Entity](./Entites.md).

<br>

```vhdl
entity muxGeneric is
	
	generic (
		width  : integer := 32
	);

	port (
		d0, d1 : in  std_logic_vector(width - 1 downto 0);
		s      : in  std_logic;
		y      : out std_logic_vector(width - 1 downto 0)
	);

end entity muxGeneric;
```

<br>

>Beschreibung von generischen Komponenten:

<br>

```vhdl
component muxGeneric is

	generic (
		width  : integer
	);

	port (
		d0, d1 : in  std_logic_vector(width - 1 downto 0);
		s      : in  std_logic;
		y      : out  std_logic_vector(width - 1 downto 0);
	);

end component muxGeneric;
```

<br>

>Instanziierung erfolgt durch zusätzliches `mappen` des Generics

<br>

```vhdl
...
muxGeneric1: muxGeneric generic map(width => 8) -- kein Semicolon --
                        port    map(...);
...
```
