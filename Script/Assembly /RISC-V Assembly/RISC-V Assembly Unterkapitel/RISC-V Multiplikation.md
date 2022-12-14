>nur Verfügbar durch `M-Erweiterung` 

<br>

- Multiplikation von 32 Bit Zahlen kann zu 64 Bit Resultat führen
- extra Instruktion für die oberen 32 Bit (signed und unsigned Kombinationen

<br>

- `mul rd, rs1, rs2`: Multiply (lower 32 Bit in Register)
- `mulh rd, rs1, rs2`: Multiplay high signed $\cdot$ signed (higher 32 Bit in Register)
- `mulhsu rd, rs1, rs2`: Multiplay high signed $\cdot$ unsigned (higher 32 Bit in Register)
- `mulhu rd, rs1, rs2`: Multiplay high unsigned $\cdot$ unsigned (higher 32 Bit in Register)

<br>

```nasm
mul s3, s1, s2  ;; in s3 liegen die lower 32 Bit
mulh s4, s1, s2 ;; in s4 liegen die higher 32 Bit
```
