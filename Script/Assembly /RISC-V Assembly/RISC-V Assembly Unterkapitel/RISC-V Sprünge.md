>Änderung der sequentiellen Programmdurchführung.
>Conditions funktionieren dabei wie [Labels](../../x86_32%20Assembly/x86_32%20Assembly%20-%20Unterkapitel/Speicher%20in%20x86%20Assembly.md) in [x86_32](../../x86_32%20Assembly/x86%20Assembly.md) um einen dynamischen Programmablauf zu gewehrleisten.

<br>

### Unbedingt

- branch if equal (`beq`)
- branch if not equal (`bne`)
- branch if less than (`blt`)
- branch if greater than or equal (`bge`)

<br>

```nasm
<operand> target ;; target ist die Zieladresse / Label
```

<br>

### Unbedingt

- jump (`j`)
- jump register (`jr`)
- jump and link (`jal`)
- jump and link register (`jalr`)

<br>

```nasm
<operand> rg1, rg2, target ;; target ist dabei des Ziels falls es zum Sprung kommt
```

<br>

### Long Jumps

>immediates sind beschränkt in ihrer Größe (20 Bits bei `jal` und 12 Bits bei `jalr`). Somit ist die Sprungweite auf diese Bitgrenze begrenzt. 
>Spezieller Befehl `audipc rs1, imm` (add upper immediate to PC) um Adressen zu erweitern auf 32 Bit.
