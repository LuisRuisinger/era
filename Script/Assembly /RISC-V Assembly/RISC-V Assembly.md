>LOAD/STORE-Architektur: nur durch `LOAD` bzw. `STORE` Befehlen kann auf den Hauptspeicher zugegriffen werden. Alle anderen Befehle arbeiten auf Registern.

<br>

### Aufbau eines RISC-V Programms

```nasm
.globl main                      ;; main wird als Einstiegspunkt deklariert

.data                            ;; globale Daten

	my_a: .word 13           ;; globale Integer Variable
	my_arr: .word 1, 24, -54 ;; globales Integer Array
	my_str: .string "Hallo"  ;; globales Character Array

.text                            ;; Programmcode Abschnitt

	main: ...

.end                             ;; Ende des Programmcodes
```

<br>

### Unterkapitel

>[[RISC-V Register]]
>
>[[RISC-V Speicher]]
>
>[[RISC-V Shifts]]
>
>[[RISC-V Multiplikation]]
>
>[[RISC-V Division]]
>
>[[RISC-V Sprünge]]
>
>[[RISC-V Instruktionscodierung]]


<br>

>Unterkapitel von [[Assembly]]
