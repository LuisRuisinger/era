>#### Definition
>
>Die Calling Convention beschreibt in welcher Ordnung Parameter allokiert werden. 
>Wie und in welcher Reihenfolge Parameter übergeben werden. Dies kann über [Register](../../Register.md) oder dem [Stack](./Stack.md) geschehen.
>Wie Rückgabewerte gespeichert werden. 
>Welche Register für den Caller (volatile registers) und welche für den Callee (non-volatile registers) gesichert werden.
>Und wie der Stack von Caller und Callee gesichert und manipuliert werden darf.

<br>

### Caller-saved Register

>Caller-saved Register müssen vor dem Aufruf eines Unterprogramms vom derzeitigen Caller gesichert werden. Dies bedeutet, dass sie auf den Stack gespusht werden müssen.
>`EAX`, `ECX` und `EDX` sind Caller-saved.

<br >

```nasm
section .text

	PUSH EAX
	PUSH ECX
	PUSH EDX
	
	CALL Unterprogramm
	
	POP EAX
	POP ECX
	POP EDX
```

<br>

### Callee-saved Register

>Callee-saved Register müssen innerhalb eines Unterprogramms vom gecallten Unterprogramm vor der Benutzung gesichert werden, da diese langlebige Informationen halten.

<br>

```nasm
section .text

	CALL Unterprogramm
	...
	
	Unterprogramm:

		PUSH EBX
		
		MOV EBX, 10
		IMUL EBX, 10
		
		POP EBX
		RET
```

<br>

### Parameterübergabe

>Die Übergabe von Parametern an Unterprogrammen erfolgt immer über den Stack. Dabei müssen die benötigten Parameter vor dem Programmaufruf durch den Caller auf den Stack in umgedrehter Reihenfolge gelegt werden, d.h. erster Parameter wird zuletzt gepusht.

<br>

- Der Rückgabewert befindet sich in EAX
- Sichern des Basepointers durch den Callee
- Kopieren des `ESP` Registers in das `EBP` Register (Standart)
- Zugriff auf Parameter über Stackaccess (wichtig [Stackbelegung](./Unterprogramme.md) beachten)

<br>

```nasm
section .text

	...
	
	PUSH ECX                ; pusht letzten Parameter auf den Stack
	PUSH EBX                ; pusht zweiten Parameter auf den Stack
	PUSH EAX                ; push dritten Parameter auf den Stack
	
	CALL Unterprogramm
	
	POP EAX                 ; hier befindet sich der Rückgabewert
	POP EBX
	POP ECX
	RET
	
	Unterprogramm:
	
		PUSH EBP            ; Sichern des Basepointers
		MOV EBP, ESP
		
		MOV EAX, [EBP - 8]  ; erster Parameter (EAX)
		ADD EAX, [EBP - 12] ; zweiter Parameter (EBX)
		ADD EAX, [EBP - 16] ; dritter Parameter (ECX)
		
		POP EBP             ; wichtig - Basepointer wieder herstellen
		RET
```

<br>

### Vergleichbares C Programm

```c
int main() {
	int a = 1;
	int b = 2;
	int c = 3;

	a = sum_ints(a, b, c);
}

int sum_ints(int a, int b, int c) {
	return a + b + c;
}
```
