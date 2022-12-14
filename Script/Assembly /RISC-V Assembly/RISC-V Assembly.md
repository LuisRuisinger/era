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

>[RISC-V Register](./RISC-V%20Assembly%20Unterkapitel/RISC-V%20Register.md)
>
>[RISC-V Speicher](./RISC-V%20Assembly%20Unterkapitel/RISC-V%20Speicher.md)
>
>[RISC-V Shifts](./RISC-V%20Assembly%20Unterkapitel/RISC-V%20Shifts.md)
>
>[RISC-V Multiplikation](./RISC-V%20Assembly%20Unterkapitel/RISC-V%20Multiplikation.md)
>
>[RISC-V Division](./RISC-V%20Assembly%20Unterkapitel/RISC-V%20Division.md)
>
>[RISC-V Sprünge](./RISC-V%20Assembly%20Unterkapitel/RISC-V%20Sprünge.md)
>
>[RISC-V Instruktionscodierung](./RISC-V%20Assembly%20Unterkapitel/RISC-V%20Instruktionscodierung.md)
