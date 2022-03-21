# ITUG JourFixe #08
## Vis-à-vis: Zweisprachige Editionen mit TUSTEP (Urs Leo Gantenbein)

## Beschreibung
### Aufgabenstellung  
Zwei Texte sollen auf gegenüberliegenden Seiten mit #SATZ gesetzt werden, zum Beispiel ein lateinischer Text **seneca1.tf** und seine deutsche Übersetzung **seneca2.tf**:  

![vav1](https://user-images.githubusercontent.com/101052082/159179569-1f17e815-365e-40bb-b6bf-1be1590fe4ae.jpg)

Die gegenüberliegenden Seiten sollen sich dabei entsprechen, das heißt, die ersten und die letzten Zeilen der Seiten sollen inhaltlich ungefähr übereinstimmen. Die Idee besteht darin, zunächst in einer *ersten Phase* an den passenden Schnittstellen Leerseiten einzufügen:

![vav2](https://user-images.githubusercontent.com/101052082/159173745-a3feb20e-29f9-4ac3-9393-520d87b84126.jpg)

Schließlich werden in der *zweiten Phase* die beiden Texte, die nun wie Schloss und Schlüsselloch zusammenpassen, übereinandergelegt, was zum gewünschten Resultat führt:

![vav3](https://user-images.githubusercontent.com/101052082/159174066-4a8d24db-cadd-4683-9f02-5d7c86d029f2.jpg)
<br>
<br>
### Phase 1: Einfügen von Seitenumbrüchen und Leerseiten mit der TUE- bzw. Makrodatei &quot;setze1&quot;
In der ersten Phase werden an passenden Stellen der beiden Texte Leerseiten eingefügt. Die ersten bzw. letzten Zeilen der gegenüberliegenden Seiten sollen sich inhaltlich entsprechen. Um dies zu erreichen, müssen die Seitenumbrüche in der Regel manuell gesetzt werden. Jedem Seitenumbruch soll eine Leerseite folgen, damit die Texte in Phase 2 zusammengesetzt werden können. Die Titelseite bildet die erste Seite des linksseitigen Texts **seneca1.tf**.

Dem rechtsseitigen Text **seneca2.tf** werden zuvor zwei Leerseiten vorangestellt, was mit folgender Steueranweisung (bzw. mit einem eigens dafür definierten Makro) erzielt werden kann:  
&lt;np2/&gt;&&&+2&&&{  

Folgende Steueranweisungen fügen einen Seitenumbruch zur nächsten linken oder rechten Seite ein. Wenn auf der beabsichtigten linken Seite ein Umbruch zur nächsten linken Seite eingesetzt wird, so wird automatisch eine Leerseite eingeschaltet. Das Gleiche gilt für die rechte Seite. Die Seitenumbrüche innerhalb eines Textabschnittes bewahren die Zeilenformatierung.
 
<table>
<tr>
    <td>&lt;npl/&gt;&&&l&&&{</td>
    <td>Seitenumbruch zwischen zwei Textabschnitten zur nächsten linken Seite</td>
</tr>
<tr>
    <td>&lt;npr/&gt;&&&r&&&{</td>
    <td>Seitenumbruch zwischen zwei Textabschnitten zur nächsten rechten Seite</td>
</tr>
<tr>
    <td>&lt;npal/&gt;&&l&&{</td>
    <td>Seitenumbruch zur nächsten linken Seite innerhalb eines Textabschnitts</td>
</tr> 
<tr>
    <td>&lt;npar/&gt;&&r&&{</td>
    <td>Seitenumbruch zur nächsten rechten Seite innerhalb eines Textabschnitts</td>
</tr> 
</table>  
<br>
  
Die Makrodatei **setze1** enthält die Satzroutinen für die beiden Dateien **seneca1.tf** und **seneca2.tf**, die im Wesentlichen den Beispielroutinen für Texte mit Apparaten im Tustep-Wiki entsprechen. Die Parameter und die Makrodefintionen für die Satzroutinen sind in den Dateien **setze_par.tf** und **setze_mak.tf** enthalten. Wie weiter unten noch erklärt wird, enthält die Parameterdatei **setze_par_s1.tf** eine Variable für die erste Seitenzahl s1, in die am Anfang der aktuell beabsichtigte Wert eingesetzt wird.  

 
Die *Phase 1* benötigt in der Regel mehrere Satzgänge mit **setze1** mit #SATZ als wesentlichem Bestandteil. Nach dem ersten Ausführen von **setze1** werden die 2. und die 3. Seite verglichen und die Seitenumbrüche mit den obigen Makros inhaltlich passend gesetzt. Dann wird **setze1** ein zweites Mal ausgeführt, das Resultat überprüft und es werden die Seitenumbrüche für die 4. und 5. Seite angebracht. Wiederum wird **setze1** angewendet und so weiter bis zum Ende der Texte. Nach dem Setzen aller Seitenumbrüche sind **seneca1.tf** und **seneca2.tf** in der *Phase 2* bereit zur Montage mit **setze2**.
<br>
<br>
### Phase 2: Zusammenfügen der beiden vorbereiteten Texte mit der TUE- bzw. Makrodatei &quot;setze2&quot;
Der linksseitige Text **seneca1.tf** enthält auf der ersten Seite die Titelseite. Nach jedem manuell eingesetzten Seitenumbruch wurde in *Phase 1* eine Leerseite eingefügt. Die Leerseiten von **seneca1.tf** tragen somit ungerade Seitennummern. Dem rechtsseitigen Text **seneca2.tf** wurden wie oben angemerkt zwei Leerseiten vorangestellt. Auch bei diesem Text folgt jedem Seitenumbruch eine Leerseite, wodurch mit Ausnahme der ersten Seite die Leerseiten von **seneca2.tf** gerade Seitennummern aufweisen. 
  
Die Makrodatei **setze2** führt zunächst mit den Dateien **seneca1.tf** und **seneca2.tf** einen getrennten Satzdurchgang durch. Die resultierenden Satzdateien aus1 und aus2 werden schließlich mit #\*MONT übereinandergelegt. Das Besondere an #\*MONT besteht darin, dass bis zu 1000 Satzdateien zusammenmontiert und damit auch komplexe Satzresultate erzielt werden können. Die Ausgabe erfolgt mit #\*PSAUS und bei Bedarf weiter mit #\*PS2PDF. Die Einzeltexte mit den fertig eingefügten Leerseiten und mit dem Resultat vis-à-vis im Buchformat 15.5 x 23.0 cm finden sich in den Dateien **ziel_seneca1.tf**, **ziel_seneca2.tf** und **ziel_seneca_bf.pdf**. 
 
\[Bemerkung: In der ersten, im Jour-fixe vorgestellten Version von **setze2** erzeugte ich mit #\*PSAUS die Ghostscriptdateien **seneca1.ps** und **seneca2.ps**, aus denen ich mittels #\*PSAUSWAHL die einzelnen Seiten extrahierte und dann über eine Schleife mit #\*PSMONT zum Endresultat zusammensetzte. Dank dem Hinweis von Hannelore und Wilhelm Ott auf #\*MONT, das direkt mit den Satzdateien arbeitet, geht das Zusammensetzen viel schneller und eleganter.\]
<br>
<br>
### Wiederverwendbarkeit der Makrodateien &quot;setze1&quot; und &quot;setze2&quot;
Wenn man mehrere Kapitel eines Buchs mit ähnlichen Satzroutinen bearbeiten will und dazu nur die Kapitelnamen und deren erste Seitenzahlen austauschen muss, kann so vorgegangen werden, wie in **setze1** und **setze2** exemplarisch ausgeführt. Man definiert den Wurzelnamen der Dateien mittels eine Parameters **root**. In unserem Fall beträgt `root = "seneca"`. Alle anderen Dateinamen werden dann mit der Funktion CONCAT zu TUSCRIPT-Variablen zusammengesetzt, die den Wurzelnamen enthalten. Diese werden mit DEFINE in TUSTEP-Variablen umgewandelt, damit sie so in die Satzroutinen eingesetzt werden können, zum Beispiel wie folgt für die Ausgangsdateien **seneca1.tf** und **seneca2.tf**: 
 
`$$ QUELLE1 = CONCAT(root,"1.tf")` <br>
`DEFINE QUELLE1` <br>
`QUELLE2 = CONCAT(root,"2.tf")` <br>
`DEFINE QUELLE2` <br>
 
Dasselbe gilt für die erste Seite s1 und die letzte Seite s998. So erwartet #\*PSAUS die Angabe von s1 und s998. Wie weiter bekannt, muss die erste Seite s1 auch im Parameter SEI von #SATZ \(hier enthalten in **setze_par.tf**\) an erster Stelle aufgeführt werden, wie zum Beispiel hier die Seite 11: 
  
SEI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;11  -2 

Um die erste Seitenzahl nicht manuell in SEI einfügen zu müssen, habe ich die Datei **setze_par_s1.tf** eingeführt, die mit **setze_par.tf** identisch ist bis auf den Parameter SEI, der dort wie folgt lautet: 
  
SEI&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;s1  -2 
 
Dieses &quot;s1&quot; stellt keinen eigentlichen Parameter dann, sondern ist ein Stellvertreterzeichen für die noch einzusetzende aktuelle erste Seitenzahl. Die Einsetzung geschieht wie folgt, indem die Datei `PARA0 = "setze_par_s1.tf"` mit OPEN geöffnet und mit CREATE eine leere Datei `PARA = "setze_par.tf"` erzeugt wird. Der Inhalt von `PARA0` wird in eine Datei text ausgelesen, die über einen LOOP satzweise nach den Vorkommen von &quot;s1&quot; durchsucht und im positiven Fall durch den aktuellen Wert, in unserem Beispiel 11, ersetzt wird. Das Resultat wird in der Parameterdatei `PARA` abgespeichert, die dann im Satzvorgang zur Anwendung kommt. 
 
In meiner Edition verwende ich für jedes Kapitel eine eigene TUE-Makrodatei, in der ich lediglich die Werte für **root** und **s1** und eventuell noch die Seitenanzahl festlegen muss. Natürlich könnte man auch eine Makrodatei mit Parametern definieren, doch dann müssten diese bei jedem Aufruf explizit angegeben werden. Ich finde die Verwendung von fixen Makrodateien praktischer. Am Schluss kann das fertige Buch mit #\*MONT zusammengesetzt werden.
