### Logische Shift Instruktion

>#### Definition
>
>Mithilfe einer logischen Shift Instruktion `SH[L/R] Quelle n` werden die Bits des Quelloperanden in eine gewisse Richtung um $n$ Bits verschoben. Dabei gehen die Bits verloren die bei dem Shift ausserhalb der 32 Bit geschoben werden. 
>Das letzte "rausgeshiftete" Bit kommt in die [CF](./Flags.md). 
>Die neu entstehenden leeren Bits werden mit 0 belegt.

<br>

>Verwendbar als $2^n$ vorzeichenlose [Multiplikation / Division](./Besondere%20arithemtische%20Operationen.md)

<br>

```nasm
section .text

	MOV AL, 4
	SHL AL, 2 ; AL = 4 x 2^2
	SHR AL, 2 ; AL = 16 / 2^2
```

<br>

### Arithmetische Shift Instruktion

>#### Definition
>
>Mithilfe einer arithmetischen Shift Instruktion `SA[L/R] Quelle n` werden die Bits des Quelloperanden in eine gewisse Richtung um $n$ Bits verschoben. 
>`SAL` verhällt sich dabei genau wie `SHL`. 
>`SAR` shiftet rechts unter Bewahrung des Vorzeichen. Somit erhalten alle neu entstehenden Bits den Wert des höchsten Bit. `SA[L/R]` interpretiert die Zahlen im [Zweierkomplement](../../Zweierkomplement.md)
>Das letzte "rausgeshiftete" Bit kommt in die CF.

<br>

>Verwendbar als $2^n$ vorzeichenbehaftete Multiplikation / Division. Die Division enthält dabei eine automatische Abrundung.

<br>

```nasm
section .text

	MOV AL, 0xFF ; 0xFF ist -1 im Zweierkomplement
	SHL AL, 4    ; AL = -1 x 2^4 = 0xF0
	SHR AL, 4    ; AL = -16 / 2^4 = 0xFF
```

<br>

### Rotier Instruktion

>#### Definition
>
>Mithilfe der rotier Instruktion `RO[L/R] Quelle n` werden die Bits des Quelloperanden in eine gewissen Richtung um `n` Bits verschoben.
>Dabei wird bei `ROL` das most-significant Bit auf die Position des least-significant Bit rotiert.
>Analog dazu `ROR`.
>Das letzte rotierte Bit wird dabei zusätzlich in die CF kopiert.

<br>

>Für Linksrotationen ist die OF Flag nur für 1 Bit Rotation definiert. Sie wird dabei auf das XOR zwischen der CF und dem most-significant Bit gesetzt.
>Für Rechtsrotationen ist die OF Flag nur für 1 Bit Rotation definiert. Sie wird dabei auf das XOR der beiden most-significant Bit gesetzt.
>Dies geschieht mit den Werten nach der jeweiligen Rotation.

<br>

```nasm
section .text

	MOV AL, 0xF0 ; 1111 0000
	ROL AL, 2    ; 1100 0011
	ROR AL, 4    ; 0011 1100
```

<br>

### Rotier Instruktion durch Carry

>#### Definition
>
>Anders als die Rotier Instruktion wird bei einem Shift das rausrotierte Bit in die CF geschoben. Der Inhalt der CF kommt an die neu enstandende Stelle durch die rotier Operation.
>Die Rotier Instruktion unter Beinhaltung der CF lautet `RC[L/R] Quelle n`.

<br>

>Für Linksrotationen ist die OF Flag nur für 1 Bit Rotation definiert. Sie wird dabei auf das XOR zwischen der CF und dem most-significant Bit gesetzt.
>Für Rechtsrotationen ist die OF Flag nur für 1 Bit Rotation definiert. Sie wird dabei auf das XOR der beiden most-significant Bit gesetzt.
>Dies geschieht mit den Werten nach der jeweiligen Rotation.

<br>

```nasm
section .text

	MOV AL, 0xF0 ; 1111 0000 - CF := 0
	RCL AL, 1    ; 1110 0000 - CF = 1
	RCR AL, 1    ; 1111 0000 - CF = 0
```