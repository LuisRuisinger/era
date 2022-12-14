> #### Defintion
>
>Unterprogramme erlauben die begingte Ausfürhung von bestimmten Subroutinen, vergleichbar zu Methodenaufrunfen. 
>Mithilfe der Instruktion `CALL` und der Adresse, bzw dem Label als Operanden ist es dem Programm möglich an das Codesegment ([bedingt](./Flags.md) zu [springen](./Sprünge.md)).
>Anders als bei `JMP` und ähnlichen Instruktionen wird die Rücksprungadresse auf den [Stack](./Stack.md) gelegt und durch den Basepointer welcher im `ESP` Register gespeichert wird makiert.
>Durch die Instruktion `RET` ist das Unterprogramm beendet, die Rücksprungadresse wird vom Stack gepoppt und es wird an die Adresse in der Befehlsabfolge zurückgesprungen.

<br>

```nasm
section .text

	CALL Label ; Sprung zu dem Label Label
	...
	
	Label:
	
		...
		ret    ; Rücksprung
```

<br>

### Lokale Variablen

>Durch die Subtraktion des Stackpointers in `ESP` ist es möglich dynamisch Platz zu schaffen für lokale Variablen $\rightarrow$ begrenzte Lebenszeit mit der Ausfürung des Unterprogramms

<br>

```nasm
section .text

	SUB ESP, 10               ; Allokieren von 10 Byte
	MOV dword [ESP + 10], 123 ; Schreiben eines Dwords direkt nach dem letzten 
	                          ; gepushten Wert
```

<br>

>Wichtig danach wieder danach den Stackpointer richtig setzen

<br>

### Parameterübergabe

>Es gilt zu klären wie Daten an Unterprogramme übergeben werden, im Unterprogramm manipuliert werden dürfen und wie der Stack manipuliert werden darf $\Rightarrow$ [x86 Calling Convention](./x86%20Calling%20Convention.md).
>Wichtig zu beachten gilt, dass die Instruktion `CALL` 2 Werte auf den Stack vor der Programmweiterfürhung legt: die Rücksprungadresse und ein Backup dieser. Beide sind 4 Byte groß.