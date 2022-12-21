>#### Definition
>
>Ein Mealy-Automat ist ein deterministischer, endlicher Automat, dessen Ausgabe von seinem Zustand und seiner Eingabe abhängt. Die Ausgabe kann auf die Kante oder in den Zustand geschrieben werden und wird getrennt mithilfe eines "/".

<br>

### Formale Definition

>Ein Moore-Automat kann als 6-[[Tupel]] defininiert werden und verhält sich gleich eines [Moore Automaten](Moore%20Automaten.md):

<br>

- $Q$ ist eine endliche Mengen an Zuständen $|Q|<\infty$
- $\Sigma$ / $I$ ist das Eingabealphabet $|\Sigma|<\infty$
- $\Omega$ / $O$ ist das Ausgabealphabet $|\Omega|<\infty$ 
- $\delta$ ist die Übergangsfunktion $\delta: Q\times\Sigma\rightarrow Q$
- $\lambda$ definiert die Ausgabefunktion $\lambda: Q\rightarrow\Omega$
- $q_0\in Q$ ist der Startzustand / Anfangszustand

<br>

### Formale Beschreibung

##### Graphische Darstellung

>Jeder Zustand trägt seinen Bezeichner (und seine Ausgabe $\Omega$ / $O$). 
>Gerichtete Kanten dienen zur Realisierung von Zustandsübergängen.
>Die Kante trägt die jeweilige Eingabe $I$ (und die Ausgabe $\Omega$ / $O$ des resultierenden Zustands).

<br>

>#### Beispiel
>
><img src="./Resourcen/Pasted%20image%2020221221141538.png" alt="" width="300"/>
