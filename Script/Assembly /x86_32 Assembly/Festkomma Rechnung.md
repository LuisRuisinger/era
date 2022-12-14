>#### Definition
>
>Anders als Floating-Point Numbers sind Fixed-Point-Numbers fest unterteilt in Vorkomma- und Nachkommastellen. Hierbei beschreibt `n.n` die Anzahl der Vorkomma- und Nachkommastellen.
>Demnach fordert eine Konvertierung auf Fixed-Point einen [logischen Linksshift](./Shifts.md) um $n$ Stellen. 
>Analog dazu folgt die Konvertierung auf einen Integer.

<br>

>#### Beispiel anhand 8.8 Festkomma Zahl
>
>Darstellung von $2.5$ als $8.8$ Fixed-Point-Number:
>
>| $2^7$ | $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ | - | $2^{-1}$ | $2^{-2}$ | $2^{-3}$ | $2^{-4}$ | $2^{-5}$ | $2^{-6}$ | $2^{-7}$ | $2^{-8}$ |
>|:-----:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
>| 0 |   0   | 0 | 0 | 0 | 0 | 1 | 0 | . | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

<br>

### Multiplikation

>[Arithmetische Operationen](./Besondere%20arithemtische%20Operationen.md) behandeln Festkommazahlen wie normale Integer
>Demnach resultiert daraus eine `16.16 Fixed-Point-Number` die man durch $8$ Bit logischen Linksshift zurück in das richtige Format bringt.
>$\Rightarrow$ Verlust von $8$ Bit Präzision

>Wichtig: `EDX` immer auf 0 setzen, da 64 Bit Resultat gelesen werden könnte

<br>

```nasm
section .text
	
	XOR EAX, EAX  ; Higher 16 Bit manipulieren das Ergebnis
	XOR EBX, EBX
	XOR EDX, EDX  ; Konkatination mit EAX manipuliert das Ergebnis
	
	MOV AX, 0x280 ; Laden von 2.5 in AX als 8.8 Fixed
	MOV BX, 0xA00 ; Laden von 10.0 in BX als 8.8 Fixed
	MUL EBX       ; Wichtig - immer auf 32Bit Ebene rechnen
	SHR EAX, 8    ; Formatierung von 16.16 auf 16.8
```

<br>

### Division

>Die Division zweier Floating-Point-Zahlen führt dazu, dass die Nachkommastellen die Differenz zwischen den Nachkommastellen der ersten und zweiten Zahl bilden. Bei ungleichen Formaten kann das dazu führen, dass die Nachkommastellen Teile der Vorkommastellen vernichten.
>$\Rightarrow$ Dividend (Erster Operand) um seine $n$ Nachkommastellen nach links shiften.

>Wichtig: `EDX` stellt auch hier eine Konkatination mit `EAX` dar

<br>

```nasm
section .text

	XOR EAX, EAX  ; Higher 16 Bit manipulieren das Ergebnis
	XOR EBX, EBX
	XOR EDX, EDX  ; Konkatination mit EAX manipuliert das Ergebnis
	
	MOV AX, 0xA00 ; Laden von 10.0 in AX
	MOV BX, 0x280 ; Laden von 2.5 in BX
	SHL EAX, 8    ; Formatierung von 8.8 auf 8.16
	DIV EBX       ; 8.16 und 8.8 werden zu 8.8
```