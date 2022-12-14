### Nicht initialisierter Speicher

>Reservieren von nicht initialisiertem Speicherbereich - in `.bss`

<br>

| Attribut | Bytes |
|:---:|:---:|
| RESB | 1 |
| RESW | 2 |
| RESD | 4 |
| RESQ | 8 |

<br>

```nasm
section .bss

	RESB 1 ; Reserviere 1 mal 1 Byte
	RESW 2 ; Reserviere 2 mal 2 Byte
	RESQ 5 ; Reserviere 5 mal 8 Byte
```

<br>

### Initialisierter Speicher

>Reservieren von initialisiertem Speicherbereich - in `.section`

<br>

| Attribut | Bytes |
|:---:|:---:|
| DB | 1 |
| DW | 2 |
| DD | 4 |
| DQ | 8 |

<br>

```nasm
section .data

	DB 123                     ; Wert 123
	DB 72,101,108,111          ; "Hello" als String - pro ASCII ein Byte
	DB 32                      ; Leerzeichen
	DB "Das ist ein String", 0 ; Nullbyte als Abbruchbedingung wichtig!
```

<br>

##### Labels für Adressangaben

```nasm
section .data

	param1: DD 123
	param2: DD -123
	rueckgabewert: RESB 1
```

<br>

$\rightarrow$ damit wird es möglich Variablen in den Code zu bringen:

```nasm
section .text

	MOV EAX, [param1]       ; Laden des Wertes an der Adresse in EAX
	INC EAX
	CALL [param2]           ; Rufen eines Unterprogramms über die Adresse
	MOV [rueckgabewert], AL ; Achtung der Rückgabewert kann maximal 8 Bit groß sein!
```

<br>

##### Platzhalter

- Labels können auch als Platzhalter für bestimmte Werte agieren
- Platzhalter werden vom Präprozessor entfernt

<br>

```nasm
section .data

	max_unsigned_byte EQU 255
	null_terminator   EQU 0
```

<br>

### Speicherzugriffe

- Speicherzugriff nur bei Quelle oder Ziel
- Speicherzugriff sollte bei Operation die Datengröße als Annotation tragen

<br>

```nasm
section .text

	PUSH DWORD 123 ; Pushen des Wertes 123 - Angabe wie viel Platz wir benötigen
	NEG WORD [42]  ; Negierung des Words an der Adresse 42
```

<br>

 >letzter Punkt wird nicht benötigt wenn wir ein Register als Operand inkludieren

```nasm
section .text

	ADD EAX, [124] ; EAX greift auf 32 Bit bei der Adresse [124] zu
```

<br>

> Es lässt sich daraus herleiten, dass Register immer passende Größen benötigen

```nasm
section .text

	MOV EAX, BX        ; nicht möglich, da 32 Bit und 16 Bit
	MOV EBX, byte [12] ; nicht möglich, da 32 Bit und 8 Bit

	MOV ECX, EDX       ; möglich
	MOV EAX, [12]      ; möglich
	MOV AH, AL         ; möglich
```

<br>

### Indirekte Adressierung

> durch indirekte Adressierung und die verwendung von bedingten [[Sprünge |Sprüngen]] ist eine fortlaufende Iteration durch längere Daten (wie Arrays) möglich

<br>

```nasm
section .text

	...
	ADD EAX, [EBX + EDX]
	INC EDX
	...
```

<br>

- Adresse liegt in EBX
- EDX ist das Offset welches wir fortlaufend inkrementieren 
- Größe `n` des Inkrements bestimmt `n` -fachen Bytesprung
- Werte liegen fortlaufend im Speicher

<br>

```nasm
... [Register + Register * Skalar + Konstante] ...
```

> größter möglicher indirekter Zugriff

<br>

>Unterkapitel von [[x86 Assembly]]
>Unterkapitel von [[Speicheraufbau]]