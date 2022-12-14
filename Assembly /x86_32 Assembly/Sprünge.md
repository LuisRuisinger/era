>[!NOTE] Definition
>
>Sprünge können zu der Abweichung von der sequentiellen Befehlsfolge führen.
>Diese können bedingt durch das Setzen von [[Flags]] und unbedingt ausgelöst werden und zur Umsetzung von [[Unterprogramme |Unterprogrammen]] genutzt werden

<br>

> `JMP <Adresse/Label>` $\rightarrow$ unbedingter Sprung an vorgegebene Adresse / Label

<br>

### Bedingte Sprünge

>Sprünge welche nur ausgeführt werden beim Setzen der jeweiligen [[Flags |Flag]]

<br>

| Sprung | Beschreibung | gesetzte Flag |
|:---|:---|:---|
|C |carry |CF = 1 |
|NC |no carry |CF = 0 |
|E, Z |equal / zero |ZF = 1 |
|NE, NZ |not equal / not zero |ZF = 0 |
|O |(signed) overflow |OF = 1 |
|NO |(signed not overflow |OF = 0 |
|G, NLE |(signed) greater / not less or equal |((SF xor OF) or ZF) = 0 |
|GE, NL |(signed) greater or equal / not less |(SF xor OF) = 0 |
|L, NGE |(signed) less / not greater or equal |(SF xor OF) = 1 |
|LE, NG |(signed) less or equal / not greater |((SF xor OF) or ZF) = 1

<br>

```nasm
section .text

	MOV AL, 25
	CMP AL, 10   ; Vergleich von AL mit 10
	JG Label   ; da 25 > 10 springen wir an das Label
	
	...
	
	Label:     ; Hier geht das Programm weiter (Bruch der Sequenz)
	
		...
```

<br>

```nasm
section .text

	MOV AL, 25
	CMP AL, 10
	JG [Adresse] ; Sprung an die Adresse im Speicher 
```
