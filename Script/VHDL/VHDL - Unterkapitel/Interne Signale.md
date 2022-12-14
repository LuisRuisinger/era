>#### Definition
>
>Interne Signale dienen zur Zwischenspeicherung von Teiloperationen innerhalb einer [Architektur](./Architecture.md). Sie verhalten sich wie Ports. Das heißt sie müssen eine [Typezuweisung](./Datentyen.md) tragen.

<br>

```vhdl
architecture behave of TwoBitComparator is
...

signal sig1, sig2, ... : std_logic;
signal sigOther1, sigOther2, ... : std_logic_vector(3 downto 0);

begin
...
```

