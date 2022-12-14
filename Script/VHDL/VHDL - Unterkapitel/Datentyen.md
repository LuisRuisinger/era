### std_logic

>`std_logic` beschreibt einen `1 Bit` großen Wert

- Zustände: `0, 1, U, X, Z, W, L, H, -`
- Wertzuweisung durch: ` <= '...'` 

<br>

### std_logic_vector

>`std_logic_vector` beschreibt ein `n Bit` großes Array

- `a : in/out std_logic_vector(n downto 0)` , `n` steht dabei für den maximalen Index
- mit `a(n)` kann man den Wert am Index `n` manipulieren
- das mappen von arrays erfolgt ohne Index: `<c_i/c_o> => a` 
- Wertzuweisung durch: `"1010", 4b"1010", X"F"` (`4b` für binary und `X` für hex)
- Werte selbst können dieselben sein wie `std_logc`
- Wertzuweisung von `n` Bit muss immer genau auf ein Array von `n` Elementen erfolgen
- Teilarray Indexierung möglich
- Konkatinierung mit `&` möglich
