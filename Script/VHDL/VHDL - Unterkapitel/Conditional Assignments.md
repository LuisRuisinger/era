>#### Defintion
>
>Bedingte Zuweisungen innerhalb einer [Architektur](./Architecture.md) geschehen aufgrund eines Zustandes der abgefragt wird.

<br>

- Vergleiche geschehen über `=` 
- `when` ... `else` als Conditional Structure

<br>

```vhdl
entity muxByte is
	port (
		d0, d1 : in  std_logic_vector(7 downto 0);
		s      : in  std_logic;
		y      : out std_logic_vector(7 downto 0)
	);
end entity muxByte;

architecture behave of muxByte is
begin

y <= d1 when s = '1' else d0;

end architecture behave;
```

<br>

>Mehrere Syntaxmöglichkeiten:

<br>

```vhdl
-- Möglichkeit 1 --

y <= d0 when s = "00" else
	 d1 when s = "01" else
	 d2 when s = "10" else
	 d3;

-- Möglichkeit 2 --

with s select y <=
	d0 when "00",
	d1 when "01",
	d2 when "10",
	d3 when others;

-- Möglichkeit 3 --

process is
	begin
	case s is
		when "00" => y <= d0;
		when "01" => y <= d1;
		when "10" => y <= d2;
	end case;
end process;

-- Möglichkeit 4 --

process is
	begin

	if s = "00" then y <= d0;
	elsif s = "01" then y <= d1;
	elsif s = "10" then y <= d2;
	else y <= d3;

	end if;
end process;
```
