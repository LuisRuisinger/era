>#### Definition
>Die Flags bilden ein eigenes Register und sind jeweils nur durch ein einzelnes Bit beschrieben. Dieses Bit kann durch bestimmte Operationen gesetzt werden und bietet die Möglichkeit mit bedingten Sprügen den Programmablauf abzuändern. 

<br>

- `MOV, PUSH, POP, JMP, CALL, RET` manipulieren nicht die Flags
- `DEC, INC` manipulieren die Carry Flag nicht
- `ADD, SUB, MUL, ...` manipulieren die Flags

<br>

### Wichtige Flags

|Bezeichner |Name |Beschreibung |
|:---|:---|:---|
|CF |Carry Flag |Übertrag |
|ZF |Zero Flag |Ergebnis ist 0 |
|SF |Sign Flag |Vorzeichen ist negativ |
|OF |Overflow Flag |Überlauf|
|PF |Parry Flag |Nummer der gesetzten Bits ist gerade | 

<br>

### Vergleichsoperationen

>Vergleichsoperationen erlauben mithilfe von [Sprüngen](./Sprünge.md) vom Abweich der sequentiellen Programmabarbeitung und dienen zur Realisation von [Unterprogrammen](./Unterprogramme.md) und [Iterationen](./Speicher%20in%20x86%20Assembly.md)

<br>

##### TEST

>#### Definition
>
>Die TEST Instruktion führt ein bitweises AND mit beiden Operanden aus und setzt dem Resultat ensprechend die SF, ZF und PF Flag. Die OF und CF Flag werden dabei auf 0 gesetzt. Die AF Flag ist undefiniert. Die Operanden selbst werden dabei nicht verändert. TEST ist nicht sign extended

<br>

```nasm
section .text

	MOV BL, 0xFF   ; Setzen jedes Bits
	TEST EAX, BL   ; nicht möglich
	TEST EAX, 0xFF ; möglich, da 0xFF000000
```

<br>

##### CMP

>#### Definition
>
>Die CMP Instruktion vergleicht den ersten Operanden mit dem zweiten. Die eigentliche Vergleichsoperation ist eine Subtraktion mit wessen Resultat entsprechend die CF, OF, SF, ZF, AF und PF Flag gesetzt werden. CMP sign extended ungleiche Operanden.

<br>

```nasm
section .text

	MOV BL, 0xFF  ; Setzen jedes Bits
	CMP EAX, BL   ; möglich
	CMP EAX, 0xFF ; möglich
```