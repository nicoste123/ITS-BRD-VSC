# README – Praktikum A2

Zusammenfassung zu den einzelnen Abschnitten in `main.s`.

### Was passiert im Code?

* **Anw01 bis Anw06:** 
  Hier geht es um `VariableA` (`0xbeef`). Zuerst wird die Adresse in `R0` geladen. Weil wir die Bytes tauschen wollen (wegen Little Endian), werden die beiden Bytes mit `ldrb` einzeln in `R2` und `R3` gepackt. Mit `lsl #8` schieben wir das eine Byte nach vorne und fügen sie mit `orr` wieder zusammen. So sind die Bytes gedreht. Am Ende schreibt `strh` den neuen Wert zurück in den Speicher.

* **Anw07 und Anw08:** 
  Der Wert `0xaffe` (`ConstByteA`) wird mit `mov` in das Register `R5` gepackt. Danach schreiben wir diesen Wert mit `strh` einfach über `VariableA` drüber.

* **Anw09 bis Anw0D:** 
  Hier arbeiten wir mit `VariableB` (`0x1234`). Ziel ist es, am Ende auf `0x4321` zu kommen. Dafür laden wir die Adresse und den Wert in Register, packen den Wert `0x30ED` in ein anderes Register und rechnen die beiden mit `add` zusammen (`0x1234 + 0x30ED = 0x4321`). `strh` speichert das Ergebnis wieder ab. 
  `Anw0E` ist am Ende nur noch eine Schleife (`b .`), damit das Programm nicht weiterläuft.

---

### Ablauf & Problemen

Ich musste den Ordner `Programs/A2/` manuell anlegen und die Dateien rüberkopieren (wobei die Dateien im Explorer teilweise grün angezeigt wurden, was mich kurz verwirrt hat). 

Der Debugger wollte bei mir leider nicht richtig starten, weil scheinbar die Profile gefehlt haben. Ich habe mir die Schritte (`Anw01` bis `Anw06`) deshalb über die Folien und eigene Recherche hergeleitet, um zu verstehen, was mit den Registern und Bytes passiert. 

Ich habe leider auch vergessen der Aufgabe entsprechend in der main.s Datei den Code ab Anw07 selber abzuändern.