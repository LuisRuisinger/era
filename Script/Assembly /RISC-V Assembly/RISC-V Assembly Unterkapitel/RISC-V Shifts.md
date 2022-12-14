>Schiebebefehle verhalten sich in RISC-V genauso wie bei [x86_32](../../x86_32%20Assembly/x86%20Assembly.md) [Shifts](../../x86_32%20Assembly/x86_32%20Assembly%20-%20Unterkapitel/Shifts.md).
>Befehle mit `uimm` müssen dabei verwendet werden wenn die Shiftreichweite mithilfe eines Immediates ausgedrückt wird.

<br>

- `sll rd, rs1, rs2`: shift left logical
- `slli rd, rs1, uimm`: shift left logical immediate
- `srl rd, rs1, rs2`: shift right logical
- `srli rd, rs1, uimm`: shift right logical immediate
- `sra rd, rs1, rs2`: shift right arithmetic
- `srai rd, rs1, uimm`: shift right arithmetic immediate