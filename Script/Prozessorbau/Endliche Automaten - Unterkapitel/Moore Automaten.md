>#### Definition
>
>Ein Moore-Automat ist ein endlicher Automat, dessen Ausgabe ausschließlich von seinem derzeitigen Zustand abhängt. Beim Erreichen eines Zustandes wird eine Ausgabe erzeugt, welche unabhängig vom Übergang auf diesen Zustand auftritt.
>Moore-Automaten können deterministisch und nichtdeterministisch sein.

<br>

### Formale Definition

>Ein Moore-Automat kann als 7-[[Tupel]] defininiert werden:

<br>

- $Q$ ist eine endliche Mengen an Zuständen $|Q|<\infty$
- $\Sigma$ / $I$ ist das Eingabealphabet $|\Sigma|<\infty$
- $\Omega$ / $O$ ist das Ausgabealphabet $|\Omega|<\infty$ 
- $\delta$ ist die Übergangsfunktion $\delta: Q\times\Sigma\rightarrow Q$
- $\lambda$ definiert die Ausgabefunktion $\lambda: Q\rightarrow\Omega$
- $q_0\in Q$ ist der Startzustand / Anfangszustand
- $F\subseteq Q$ ist eine (endliche) Menge möglicher akzeptierter Zustände (Endzustandsmenge) $\Rightarrow$ wenn der Automat nach dem Lesen des Eingabeworts $J\in\Sigma^*$ in einem Zustand aus $F$ hält (meistens in unserem Fall haben wir nur einen solchen Zustand), so gehört $J$ als geltendes Wort zur Sprache $L$ über dem Alphabet $\Sigma$ 

<br>

>Falls die reguläre Sprache nicht betrachtet werden soll kann $F$ auch weggelassen werden und wir erhalten somit ein 6-Tupel. 
>Das 6-Tupel eines Moore-Automaten ist formal dasselbe eines [Mealy Automaten](Mealy%20Automaten.md).

<br>

### Formale Beschreibung

##### Graphische Darstellung

>Jeder Zustand trägt seinen Bezeichner und seine Ausgabe $\Omega$ / $O$. 
>Gerichtete Kanten dienen zur Realisierung von Zustandsübergängen.
>Sie tragen die jeweilige Eingabe $I$.
>Falls wir reguläre Sprache betrachten werden Zustände aus $F$ deutlich makiert.

<br>

>#### Beispiel
>
>Es gilt: $Q=\{q_0, q_1, q_2, q_3\}$, $\Sigma=\{x, y, z\}$, $\Omega=\{a, b, c\}$ und $q_0=q_0$
>
><img src="./Resourcen/Pasted%20image%2020221221111306.png" alt="" width="300"/>

<br>

### Nicht deterministische und deterministische Automatenumwandlung

>Beobachtung: 
>
>Sowohl Zustand $q_2$ und $q_3$ behandeln nicht alle möglichen Inputs aus $\Sigma$. Es handelt sich um einen nicht deterministischen Automaten.

<br>

##### Umwandlung

>Es wird eine Art "Killzustand" hinzuzufügen $q_4$. Jede Inputkette die diesen Zustand wird als invalid betrachtet. Es ist ihr nie möglich diesen Zustand zu verlassen. Die einzige Möglichkeit ist diese Kette zu verwerfen.

<br>

##### Automatentafel Darstellung

>Eine Automatentafel beschreibt jeweils einen derzeitigen Zustand und die Auswirkungen verschiedener Eingaben.
>Zudem gibt es eine Spalte für die derzeitige Ausgabe des zu betrachtenden Zustands.

<br>

>#### Beispiel
>
>Es gilt weiterhin: $Q=\{q_0, q_1, q_2, q_3\}$, $\Sigma=\{x, y, z\}$, $\Omega=\{a, b, c\}$ und $q_0=q_0$
>
>| $\delta$  | x | y | z | $\lambda$ |
>|:---:|:---:|:---:|:---:|:---:|
>| $q_0$ | $q_3$ | $q_2$ | $q_1$ | $b$ |
>| $q_1$ | $q_3$ | $q_2$ | $q_3$ | $a$ |
>| $q_2$ | $-$ | $q_3$ | $-$ | $a$ |
>| $q_3$ | $q_3$ | $-$ | $q_2$ | $c$ |

<br>

>Umwandlung in einen deterministischen Automaten:

<br>

