# VHDL
### Einbinden der Standard Libary

```vhdl
libary IEEE; use IEEE.STD_LOGIC_1164.all;
```


### Datentypen

#### std_logic

`std_logic` beschreibt einen `1 Bit` großen Wert

- Zustände: `0, 1, U, X, Z, W, L, H, -`
- Wertzuweisung durch: ` <= '...'`

#### std_logic_vector

`std_logic_vector` beschreibt ein `n Bit` großes Array

- `a : in/out std_logic_vector(n downto 0)` , `n` steht dabei für den maximalen Index
- mit `a(n)` kann man den Wert am Index `n` nutzen
- das mappen von arrays erfolgt ohne Index: `<c_i/c_o> => a`
- Wertzuweisung durch: `"1010", 4b"1010", X"F"` (`4b` für binary und `X` für hex)
- Wertzuweisung von `n` Bit muss immer genau auf ein Array von `n` Elementen erfolgen
- Teilarray Indexierung möglich


### Komponentenbeschreibung

```vhdl
entity <name> is 
	port (
		a, b, c : in  std_logic;
		y       : out std_logic
	);
end entity <name>;
```

- `<name>` :=  Entityname
- `port(...)`  beinhaltet die Eingänge und Ausgänge der Schaltung
- `... : in`  beschreibt die Eingänge
- `... : out`  beschreibt die Ausgänge


### Verhaltensbeschreibung

```vhdl
architecture <a-name> of <name> is

-- components --
-- intern signals --

begin

-- logical behavior --

end architecture <a-name>;
```

- `<a-name>` := Architekturname
- `<name>` := Entityname zudem die Architektur gehören soll

#### Components

- Komponenten innerhalb einer Architektur können als Art Baukasten verwendet werden um die neu Schaltungsarchitektur zu beschreiben
- dabei gilt zu beachten, dass das Komponent eine definierte Architektur besitzt
- der Name des Komponenten muss übereinstimmen mit dem Namen der passenden Komponentenarchitektur

```vhdl
architecture <a-name> of <name> is

component <c-name> is
	port (
		... : in  std_logic;
		... : out std_logic
	);
end component <c-name>;

-- intern signals --
...
```

`<c-name>` := Komponentenname

#### Intern Signals

Interne Signale dienen zur Zwischenspeicherung von Teiloperationen

```vhdl
architecture <a-name> of <name> is

-- components --

singal <s-name_1>, <s-name_2>, ... : std_logic;
...
```

`<s-name_n>` := Name eines internen Signals

#### Logical Behavior

Das Herzstück der Architektur beschreibt das Verhalten des Entities

```vhdl
architecture <a-name> of <name> is

...

begin 

<s-name_n> oder <defined-output> <= <defined-input> <operation> <defined-input>;
...

end architecture <a-name>;
```

- Der Output einer Operation wird mit `<=` zugewiesen und kann zugeteilt werden:
    - `<s-name>` := Zwischenspeicher
    - `<defined-output>` := `out signal` unseres Entites

- `<operation>` steht als Platzhalter für eine logische Operation `and, or, nand, nor, xor, xnor` und steht in einem Ausdruck mit einem oder mehrer `<defined-input>`
- `<defined-input>` kann dabei ein `in signal` unseres Entities sein oder ein Zwischenspeicher

Jedoch kann so nicht eine Schaltung in Form eines Komponenten wiederverwendet werden.
Hierzu müssen wir die Schaltungseingänge und -ausgänge des benötigten Komponenten "mappen". Dies geschieht über `=>` :

```vhdl
architecture <a-name> of <name> is

...

begin

<c-name_n>: <c-name> port map(...)
```

- `<c-name_n>` := beliebig gewählter Name einer initialisierten Komponente
- `<c-name>` := Name der zu verwendenden Komponente
- `port map(...)` mappt die Eingänge und Ausgänge der initialisierten Komponente

Das mapping selbst erfolgt dabei so:

```vhdl
... map(<c_i> => <e_i>, <c_o> => <e_o>);
```

- `<c_i>` := Input des Komponenten, dabei müssen wir alle `n` Inputs auf `<e_i>` Entity Input mappen
- `<c_o>` := Output des Komponenten, dabei müssen wir alle `n` Outputs `<e_o>` Entity Ouput mappen

```vhdl
... map(<e_o> => open);
```

- durch `open` wird der Ouput des Komponents "verworfen"
- logische Terme müssen innerhalb des mappens mit `"..."` umschlossen werden
