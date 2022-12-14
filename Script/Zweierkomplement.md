>#### Definition
>
>Das Zweierkomplement beschreibt eine Darstellungsvariante von negativen Zahlen.
>Dabei wird das positive Gegenstück der negativen Zahl genommen, invertiert und 1 dazu addiert. Das Resultat ist die nun negative Zahl.

<br>

>#### Beispiel
>
>Aus der Zahl 7 die Zahl -7 generieren (Komplementbildung):
>
>$inv(0000 0111_2) + 0000 0001_2\rightarrow 1111 1000_2 + 0000 0001_2\rightarrow 1111 1001_2$

<br>

### Arithmetische Operationen

##### Addition

>Die Addition verhält sich analog zur Addition mit vorzeichenlosen Zahlen

<br>

##### Subtraktion

>Die Subtraktion mit Zahlen im Zweierkomplement erfolgt in 2 Schritten:
>
>1. Schritt - Komplementbildung des Subtrahenden
>2. Schritt - Addition der neu enstandenen Zahl

<br>

>#### Beispiel
>
>$0000 1001_2 - 0000 0111_2$
>
>$= 0000 1001_2 + inv(0000 0111_2) + 0000 0001$
>$= 0000 1001_2 + 1111 1000_2 + 0000 0001_2$
>$= 0000 1001_2 + 1111 1001_2$ 
>$= 0000 0010_2$