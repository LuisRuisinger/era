>#### Definition
>
>Das Instruktionsformat R-Typ (Register-Format Typ) wird meist für arithmetische und logische Instruktionen verwendet.

<br>

![[Pasted image 20221207000020.png]]

<br>

- `funct7`: Funktionscode 7 Bit
- `rs2`: [Register](../RISC-V%20Register.md) des zweiten Quelloperanden (x-Cordierung wird das x gekappt und die Zahl in binär übersetzt)
- `rs1`: analog zu `rs2`
- `funct3`: Funktionscode 3 Bit
- `rd`: Zielregister - analog zu `rs2`
- `op`: Operationscode (OP-Code) - 51 arithmetische und logische