>#### Beispiel
>
>Hinzufügen der reflexiven Kanten:
>
>| $\delta$  | x | y | z | $\lambda$ |
>|:---:|:---:|:---:|:---:|:---:|
>| $q_0$ | $q_3$ | $q_2$ | $q_1$ | $b$ |
>| $q_1$ | $q_3$ | $q_2$ | $q_3$ | $a$ |
>| $q_2$ | $q_4$ | $q_3$ | $q_4$ | $a$ |
>| $q_3$ | $q_3$ | $q_4$ | $q_2$ | $c$ |

<br>

##### Wahrheitstabellarische Darstellung 

>Gleichzustellen mit einer Automatentafeldarstellung.
>Jedoch wird jeder Input seperat gemapped auf jeden Zustand betrachtet. 
>Rechts befindet sich weiterhin die derzeitge Ausgabe aber als Relation zwischen $I$ und $Q$
>Links der Input $I$.
>In der Mitte befinden sich der alte und der neue Zustand. Die Anzahl der benötigten [[Flip-Flops]] richtet sich nach der Anzahl der Zustände zur [[Zahlensysteme |Basis 2]].
>Eine Darstellung kann nur in einer deterministischen Form erfolgen.

<br>

>#### Beispiel
>
>Es gilt weiterhin: $Q=\{q_0, q_1, q_2, q_3\}$, $\Sigma=\{x, y, z\}$, $\Omega=\{a, b, c\}$ und $q_0=q_0$
>
>| $I$ | | $FF0$ | $FF1$ | $FF2$ | | $FF0'$ | $FF1'$ | $FF2'$ | | $O$ |
>|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
>| $x$ | | $0$ |  $1$ | $1$ | | $0$ |   $0$ | $0$ | | $c$ |
>| $x$ | | $0$ |   $1$ | $1$ | | $0$ |  $0$ | $1$ | | $c$ |
>| $x$ | | $1$ |   $0$ | $0$ | | $0$ |   $1$ | $0$ | | $-$ |
>| $x$ | | $0$ |   $1$ | $1$ | | $0$ |   $1$ | $1$ | | $c$ |
>| $y$ | | $0$ |   $1$ | $1$ | | $0$ |   $0$ | $0$ | | $c$ |
>| $y$ | | $0$ |   $1$ | $0$ | | $0$ |  $0$ | $1$ | | $a$ |
>| $y$ | | $0$ |   $1$ | $1$ | | $0$ |  $1$ | $0$ | | $c$ |
>| $y$ | | $1$ |   $0$ | $0$ | | $0$ |  $1$ | $1$ | | $-$ |
>| $z$ | | $0$ |   $0$ | $1$ | | $0$ |  $0$ | $0$ | | $a$ |
>| $z$ | | $0$ |   $1$ | $1$ | | $0$ |  $0$ | $1$ | | $c$ |
>| $z$ | | $1$ |   $0$ | $0$ | | $0$ |  $1$ | $0$ | | $-$ |
>| $z$ | | $0$ |   $1$ | $0$ | | $0$ |  $1$ | $1$ | | $a$ |

<br>

##### Bool'sche Term Darstellung

>Bool'sche Terme können keine undefinierten Relationen darstellen $\Rightarrow$ nur deterministische Automaten können durch solche Terme ausgedrückt werden.

<br>

>#### Beispiel
>
>Es gilt weiterhin: $Q=\{q_0, q_1, q_2, q_3\}$, $\Sigma=\{x, y, z\}$, $\Omega=\{a, b, c\}$ und $q_0=q_0$
>
>Terme der Flip-Flop's:
>
>$FF0=(x\wedge FF0'\wedge\lnot FF1'\wedge\lnot FF2')\ \vee \ ...$
>$FF1=(y\wedge\lnot FF0'\wedge FF1')\ \vee \ ...$
>$FF2=(z\wedge\lnot FF0'\wedge\lnot FF1'\wedge\lnot FF0')\ \vee \ ...$
>
>Terme der Ausgänge:
>
>$a=(\lnot FF0\wedge FF1\wedge\lnot FF2)\vee (\lnot FF0\wedge\lnot FF1\wedge FF2)$
>$b=\lnot FF0\wedge\lnot FF1\wedge\lnot FF2$
>$c=\lnot FF0\wedge FF1\wedge FF2$

<br>

##### Schaltplan Darstellung

>Eine Schaltplandarstellung ist auch nur für deterministischen Automaten möglich

<br>

>#### Beispiel 
>
>Es gilt nun: $Q=\{s_0, s_1, s_2, s_3\}$, $\Sigma=\{0, 1\}$ und $q_0=s_0$
>$1$ wird zudem nur ausgegeben wenn die Eingabekette $101$ zum derzeitigen Zeitpunkt lautet - analog zu W09T01.
>
><img src="./Resourcen/Pasted%20image%2020221221133918.png" alt="" width="500"/>