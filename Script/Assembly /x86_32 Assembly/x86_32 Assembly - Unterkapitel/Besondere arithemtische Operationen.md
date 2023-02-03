### Multiplikation

```nasm
MUL <Quelle> - unsigned
```

```nasm
IMUL <Quelle> - signed
```

>`EDX:EAX` $:=$ `EAX` $\cdot$ `Quelle` (Konkatiniertes 64 Bit Ergebnis)

<br>

```nasm
IMUL <Ziel>, <Quelle> - signed / unsigned
```

> `Ziel` $:=$ `Ziel` $\cdot$ `Quelle` $\rightarrow$ nur 32 Bit

<br>

### Division

```nasm
DIV <Quelle> - unsigned
```

```nasm
IDIV <Quelle> - signed
```

> `EAX` $:=$ `(EDX:EAX)/Quelle`
> `EDX` $:=$ `Rest`
