>#### Definition
>
>Das Instruktionsformat I-Typ (Immediate-Format Typ) wird verwendet für die Immediate Version der arithmetischen und logischen [R-Typ](./R-Typ.md) Format.

<br>

![[Pasted image 20221207000852.png]]

<br>

- `immediate`: [12-Bit Konstante](../RISC-V%20Speicher.md) sign extended
- `rs1`: [Quellregister](../RISC-V%20Register.md)
- `funct3`: Funktionscode 3 Bit
- `rd`: Zielregister
- `op`: Operationscode (OP-Code) - 3 load, 19 arithmetische und logische, 103 [Sprünge](../RISC-V%20Sprünge.md)

<br>

>Shift Operationen vom I-Typ verwenden nur die obersten 7 Bit als Funktionscode

