>#### Definition
>
>Eine Liste von Werten die aufeinanderliegen und nach unten durch neue Einträge dynamisch wächst.  Das rauflegen und abnehmen von Daten erfolgt nach dem LIFO Prinzip. 
>Das Ende des Stackpointers wird durch den Stackpointer gekennzeichnet welcher sich im `ESP` Register befindet. 

>Da der Stack im Konstrast zum Heap nach unten wächst können bei sehr großen Datenmengen die auf die jeweilige Struktur gelegt werden diese ineinander kollidieren was als Resultat einen Error erzeugt.

<br>

### PUSH

>#### Definition
>
>Die Instruktion `PUSH` setzt einen neuen Wert auf den Stack. Der Stackpointer wird um eins verringert.

<br>

```nasm
section .text

	PUSH EAX       ; pusht ein Dword auf den Stack - Stackpointer wird um 4 kleiner
	PUSH dword EAX ; nicht möglich
	PUSH qword 187 ; reservieren ein Qword auf dem Stack obwohl Wert in Bit passt
	PUSH word [Adresse] ; Präfix wird benötigt für richtiges Alignment
```

<br>

### POP

>#### Definition
>
>Die Instruktion `POP` nimmt den letzten Wert vom Stack. Die Größe des heruntergenommenen Wertes entspricht der Größe des Zieloperanden.
>Der Stackpointer wird zudem um die Byteanzahl des Zieloperanden addiert.

<br>

```nasm
section .text

	POP EAX ; nimmt ein Dword vom Stack - Stackpointer wird um 4 größer
	POP byte [Adresse] ; Präfix wird benötigt für richtiges Alignment
```

<br>

### Lokale Variablen

>siehe [Unterprogramme](./Unterprogramme.md)