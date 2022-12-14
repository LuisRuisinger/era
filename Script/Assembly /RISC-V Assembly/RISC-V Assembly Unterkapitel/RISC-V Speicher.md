### Speicherzugriff

##### Lesen vom Speicher

>Durch den Befehlssatz `lw destination, offset (base)`.
>Dabei wird in die `destination` der Zielwert geschrieben. Die `base` stellt das Register bzw. die Adresse da auf die wir zugreifen. Bei dem `offset` handelt es sich um eine `n Byte` große Verschiebung.

<br>

```nasm
lw t1, 8 (s0) ;; Laden des Wertes an der Adresse in s0 + 8 in t1
```

<br>

##### Schreiben in Speicher

>Durch den Befehlssatz `sw source, offset (base)`.
>Dabei wird der Wert im Register `source` im Speicher an die Adresse `base` + ihrem Offset `offset` geschrieben.

<br>

```nasm
sw t1, 8 (s0) ;; Schreiben des Wertes in t1 an die Adresse s0 + 8 im Speicher
```

<br>

### Konstanten

##### 12 Bit Konstanten

- Konstante ist eine 12 Bit Zahl im Zweierkomplement
- Befehle mit Immediates mit maximal 12 Bit müssen `-i` Suffix tragen

<br>

##### 32 Bit Konstanten

> `lui` - load upper immediate: Lädt eine Konstante in die oberen 20 Bit des Zielregisters. Die unteren 12 Bits werden genullt. Eine Operation erfolgt indem man die unteren 12 Bit der Konstante als weiteren, nun sign extended Operator, hinzufügt. `-i` Suffix muss für Operationen mit den unteren 12 Bit weiterhin bestehen.

<br>

```nasm
lui s0, 0xFEDC8 ;; s0 ist nun 0xFEDC8000
addi s0, s0, 0x765 ;; addiert die unteren 12 Bit sign extended dazu
```

<br>

>Falls Bit 11 (der höchste Bit einer 12 BIt Variable) 1 ist muss vor einem Zusammenfügen zu einer 32 Bit Konstante die upper 20 Bit um 1 erhöht werden.

<br>

```nasm
lui s0, 0xFEDC9 ;; Laden von 0xFEDC8EAB in s0 (Inkrement da Bit 11 1 ist)
addi s0, s0, -341 ;; Zusammenfügen mit 0xFFFFFEAB (sign extended)
```